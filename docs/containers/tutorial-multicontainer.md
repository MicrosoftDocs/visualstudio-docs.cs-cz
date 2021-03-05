---
title: Práce s více kontejnery pomocí Docker Compose
author: ghogen
description: Naučte se používat více kontejnerů s Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: e5bd7673bc600d0ae84b0a343a071e2a8621e4b9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150199"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Kurz: Vytvoření aplikace s více kontejnery pomocí Docker Compose

V tomto kurzu se naučíte spravovat více než jeden kontejner a při používání nástrojů kontejneru v aplikaci Visual Studio komunikovat mezi nimi.  Správa více kontejnerů vyžaduje *orchestraci kontejnerů* a vyžaduje produkt Orchestrator, například Docker Compose, Kubernetes nebo Service Fabric. Zde použijeme Docker Compose. Docker Compose je skvělé pro místní ladění a testování v průběhu vývojového cyklu.

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **vývoj pro web**, **Azure Tools** nebo **.NET Core pro vývoj pro různé platformy**
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **vývoje pro web**, úlohy **nástrojů Azure** a/nebo **.NET Core pro vývoj pro různé platformy**
* [Vývojové nástroje .NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) pro vývoj pomocí .net Core 2,2
* [Vývojové nástroje .NET Core 3](https://dotnet.microsoft.com/download/dotnet-core/3.1) pro vývoj pomocí .net Core 3,1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Vytvoření projektu webové aplikace

V aplikaci Visual Studio vytvořte projekt **ASP.NET Core webové aplikace** s názvem `WebFrontEnd` a vytvořte webovou aplikaci se stránkami Razor.
  
::: moniker range="vs-2017"

Nevybírejte možnost **Povolit podporu Docker**. Podporu Docker přidáte později.

![Snímek obrazovky s vytvořením webového projektu](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Vytvořit projekt ASP.NET Core webové aplikace](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Nevybírejte možnost **Povolit podporu Docker**. Podporu Docker přidáte později.

![Snímek obrazovky s dalšími informacemi při vytváření webového projektu Není vybraná možnost povolit podporu Docker.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Vytvoření projektu webového rozhraní API

Přidejte projekt do stejného řešení a zavolejte ho *MyWebAPI*. Jako typ projektu vyberte **rozhraní API** a zrušte zaškrtnutí políčka **Konfigurovat pro protokol HTTPS**. V tomto návrhu používáme pro komunikaci s klientem pouze protokol SSL, nikoli pro komunikaci mezi kontejnery ve stejné webové aplikaci. `WebFrontEnd`Potřebuje pouze https a kód v příkladech předpokládá, že jste toto zaškrtávací políčko zrušili. Obecně platí, že certifikáty vývojářů rozhraní .NET používané v aplikaci Visual Studio jsou podporovány pouze pro požadavky z externích na kontejner, nikoli pro požadavky na kontejner na kontejner.

::: moniker range="vs-2017"
   ![Snímek obrazovky s vytvořením projektu webového rozhraní API](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Snímek obrazovky s vytvořením projektu webového rozhraní API](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Přidat kód pro volání webového rozhraní API

1. V `WebFrontEnd` projektu otevřete soubor *index.cshtml.cs* a nahraďte `OnGet` metodu následujícím kódem.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > V kódu reálného světa byste `HttpClient` po všech žádostech neměli nakládat. Osvědčené postupy najdete v tématu [použití HttpClientFactory k implementaci odolných požadavků HTTP](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Pro .NET Core 3,1 v aplikaci Visual Studio 2019 nebo novější používá šablona webového rozhraní API rozhraní WeatherForecast API, takže odkomentujte řádek a přidejte komentář k řádku pro ASP.NET 2. x.

1. V souboru *index. cshtml* přidejte řádek, který se zobrazí `ViewData["Message"]` , aby soubor vypadal jako následující kód:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (Jenom ASP.NET 2. x) Nyní v projektu webového rozhraní API přidejte kód do řadiče hodnot a upravte zprávu vrácenou rozhraním API pro volání, které jste přidali ze služby *webendu*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    S .NET Core 3,1 to není potřeba, protože můžete použít rozhraní WeatherForecast API, které už existuje. Je však třeba odkomentovat volání <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>  v `Configure` metodě v *Startup.cs*, protože tento kód používá protokol HTTP, nikoli HTTPS pro volání webového rozhraní API.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. V `WebFrontEnd` projektu vyberte možnost **Přidat > kontejner Orchestrator support**. Zobrazí se dialogové okno **Možnosti podpory Docker** .

1. Vyberte **Docker Compose**.

1. Vyberte cílový operační systém, například Linux.

   ![Snímek obrazovky s výběrem cílového operačního systému](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio vytvoří soubor *Docker-Compose. yml* a soubor *. dockerignore* v uzlu **Docker – pro vytváření** v řešení a tento projekt se zobrazí tučným písmem, které ukazuje, že se jedná o projekt po spuštění.

   ![Snímek obrazovky Průzkumník řešení s přidaným projektem Docker – sestavení](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-Compose. yml* se zobrazí takto:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Soubor *. dockerignore* obsahuje typy souborů a rozšíření, které nechcete, aby Docker zahrnul do kontejneru. Tyto soubory jsou obecně spojené s vývojovým prostředím a správou zdrojového kódu, nikoli součástí aplikace nebo služby, kterou vyvíjíte.

   Podrobnosti o spuštěných příkazech najdete v části **nástroje kontejneru** v podokně výstup.  K nakonfigurování a vytvoření kontejnerů modulu runtime se používá nástroj příkazového řádku Docker – sestavení.

1. V projektu webového rozhraní API znovu klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat**  >  **podporu kontejneru Orchestrator**. Zvolte **Docker Compose** a pak vyberte stejný cílový operační systém.  

    > [!NOTE]
    > V tomto kroku bude Visual Studio nabízet vytvoření souboru Dockerfile. Pokud to uděláte na projektu, který už má podporu Docker, zobrazí se dotaz, jestli chcete přepsat existující souboru Dockerfile. Pokud jste v souboru Dockerfile udělali změny, které chcete zachovat, klikněte na ne.

    Visual Studio provede některé změny souboru YML Docker pro vytváření. Teď jsou zahrnuté obě služby.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Nyní spusťte web místně (F5 nebo CTRL + F5) a ověřte, zda funguje podle očekávání. Pokud je všechno správně nakonfigurované pomocí verze .NET Core 2. x, zobrazí se zpráva Hello z webendu a WebApi (s hodnotou 1).  S .NET Core 3 vidíte data předpovědi počasí.

   První projekt, který použijete při přidání orchestrace kontejnerů, je nastaven tak, aby se spustil při spuštění nebo ladění. Akci spuštění můžete nakonfigurovat ve **vlastnostech projektu** pro projekt Docker-pro vytváření.  V uzlu projekt Docker – sestavení klikněte pravým tlačítkem myši a otevřete místní nabídku a zvolte možnost **vlastnosti** nebo stiskněte klávesu ALT + ENTER.  Následující snímek obrazovky ukazuje vlastnosti, které chcete použít pro toto řešení.  Můžete například změnit stránku, která je načtena přizpůsobením vlastnosti **Adresa URL služby** .

   ![Snímek obrazovky Docker – sestavení vlastností projektu](media/tutorial-multicontainer/launch-action.png)

   Tady vidíte, co se zobrazí při spuštění (verze .NET Core 2. x):

   ![Snímek obrazovky běžící webové aplikace](media/tutorial-multicontainer/webfrontend.png)

   Webová aplikace pro .NET 3,1 zobrazuje data o počasí ve formátu JSON.

## <a name="next-steps"></a>Další kroky

Podívejte se na možnosti nasazení vašich [kontejnerů do Azure](/azure/containers).

## <a name="see-also"></a>Viz také
  
[Docker Compose](https://docs.docker.com/compose/)  
[Nástroje kontejneru](./index.yml)