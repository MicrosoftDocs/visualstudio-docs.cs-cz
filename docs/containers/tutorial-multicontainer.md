---
title: Kurz pro multikontejnery pomocí & & ASP.NET core
author: ghogen
description: Naučte se používat více kontejnerů s Docker Compose
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027334"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Kurz: Vytvoření aplikace s více kontejnery s Docker Compose

V tomto kurzu se dozvíte, jak spravovat více než jeden kontejner a komunikovat mezi nimi při použití nástrojů kontejneru v sadě Visual Studio.  Správa více kontejnerů vyžaduje *orchestraci kontejnerů* a vyžaduje orchestrator, jako je Docker Compose, Kubernetes nebo Service Fabric. Zde použijeme Docker Compose. Docker Compose je skvělé pro místní ladění a testování v průběhu vývojového cyklu.

## <a name="prerequisites"></a>Požadavky

::: moniker range="vs-2017"
* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **úlohy pro vývoj napříč platformami .NET Core**
::: moniker-end

::: moniker range=">= vs-2019"
* [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou **pro vývoj webu**, nástroje **Azure** nebo **.NET Core**
* [.NET Core 2.2 Vývojové nástroje](https://dotnet.microsoft.com/download/dotnet-core/2.2) pro vývoj s .NET Core 2.2
* [.NET Core 3 Vývojové nástroje](https://dotnet.microsoft.com/download/dotnet-core/3.1) pro vývoj s .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Vytvoření projektu webové aplikace

V sadě Visual Studio vytvořte projekt `WebFrontEnd`ASP.NET základní webové **aplikace** s názvem . Vyberte **webovou aplikaci** a vytvořte webovou aplikaci se stránkami Razor. 
  
::: moniker range="vs-2017"

Nevybírejte **povolit podporu Dockeru**. Podporu Dockeru přidáte později.

![Snímek obrazovky s vytvořením webového projektu](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Snímek obrazovky s vytvořením webového projektu](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

Nevybírejte **povolit podporu Dockeru**. Podporu Dockeru přidáte později.

![Snímek obrazovky s vytvořením webového projektu](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Vytvoření projektu webového rozhraní API

Přidejte projekt do stejného řešení a nazvěte jej *MyWebAPI*. Jako typ projektu vyberte **rozhraní API** a zrušte zaškrtnutí políčka Konfigurovat pro **protokol HTTPS**. V tomto návrhu používáme pouze SSL pro komunikaci s klientem, nikoli pro komunikaci mezi kontejnery ve stejné webové aplikaci. Pouze `WebFrontEnd` potřebuje HTTPS a kód v příkladech předpokládá, že jste zrušili toto políčko.

::: moniker range="vs-2017"
   ![Snímek obrazovky s vytvořením projektu webového rozhraní API](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Snímek obrazovky s vytvořením projektu webového rozhraní API](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Přidání kódu pro volání webového rozhraní API

1. V `WebFrontEnd` projektu otevřete *soubor Index.cshtml.cs* a `OnGet` nahraďte metodu následujícím kódem.

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
    > V reálném kódu, neměli byste `HttpClient` zlikvidovat po každém požadavku. Doporučené postupy naleznete v [tématu Použití httpclientfactory k implementaci odolných požadavků HTTP](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Pro rozhraní .NET Core 3.1 ve Visual Studiu 2019 nebo novější používá šablona webového rozhraní API rozhraní WeatherForecast API, takže odkomentujte tento řádek a zakomentujte řádek pro ASP.NET 2.x.

1. V souboru *Index.cshtml* přidejte `ViewData["Message"]` řádek, který se zobrazí, aby soubor vypadal jako následující kód:
    
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

1. (pouze ASP.NET 2.x) Nyní v projektu webového rozhraní API přidejte kód do řadiče hodnoty a přizpůsobte zprávu vrácenou rozhraním API pro volání, které jste přidali z *webfrontendu*.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    S rozhraním .NET Core 3.1 to nepotřebujete, protože můžete použít rozhraní API WeatherForecast, které již existuje. Je však nutné zakomentovat volání <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> v metodě `Configure` v *Startup.cs*, protože tento kód používá http, nikoli HTTPS, k volání webového rozhraní API.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. V `WebFrontEnd` projektu zvolte **Přidat > podpora orchestrator kontejneru**. Zobrazí se dialogové okno **Možnosti podpory Dockeru.**

1. Zvolte **Docker Compose**.

1. Vyberte si cílový operační systém, například Linux.

   ![Snímek obrazovky s výběrem cílového operačního systému](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio vytvoří soubor *docker-compose.yml* a *soubor .dockerignore* v uzlu **docker-compose** v řešení a tento projekt se zobrazí tučným písmem, což ukazuje, že se jedná o projekt při spuštění.

   ![Snímek obrazovky Průzkumníka řešení s přidaným projektem docker-compose](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.yml* se zobrazí takto:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   Soubor *.dockerignore* obsahuje typy souborů a přípony, které nechcete, aby Docker zahrnout do kontejneru. Tyto soubory jsou obecně spojeny s vývojovým prostředím a správě zdrojového kódu, nikoli součástí aplikace nebo služby, kterou vyvíjíte.

   Podrobnosti o spuštěných příkazech naleznete v části **Nástroje kontejneru** ve výstupním podokně.  Můžete vidět nástroj příkazového řádku docker-compose se používá ke konfiguraci a vytvoření kontejnerů runtime.

1. V projektu webového rozhraní API znovu klikněte pravým tlačítkem myši na uzel projektu a zvolte **Přidat** > **podporu orchestratoru kontejneru**. Zvolte **Docker Compose**a pak vyberte stejný cílový operační systém.  

    > [!NOTE]
    > V tomto kroku Visual Studio nabídne k vytvoření dockerfile. Pokud to u děláte na projektu, který již má podporu Dockeru, budete vyzváni, zda chcete přepsat existující Dockerfile. Pokud jste v souboru Dockerfile provedli změny, které chcete zachovat, zvolte ne.

    Visual Studio provede některé změny vašeho dockeru tvoří YML soubor. Nyní jsou zahrnuty obě služby.

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

1. Spusťte web místně nyní (F5 nebo Ctrl + F5) a ověřte, zda funguje podle očekávání. Pokud je vše správně nakonfigurováno s verzí .NET Core 2.x, zobrazí se zpráva "Hello from webfrontend a webapi (s hodnotou 1)."  S rozhraním .NET Core 3 se zobrazí data předpovědi počasí.

   První projekt, který použijete při přidání orchestrace kontejneru je nastavena na spuštění při spuštění nebo ladění. Akci spuštění můžete nakonfigurovat v **aplikaci Vlastnosti projektu** pro projekt docker-compose.  V uzlu projektu docker-compose otevřete místní nabídku klepnutím pravým tlačítkem myši a pak zvolte **Vlastnosti**nebo použijte Alt+Enter.  Následující snímek obrazovky ukazuje vlastnosti, které byste chtěli pro řešení použité zde.  Můžete například změnit stránku, která je načtena přizpůsobením vlastnosti **URL služby.**

   ![Snímek obrazovky s vlastnostmi projektu docker-compose](media/tutorial-multicontainer/launch-action.png)

   Zde je to, co vidíte při spuštění (verze .NET Core 2.x):

   ![Snímek obrazovky spuštěné webové aplikace](media/tutorial-multicontainer/webfrontend.png)

   Webová aplikace pro rozhraní .NET 3.1 zobrazuje data o počasí ve formátu JSON.

## <a name="next-steps"></a>Další kroky

Podívejte se na možnosti nasazení [kontejnerů do Azure](/azure/containers).

## <a name="see-also"></a>Viz také
  
[Docker Compose](https://docs.docker.com/compose/)  
[Nástroje kontejneru](/visualstudio/containers/)
