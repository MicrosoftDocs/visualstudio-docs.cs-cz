---
title: Ladění aplikací v místním kontejneru Docker | Microsoft Docs
description: Naučte se, jak upravit aplikaci, která běží v místním kontejneru Docker, aktualizujte kontejner pomocí možností upravit a aktualizovat a pak nastavte zarážky ladění.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916525"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Ladění aplikací v místním kontejneru Docker

Visual Studio poskytuje konzistentní způsob vývoje kontejnerů Docker a místní ověření aplikace. Můžete spouštět a ladit své aplikace v kontejnerech Linux nebo Windows spuštěných na místní ploše Windows s nainstalovaným Docker a nemusíte při každém provedení změny kódu restartovat kontejner.

Tento článek ukazuje, jak pomocí sady Visual Studio spustit aplikaci v místním kontejneru Docker, provést změny a pak aktualizovat prohlížeč, aby se změny zobrazily. Tento článek také ukazuje, jak nastavit zarážky pro ladění pro aplikace s využitím kontejnerů. Mezi podporované typy projektů patří .NET Framework a webové a konzolové aplikace .NET Core. V tomto článku používáme ASP.NET Core Web Apps a .NET Framework konzolové aplikace.

Pokud již máte projekt podporovaného typu, Visual Studio může vytvořit souboru Dockerfile a nakonfigurovat projekt tak, aby běžel v kontejneru. Viz [nástroje kontejneru v aplikaci Visual Studio](overview.md).

## <a name="prerequisites"></a>Požadavky

Chcete-li ladit aplikace v místním kontejneru Docker, musí být nainstalovány následující nástroje:

::: moniker range="vs-2017"

* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s nainstalovanou úlohou vývoje webu

::: moniker-end

::: moniker range="vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s nainstalovanou úlohou vývoje webu

::: moniker-end

Pokud chcete spouštět kontejnery Docker místně, musíte mít místního klienta Docker. Můžete použít [sadu nástrojů Docker](https://www.docker.com/products/docker-toolbox), která vyžaduje, aby byla technologie Hyper-V zakázaná. Můžete také použít [Docker for Windows](https://www.docker.com/get-docker), který používá technologii Hyper-V a vyžaduje systém Windows 10.

Kontejnery Docker jsou k dispozici pro projekty .NET Framework a .NET Core. Pojďme se podívat na dva příklady. Nejdřív se podíváme na webovou aplikaci .NET Core. Pak se podíváme na .NET Framework konzolovou aplikaci.

## <a name="create-a-web-app"></a>Vytvoření webové aplikace

Pokud máte projekt a Přidali jste podporu Docker, jak je popsáno v [přehledu](overview.md), přeskočte tuto část.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Úprava kódu a aktualizace

Chcete-li rychle iterovat změny, můžete aplikaci spustit v kontejneru. Pak můžete pokračovat v provádění změn a zobrazit je stejně jako u IIS Express.

1. Ujistěte se, že je Docker nastavený tak, aby používal typ kontejneru (Linux nebo Windows), který používáte. Pravým tlačítkem myši klikněte na ikonu Docker na hlavním panelu a vyberte možnost **Přepnout na kontejnery Linux** nebo podle potřeby **Přepnout na kontejnery Windows** .

1. (Jenom .NET Core 3 a novější) Úprava kódu a aktualizace běžící lokality, jak je popsáno v této části, nejsou povoleny ve výchozích šablonách v rozhraní .NET Core > = 3,0. Pokud ho chcete povolit, přidejte balíček NuGet [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/). V *Startup.cs*přidejte volání metody rozšíření `IMvcBuilder.AddRazorRuntimeCompilation` do kódu v metodě `ConfigureServices`. Tuto možnost potřebujete jenom v režimu ladění, proto ho zakódovat takto:

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

   Další informace naleznete v tématu [kompilace souborů Razor v ASP.NET Core](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1).

1. Nastavte **konfiguraci řešení** na **ladit**. Potom stisknutím klávesy **Ctrl**+**F5** Sestavte image Docker a spusťte ji místně.

    Když je image kontejneru sestavená a spuštěná v kontejneru Docker, Visual Studio spustí webovou aplikaci ve výchozím prohlížeči.

1. Přejít na stránku *index* . Na této stránce provedeme změny.
1. Vraťte se do sady Visual Studio a otevřete *index. cshtml*.
1. Na konec souboru přidejte následující obsah HTML a pak změny uložte.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. V okně výstup, po dokončení sestavení .NET a zobrazení následujících řádků, přepněte zpět do prohlížeče a aktualizujte stránku:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vaše změny byly provedeny!

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

Změny se často vyžadují ještě další kontroly. Pro tuto úlohu můžete použít funkce ladění sady Visual Studio.

1. V aplikaci Visual Studio otevřete *index.cshtml.cs*.
2. Obsah metody `OnGet` nahraďte následujícím kódem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Nalevo od řádku kódu nastavte zarážku.
4. Chcete-li spustit ladění a stisknout zarážku, stiskněte klávesu F5.
5. Přepněte do sady Visual Studio, abyste zobrazili zarážku. Zkontrolujte hodnoty.

   ![Bod přerušení](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Vytvoření konzolové aplikace .NET Framework

Pokud používáte projekty konzolových aplikací .NET Framework, možnost přidat podporu Docker bez orchestrace není podporována. Můžete i nadále používat následující postup, i když používáte pouze jeden projekt Docker.

1. Vytvořte nový projekt konzolové aplikace .NET Framework.
1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat** **podporu orchestrace kontejnerů** > .  V dialogovém okně, které se zobrazí, vyberte možnost **Docker Compose**. Do projektu se přidá souboru Dockerfile a přidá se Docker Compose projekt s přidruženými podpůrnými soubory.

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

1. V Průzkumník řešení otevřete *program.cs*.
2. Obsah metody `Main` nahraďte následujícím kódem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Nastaví zarážku vlevo od čárového kódu.
4. Stisknutím klávesy F5 spusťte ladění a stiskněte zarážku.
5. Přepněte do sady Visual Studio, abyste viděli zarážku a zkontrolovali hodnoty.

   ![Bod přerušení](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Opakované použití kontejneru

Během cyklu vývoje aplikace Visual Studio znovu sestaví pouze image kontejneru a samotný kontejner při změně souboru Dockerfile. Pokud souboru Dockerfile nezměníte, Visual Studio znovu použije kontejner z předchozího spuštění.

Pokud jste kontejner ručně upravili a chcete ho restartovat pomocí čisticí image kontejneru, použijte příkaz **sestavit** > **vyčistit** v aplikaci Visual Studio a pak Sestavte jako normální.

## <a name="troubleshoot"></a>Řešení problémů

Naučte se [řešit potíže s vývojem pro Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="next-steps"></a>Další kroky

Podrobnější informace získáte v tématu [jak Visual Studio](container-build.md)sestavuje aplikace s využitím kontejnerů.

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Další informace o Docker se sadou Visual Studio, Windows a Azure

* Další informace o [vývoji kontejnerů pomocí sady Visual Studio](/visualstudio/containers).
* Informace o sestavení a nasazení kontejneru Docker najdete v tématu [integrace Docker pro Azure Pipelines](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Rejstřík článků s Windows serverem a nano serverem najdete v tématu [informace o kontejnerech Windows](/virtualization/windowscontainers/).
* Přečtěte si o [službě Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) a Projděte si [dokumentaci ke službě Azure Kubernetes](/azure/aks).
