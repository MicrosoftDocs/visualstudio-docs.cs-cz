---
title: Ladění aplikací v místním kontejneru Dockeru | Microsoft Docs
description: Zjistěte, jak upravit aplikaci spuštěnou v místním kontejneru Dockeru, aktualizovat kontejner pomocí funkce Upravit a aktualizovat a pak nastavit zarážky ladění.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306381"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Ladění aplikací v místním kontejneru Dockeru

Visual Studio poskytuje konzistentní způsob, jak vyvíjet kontejnery Dockeru a ověřovat aplikaci místně.
Aplikace můžete spouštět a ladit v kontejnerech Linuxu nebo Windows běžících na místní ploše Windows s nainstalovaným Dockerem a nemusíte kontejner restartovat pokaždé, když změníte kód.

Tento článek ukazuje, jak pomocí Visual Studio spustit aplikaci v místním kontejneru Dockeru, provést změny a pak aktualizovat prohlížeč, aby se změny prošly. Tento článek také ukazuje, jak nastavit zarážky pro ladění kontejnerizovaných aplikací. Mezi podporované typy projektů patří .NET Framework a webové a konzolové aplikace .NET Core. V tomto článku používáme webové aplikace ASP.NET Core a .NET Framework konzolové aplikace.

Pokud už máte projekt podporovaného typu, Visual Studio soubor Dockerfile a nakonfigurovat ho tak, aby se spouštěl v kontejneru. Viz [Nástroje kontejneru v Visual Studio](overview.md).

## <a name="prerequisites"></a>Požadavky

Pokud chcete ladit aplikace v místním kontejneru Dockeru, musí být nainstalované následující nástroje:

::: moniker range="vs-2017"

* [Visual Studio 2017 s](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nainstalovanou úlohou Vývoj pro web

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019 s](https://visualstudio.microsoft.com/downloads) nainstalovanou úlohou Vývoj pro web

::: moniker-end

::: moniker range="vs-2022"

* [Visual Studio 2022 Preview]() s nainstalovanou úlohou Vývoj pro web

::: moniker-end

Pokud chcete spouštět kontejnery Dockeru místně, musíte mít místního klienta Dockeru. Můžete použít [Docker for Windows](https://www.docker.com/get-docker), který používá Hyper-V a vyžaduje Windows 10.

Kontejnery Dockeru jsou k dispozici pro .NET Framework a projekty .NET Core. Podívejme se na dva příklady. Nejprve se podíváme na webovou aplikaci .NET Core. Pak se podíváme na aplikaci konzoly .NET Framework počítače.

## <a name="create-a-web-app"></a>Vytvoření webové aplikace

Pokud máte projekt a přidali jste podporu Dockeru, jak je popsáno v [přehledu,](overview.md)tuto část přeskočte.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Úprava kódu a aktualizace

Pokud chcete rychle iterovat změny, můžete aplikaci spustit v kontejneru. Pak pokračujte v změnách a prohlížet je stejně jako u IIS Express.

1. Ujistěte se, že je Docker nastavený na použití typu kontejneru (Linux nebo Windows), který používáte. Klikněte pravým tlačítkem na ikonu Dockeru na hlavním panelu a podle potřeby zvolte Switch **to Linux containers** (Přepnout na kontejnery Linuxu) nebo **Switch to Windows containers (Přepnout na kontejnery Windows).**

1. (pouze .NET Core 3 a novější) Úprava kódu a aktualizace spuštěné lokality, jak je popsáno v této části, není ve výchozích šablonách v .NET Core >= 3.0. Pokud ho chcete povolit, přidejte balíček NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). V *souboru Startup.cs* přidejte volání metody rozšíření `IMvcBuilder.AddRazorRuntimeCompilation` do kódu v `ConfigureServices` metodě . Tuto možnost potřebujete povolit pouze v režimu LADĚNÍ, takže ji napište následujícím způsobem:

    ```csharp
    public IWebHostEnvironment Env { get; set; }

    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();

    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif

        // code omitted for brevity
    }
    ```

    Upravte `Startup` metodu následujícím způsobem:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Další informace najdete v tématu Kompilace [souborů Razor v ASP.NET Core.](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true)

1. Nastavte **Konfigurace řešení** na **Ladit.** Potom stisknutím **klávesy Ctrl** + **F5** sestavte image Dockeru a spusťte ji místně.

    Když je image kontejneru sestavená a spuštěná v kontejneru Dockeru, Visual Studio ve výchozím prohlížeči spustí webovou aplikaci.

1. Přejděte na *stránku Index.* Na této stránce budeme provádět změny.
1. Vraťte se Visual Studio a *otevřete soubor Index.cshtml.*
1. Na konec souboru přidejte následující obsah HTML a pak změny uložte.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Po dokončení sestavení .NET a zobrazení následujících řádků v okně výstupu přepněte zpět do prohlížeče a aktualizujte stránku:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vaše změny se použily!

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

Změny často vyžadují další kontrolu. Pro tuto úlohu můžete Visual Studio nástroje .

1. V Visual Studio soubor *Index.cshtml.cs*.
2. Obsah metody `OnGet` nahraďte následujícím kódem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Nalevo od řádku kódu nastavte zarážku.
4. Stisknutím klávesy F5 spusťte ladění a stiskněte zarážku.
5. Přepněte na Visual Studio a zobrazte zarážku. Kontrola hodnot.

   ![Snímek obrazovky znázorňující část kódu pro Index.cshtml.cs v souboru Visual Studio se zarážkou vlevo od řádku kódu zvýrazněnou žlutou barvou](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>Vytvoření .NET Framework konzoly

Při použití .NET Framework projektů konzolových aplikací není možnost přidání podpory Dockeru bez orchestrace podporována. Stále můžete použít následující postup, i když používáte pouze jeden projekt Dockeru.

1. Vytvořte nový projekt .NET Framework konzolové aplikace.
1. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a pak vyberte **Přidat podporu**  >  **orchestrace kontejnerů.**  V dialogovém okně, které se zobrazí, **vyberte Docker Compose**. Do projektu se přidá soubor Dockerfile a přidá se Docker Compose projekt s přidruženými podpůrnými soubory.

### <a name=&quot;debug-with-breakpoints&quot;></a>Ladění pomocí zarážek

1. V Průzkumník řešení otevřete *soubor Program.cs.*
2. Obsah metody `Main` nahraďte následujícím kódem:

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Nastavte zarážku nalevo od řádku kódu.
4. Stisknutím klávesy F5 spusťte ladění a stiskněte zarážku.
5. Přepněte na Visual Studio a zobrazte zarážku a zkontrolujte hodnoty.

   ![Snímek obrazovky s oknem kódu pro program.cs v Visual Studio se zarážkou nastavenou nalevo od řádku kódu, která je zvýrazněná žlutě](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Opakované použití kontejnerů

Během vývojového cyklu Visual Studio znovu sestaví pouze image kontejnerů a samotný kontejner při změně souboru Dockerfile. Pokud soubor Dockerfile nezměníte, Visual Studio kontejner z předchozího spuštění.

Pokud jste kontejner ručně upravili a chcete ho restartovat pomocí čisté image kontejneru, použijte příkaz **Build** Clean v Visual Studio a pak se  >   sestavte jako obvykle.

## <a name="troubleshoot"></a>Řešení potíží

Naučte se [řešit potíže Visual Studio docker development](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Další kroky

Další podrobnosti najdete v tématu How Visual Studio builds containerized apps (Vytváření [kontejnerizovaných aplikací).](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Další informace o Dockeru s Visual Studio, Windows a Azure

* Další informace o vývoji [kontejnerů s Visual Studio](./index.yml).
* Informace o sestavení a nasazení kontejneru Dockeru najdete v tématu [Integrace Dockeru pro Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Rejstřík článků o Windows Serveru a Nano Serveru najdete v článku Informace o [kontejneru Windows.](/virtualization/windowscontainers/)
* Seznamte [se Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) a prohlédněte si Azure Kubernetes Service [dokumentaci.](/azure/aks)
