---
title: Aplikace s více kontejnery s Docker Compose
description: Naučte se spravovat více než jeden kontejner a komunikovat mezi nimi v Visual Studio pro Mac
ms.custom: SEO-VS-2020
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: e46a66ab9ec05f8e7ad13091fdced01bffbd93b5
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038670"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Vytvoření vícekontejnerové aplikace pomocí nástroje Docker Compose

V tomto kurzu se naučíte spravovat více než jeden kontejner a mezi nimi komunikovat při použití Docker Compose v Visual Studio pro Mac.

## <a name="prerequisites"></a>Požadavky

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pro Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Vytvoření webové aplikace ASP.NET Core a přidání podpory Docker

1. Nové řešení můžete vytvořit tak, že na **soubor > nové řešení**.
1. V části **webové a konzolové > aplikace** vyberte šablonu **webové aplikace** : ![ vytvořit novou aplikaci ASP.NET.](media/docker-quickstart-1.png)
1. Vyberte cílovou architekturu. V tomto příkladu použijeme .NET Core 3,1: ![ nastavení cílové platformy.](media/docker-quickstart-2.png)
1. Zadejte podrobnosti projektu, jako je například název projektu (_DockerDemoFrontEnd_ v tomto příkladu) a název řešení (_DockerDemo_). Vytvořený projekt obsahuje všechny základy, které potřebujete k vytvoření a spuštění webu ASP.NET Core.
1. V Oblast řešení klikněte pravým tlačítkem na projekt DockerDemoFrontEnd a vyberte **přidat > přidat podporu Docker**: ![ Přidat podporu Docker.](media/docker-quickstart-3.png)

Visual Studio pro Mac automaticky přidá nový projekt do vašeho řešení s názvem **Docker-** **souboru Dockerfile** a přidá do existujícího projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Vytvoření webového rozhraní API ASP.NET Core a přidání podpory Docker

V dalším kroku vytvoříme druhý projekt, který bude fungovat jako naše rozhraní API back-endu. Šablona rozhraní **.NET Core API** zahrnuje kontroler, který nám umožňuje zpracovávat požadavky RESTful.

1. Kliknutím pravým tlačítkem na řešení a zvolením **přidat > přidat nový projekt**přidejte nový projekt do existujícího řešení.
1. V části **webové a konzolové > aplikace** vyberte šablonu **rozhraní API** .
1. Vyberte cílovou architekturu. V tomto příkladu použijeme .NET Core 3,1.
1. Zadejte podrobnosti projektu, jako je například název projektu (_MyWebAPI_ v tomto příkladu).
1. Po vytvoření přejděte na Oblast řešení a klikněte pravým tlačítkem na projekt MyWebAPI a vyberte **přidat > přidat podporu Docker**.

Soubor **Docker-Compose. yml** v projektu **Docker-** se automaticky aktualizuje tak, aby zahrnoval projekt rozhraní API spolu s existujícím projektem webové aplikace. Když sestavíte a spustíte projekt **Docker-** Build, každý z těchto projektů se nasadí do samostatného kontejneru Docker.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrace dvou kontejnerů

V našem řešení teď máme dva projekty ASP.NET a obě jsou nakonfigurované s podporou Docker. Dál je potřeba přidat nějaký kód!

1. V `DockerDemoFrontEnd` projektu otevřete soubor *pages/index. cshtml. cs* a nahraďte `OnGet` metodu následujícím kódem:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > V produkčním kódu nebudete `HttpClient` po každé žádosti Dispose. Osvědčené postupy najdete v tématu [použití HttpClientFactory k implementaci odolných požadavků HTTP](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. V souboru *index. cshtml* přidejte řádek, který se zobrazí `ViewData["Message"]` , aby soubor vypadal jako následující kód:

      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }

      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```
  
1. V projektech front-endu i webového rozhraní API zakomentujte volání [Microsoft. AspNetCore. Builder. HttpsPolicyBuilderExtensions. UseHttpsRedirection](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) v `Configure` metodě v *Startup.cs*, protože tento ukázkový kód používá pro volání webového rozhraní API http, nikoli https.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. Nastavte `docker-compose` projekt jako spouštěný projekt a přejít na **Spustit > spustit ladění**. Pokud je všechno správně nakonfigurované, zobrazí se zpráva Hello z webendu a WebApi (s hodnotou 1). ":

![Řešení Docker multi Container je spuštěné](media/docker-multicontainer-debug.png)
