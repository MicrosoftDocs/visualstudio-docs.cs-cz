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
ms.openlocfilehash: 5af092bbcb987f45b10121f37d40eaa5466c3da5
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062177"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Ladění aplikací v místním kontejneru Docker

Visual Studio poskytuje konzistentní způsob vývoje v kontejneru Docker a místní ověření aplikace. Při každém provedení změny kódu není nutné znovu spustit kontejner.

Tento článek ukazuje, jak pomocí sady Visual Studio spustit webovou aplikaci v ASP.NET Core v místním kontejneru Docker, provést změny a pak aktualizovat prohlížeč, aby se změny projevily. Tento článek také ukazuje, jak nastavit zarážky pro ladění pro kontejnerové ASP.NET Core webové aplikace a .NET Framework konzolové aplikace.

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

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Úprava kódu a aktualizace

Chcete-li rychle iterovat změny, můžete aplikaci spustit v kontejneru. Pak můžete pokračovat v provádění změn a zobrazit je stejně jako u IIS Express.

1. Nastavte **konfiguraci řešení** na **ladit**. Potom stisknutím klávesy **CTRL**+**F5** Sestavte image Docker a spusťte ji místně.

    Když je image kontejneru sestavená a spuštěná v kontejneru Docker, Visual Studio spustí webovou aplikaci ve výchozím prohlížeči.

2. Přejít na stránku *index* . Na této stránce provedeme změny.
3. Vraťte se do sady Visual Studio a otevřete *index. cshtml*.
4. Na konec souboru přidejte následující obsah HTML a pak změny uložte.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

5. V okně výstup, po dokončení sestavení .NET a zobrazení následujících řádků, přepněte zpět do prohlížeče a aktualizujte stránku:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Vaše změny byly provedeny!

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

Změny se často vyžadují ještě další kontroly. Pro tuto úlohu můžete použít funkce ladění sady Visual Studio.

1. V aplikaci Visual Studio otevřete *index.cshtml.cs*.
2. Obsah `OnGet` metody nahraďte následujícím kódem:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Nalevo od řádku kódu nastavte zarážku.
4. Chcete-li spustit ladění a stisknout zarážku, stiskněte klávesu F5.
5. Přepněte do sady Visual Studio, abyste zobrazili zarážku. Zkontrolujte hodnoty.

   ![Bodu](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Vytvoření konzolové aplikace .NET Framework

Pokud používáte projekty konzolových aplikací .NET Framework, možnost přidat podporu Docker bez orchestrace není podporována. Můžete i nadále používat následující postup, i když používáte pouze jeden projekt Docker.

1. Vytvořte nový projekt konzolové aplikace .NET Framework.
1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a pak vyberte **Přidat** > **podporu orchestrace kontejnerů**.  V dialogovém okně, které se zobrazí, vyberte možnost **Docker Compose**. Do projektu se přidá souboru Dockerfile a přidá se Docker Compose projekt s přidruženými podpůrnými soubory.

### <a name="debug-with-breakpoints"></a>Ladění pomocí zarážek

1. V Průzkumník řešení otevřete *program.cs*.
2. Obsah `Main` metody nahraďte následujícím kódem:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Nastaví zarážku vlevo od čárového kódu.
4. Stisknutím klávesy F5 spusťte ladění a stiskněte zarážku.
5. Přepněte do sady Visual Studio, abyste viděli zarážku a zkontrolovali hodnoty.

   ![Bodu](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Opakované použití kontejneru

Během cyklu vývoje aplikace Visual Studio znovu sestaví pouze image kontejneru a samotný kontejner při změně souboru Dockerfile. Pokud souboru Dockerfile nezměníte, Visual Studio znovu použije kontejner z předchozího spuštění.

Pokud jste kontejner ručně upravili a chcete ho restartovat pomocí čisticí image kontejneru, použijte příkaz **sestavit** > **Vyčištění** v aplikaci Visual Studio a pak Sestavte normálním způsobem.

## <a name="troubleshoot"></a>Řešení potíží

Naučte se [řešit potíže s vývojem pro Visual Studio Docker](troubleshooting-docker-errors.md).

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Další informace o Docker se sadou Visual Studio, Windows a Azure

* Další informace o [vývoji kontejnerů pomocí sady Visual Studio](/visualstudio/containers).
* Informace o sestavení a nasazení kontejneru Docker najdete v tématu [integrace Docker pro Azure Pipelines](https://aka.ms/dockertoolsforvsts).
* Rejstřík článků s Windows serverem a nano serverem najdete v tématu [informace o kontejnerech Windows](https://aka.ms/containers).
* Přečtěte si o [službě Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) a Projděte si [dokumentaci ke službě Azure Kubernetes](/azure/aks).
