---
title: Ladění aplikací v místním kontejneru Dockeru | Dokumenty společnosti Microsoft
description: Zjistěte, jak upravit aplikaci, která běží v místním kontejneru Dockeru, aktualizovat kontejner pomocí úprav a aktualizovat a pak nastavit ladění zarážek.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916525"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Ladění aplikací v místním kontejneru Dockeru

Visual Studio poskytuje konzistentní způsob, jak vyvíjet kontejnery Dockeru a ověřit vaši aplikaci místně. Aplikace můžete spouštět a ladit v kontejnerech Linuxu nebo Windows spuštěných na místní ploše Windows s nainstalovaným Dockerem a nemusíte restartovat kontejner pokaždé, když provedete změnu kódu.

Tento článek ukazuje, jak pomocí Visual Studia spustit aplikaci v místním kontejneru Dockeru, provést změny a potom aktualizovat prohlížeč, aby se změny zosakly. Tento článek také ukazuje, jak nastavit zarážky pro ladění pro kontejnerizované aplikace. Mezi podporované typy projektů patří rozhraní .NET Framework a webové a konzolové aplikace .NET Core. V tomto článku používáme ASP.NET základní webové aplikace a konzolové aplikace rozhraní .NET Framework.

Pokud již máte projekt podporovaného typu, Visual Studio můžete vytvořit Dockerfile a nakonfigurovat projekt spustit v kontejneru. Viz [Nástroje kontejneru v sadě Visual Studio](overview.md).

## <a name="prerequisites"></a>Požadavky

Chcete-li ladit aplikace v místním kontejneru Dockeru, musí být nainstalovány následující nástroje:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou pro vývoj webu

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou pro vývoj webu

::: moniker-end

Chcete-li spustit kontejnery Dockeru místně, musíte mít místního klienta Dockeru. Můžete použít [Panel nástrojů Dockeru](https://www.docker.com/products/docker-toolbox), který vyžaduje, aby byla zakázána technologie Hyper-V. Můžete také použít [Docker pro Windows](https://www.docker.com/get-docker), který používá Technologie Hyper-V a vyžaduje Windows 10.

Kontejnery Dockeru jsou k dispozici pro rozhraní .NET Framework a .NET Core projekty. Podívejme se na dva příklady. Nejprve se podíváme na webovou aplikaci .NET Core. Pak se podíváme na konzolovou aplikaci rozhraní .NET Framework.

## <a name="create-a-web-app"></a>Vytvoření webové aplikace

Pokud máte projekt a přidali jste podporu Dockeru, jak je popsáno v [přehledu](overview.md), přeskočte tuto část.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Úprava kódu a aktualizace

Chcete-li rychle itrerate změny, můžete spustit aplikaci v kontejneru. Potom pokračujte v provádění změn a zoáčte je stejně jako se sazí IIS Express.

1. Ujistěte se, že Docker je nastaven na použití typu kontejneru (Linux nebo Windows), který používáte. Klikněte pravým tlačítkem myši na ikonu Dockeru na hlavním panelu a podle potřeby zvolte **Přepnout na linuxové kontejnery** nebo **Přepnout do kontejnerů Windows.**

1. (Pouze rozhraní 3 a novější. Úprava kódu a aktualizace spuštěného webu, jak je popsáno v této části, není povolena ve výchozích šablonách v rozhraní .NET Core >= 3.0. Chcete-li jej povolit, přidejte balíček NuGet [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). V *Startup.cs*přidejte volání metody `IMvcBuilder.AddRazorRuntimeCompilation` rozšíření do `ConfigureServices` kódu v metodě. Stačí pouze to to povoleno v režimu LADĚNÍ, tak kód je následujícím způsobem:

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

   Další informace naleznete [v tématu Kompilace souborů Razor v ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Nastavte **konfiguraci řešení** na **ladění**. Potom stiskněte **kombinaci kláves**+**F5,** abyste vytvořili bitovou kopii Dockeru a spusťte ji místně.

    Když je image kontejneru vytvořená a spuštěná v kontejneru Dockeru, Visual Studio spustí webovou aplikaci ve výchozím prohlížeči.

1. Přejděte na stránku *Rejstřík.* Na této stránce provedeme změny.
1. Vraťte se do sady Visual Studio a otevřete *soubor Index.cshtml*.
1. Přidejte na konec souboru následující obsah HTML a uložte změny.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Ve výstupním okně po dokončení sestavení rozhraní .NET a zobrazení následujících řádků přepněte zpět do prohlížeče a aktualizujte stránku:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vaše změny byly použity!

### <a name="debug-with-breakpoints"></a>Ladění s zarážkou

Často změny vyžadují další kontrolu. Pro tuto úlohu můžete použít funkce ladění sady Visual Studio.

1. V sadě Visual Studio otevřete *Index.cshtml.cs*.
2. Obsah `OnGet` metody se nahradí následujícím kódem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Nalevo od řádku kódu nastavte zarážku.
4. Chcete-li spustit ladění a narazit na zarážku, stiskněte klávesu F5.
5. Přepnutím do sady Visual Studio zobrazíte zarážku. Zkontrolujte hodnoty.

   ![Zarážka](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Vytvoření konzolové aplikace rozhraní .NET Framework

Při použití projektů konzoly rozhraní .NET Framework není možnost přidat podporu Dockeru bez orchestrace podporována. Stále můžete použít následující postup, i když používáte pouze jeden projekt Dockeru.

1. Vytvořte nový projekt aplikace konzoly rozhraní .NET Framework.
1. V Průzkumníku řešení klepněte pravým tlačítkem myši na uzel projektu a potom vyberte **přidat** > **podporu orchestrace kontejneru**.  V zobrazeném dialogovém okně vyberte **příkaz Docker Compose**. Dockerfile je přidán do projektu a Docker Compose projekt s přidruženými soubory podpory je přidán.

### <a name="debug-with-breakpoints"></a>Ladění s zarážkou

1. V Průzkumníku řešení otevřete *Program.cs*.
2. Obsah `Main` metody se nahradí následujícím kódem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Nastavte zarážku nalevo od řádku kódu.
4. Stisknutím klávesy F5 spusťte ladění a stisknete zarážku.
5. Přepnutím do sady Visual Studio zobrazíte zarážku a zkontrolujete hodnoty.

   ![Zarážka](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Opětovné použití kontejneru

Během vývojového cyklu Visual Studio znovu vytvoří pouze vaše image kontejneru a samotného kontejneru při změně Dockerfile. Pokud nezměníte Dockerfile, Visual Studio znovu použije kontejner z dřívějšího spuštění.

Pokud jste ručně upravili kontejner a chcete restartovat s čistou image kontejneru, použijte **příkaz Sestavit** > **čisté** v sadě Visual Studio a pak sestavte jako normální.

## <a name="troubleshoot"></a>Řešení potíží

Přečtěte si, jak [řešit potíže s vývojem aplikace Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Další kroky

Další podrobnosti [načtete, jak Visual Studio vytváří kontejnerizované aplikace](container-build.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Další informace o Dockeru s Visual Studio, Windows a Azure

* Další informace o [vývoji kontejnerů v sadě Visual Studio](/visualstudio/containers).
* Pokud chcete vytvořit a nasadit kontejner Dockeru, přečtěte si informace [o integraci Dockeru pro Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Index článků windows server a nano server naleznete v tématu [informace o kontejneru systému Windows](/virtualization/windowscontainers/).
* Přečtěte si o [službě Azure Kubernetes service](https://azure.microsoft.com/services/kubernetes-service/) a projděte si [dokumentaci ke službě Azure Kubernetes](/azure/aks).
