---
title: Kurz – vytvoření aplikace s více kontejnery s dockerovým komponem
description: Přečtěte si, jak spravovat víc než jeden kontejner a komunikovat mezi nimi ve Visual Studiu for Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983953"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Vytvoření vícekontejnerové aplikace pomocí nástroje Docker Compose

V tomto kurzu se dozvíte, jak spravovat více než jeden kontejner a komunikovat mezi nimi při použití Docker Compose v Visual Studiu pro Mac.

## <a name="prerequisites"></a>Požadavky

* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio pro Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>Vytvoření základní webové aplikace ASP.NET a přidání podpory Dockeru

1. Vytvořte nové řešení tak, že přejdete na **Soubor > nové řešení**.
1. V části **.NET Core >** App ![zvolte šablonu webové **aplikace:** Vytvoření nové aplikace ASP.NET](media/docker-quickstart-1.png)
1. Vyberte cílovou architekturu. V tomto příkladu použijeme rozhraní .NET Core 2.2: ![Nastavení cílového rozhraní](media/docker-quickstart-2.png)
1. Zadejte podrobnosti projektu, například Název projektu (_DockerDemoFrontEnd_ v tomto příkladu) a Název řešení (_DockerDemo_). Vytvořený projekt obsahuje všechny základy, které potřebujete k vytvoření a spuštění webu ASP.NET Core.
1. V panelu řešení klikněte pravým tlačítkem myši na projekt ![DockerDemoFrontEnd a vyberte Přidat > Přidat podporu **Dockeru:** Přidat podporu dockeru](media/docker-quickstart-3.png)

Visual Studio pro Mac automaticky přidá nový projekt do vašeho řešení s názvem **docker-compose** a přidá **dockerfile** do vašeho stávajícího projektu.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>Vytvoření základního webového rozhraní API ASP.NET a přidání podpory Dockeru

Dále vytvoříme druhý projekt, který bude fungovat jako naše backend API. Šablona **rozhraní .NET Core API** obsahuje řadič, který nám umožňuje zpracovávat požadavky RESTful.

1. Přidejte nový projekt do existujícího řešení kliknutím pravým tlačítkem myši na řešení a výběrem **možnosti Přidat > Přidat nový projekt**.
1. V části **.NET Core > App** zvolte šablonu **rozhraní API.**
1. Vyberte cílovou architekturu. V tomto příkladu použijeme .NET Core 2.2
1. Zadejte podrobnosti projektu, například Název projektu (_DockerDemoAPI_ v tomto příkladu).
1. Po vytvoření přejděte na panel řešení a klikněte pravým tlačítkem myši na projekt DockerDemoAPI a vyberte **přidat > Přidat podporu Dockeru**.

Soubor **docker-compose.yml** v projektu **docker-compose** bude automaticky aktualizován tak, aby zahrnoval projekt rozhraní API vedle existujícího projektu Webové aplikace. Když vytvoříme a spustíme projekt **docker-compose,** každý z těchto projektů se nasadí do samostatného kontejneru Dockeru.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Integrujte dva kontejnery

Nyní máme dva ASP.NET projekty v našem řešení a oba jsou nakonfigurovány s podporou Dockeru. Dále musíme přidat nějaký kód!

1. V `DockerDemoFrontEnd` projektu otevřete *soubor Index.cshtml.cs* a `OnGet` nahraďte metodu následujícím kódem:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

1. V souboru *Index.cshtml* přidejte `ViewData["Message"]` řádek, který se zobrazí, aby soubor vypadal jako následující kód:

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

1. Nyní v projektu webového rozhraní API přidejte kód do řadiče hodnoty a přizpůsobte zprávu vrácenou rozhraním API pro volání, které jste přidali z *webfrontendu*:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Nastavte `docker-compose` projekt jako projekt spuštění a přejděte na **spustit > spustit ladění**. Pokud je vše správně nakonfigurováno, zobrazí se zpráva "Hello from webfrontend a webapi (s hodnotou 1).":

![Docker řešení s více kontejnery běží](media/docker-multicontainer-debug.png)
