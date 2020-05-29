---
title: Publikování do Azure importem nastavení publikování
description: Vytvořte a importujte profil publikování pro nasazení aplikace ze sady Visual Studio na Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd316956f8e6c385cd59c017af50452b07537dc6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183311"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace pro Azure App Service importem nastavení publikování v aplikaci Visual Studio

Pomocí nástroje **publikovat** můžete importovat nastavení publikování a pak aplikaci nasadit. V tomto článku používáme nastavení publikování pro Azure App Service, ale podobný postup můžete použít k importu nastavení publikování z [IIS](../deployment/tutorial-import-publish-settings-iis.md). V některých scénářích může být použití profilu nastavení publikování rychlejší než ruční konfigurace nasazení na službu pro každou instalaci sady Visual Studio.

Tyto kroky platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v aplikaci Visual Studio. Můžete také importovat nastavení publikování pro aplikace v [Pythonu](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) .

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Vygenerujte soubor nastavení publikování z Azure App Service
> * Import souboru nastavení publikování do sady Visual Studio
> * Nasazení aplikace do Azure App Service

Soubor nastavení publikování (* \* . publishsettings*) se liší od publikačního profilu (* \* . pubxml*) vytvořeného v aplikaci Visual Studio. Soubor nastavení publikování se vytvoří pomocí Azure App Service a pak ho můžete importovat do sady Visual Studio.

> [!NOTE]
> Pokud potřebujete kopírovat profil publikování sady Visual Studio (soubor* \* . pubxml* ) z jedné instalace sady Visual Studio na jiný, můžete najít profil publikování * \<profilename\> . pubxml*ve složce * \\<ProjectName \> \Properties\PublishProfiles* pro spravované typy projektů. Pro weby se podívejte do složky *\ App_Data* . Profily publikování jsou soubory XML MSBuild.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoje pro ASP.NET a web** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   a nainstalujte si ji zdarma.
::: moniker-end

::: moniker range="vs-2017"

* Musíte mít nainstalovanou aplikaci Visual Studio 2017 a úlohu **vývoje pro ASP.NET a web** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   a nainstalujte si ji zdarma.
::: moniker-end

* Vytvořte Azure App Service. Podrobné pokyny najdete v tématu [nasazení webové aplikace v ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v aplikaci Visual Studio

1. V počítači se sadou Visual Studio vytvořte nový projekt.

    Vyberte správnou šablonu. V tomto příkladu zvolte buď **ASP.NET webová aplikace (.NET Framework)** , nebo (pouze pro C#) **ASP.NET Core webové aplikace**a klikněte na tlačítko **OK**.

    Pokud nevidíte zadané šablony projektu, klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Nainstalujte úlohu **vývoje ASP.NET a webu** .

    Šablona projektu, kterou zvolíte (ASP.NET nebo ASP.NET Core), musí odpovídat verzi ASP.NET nainstalované na webovém serveru.

1. Zvolte **MVC** (.NET Framework) nebo **Webová aplikace (Model-View-Controller)** (pro .NET Core) a ujistěte se, že není vybrané **žádné ověřování** , a pak klikněte na **OK**.

1. Zadejte název jako **MyWebApp** a klikněte na **OK**.

    Visual Studio vytvoří projekt.

1. Vyberte **sestavit sestavení**  >  **řešení** a sestavte projekt.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Vytvořte soubor nastavení publikování v Azure App Service

1. V Azure Portal otevřete Azure App Service.

1. Klikněte na **získat profil publikování** a profil uložte místně.

    ![Získat profil publikování](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Soubor s příponou *. publishsettings* byl vygenerován v umístění, kam jste uložili soubor. Následující kód ukazuje částečný příklad souboru (v čitelnějším formátování).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    Předchozí soubor *. publishsettings obvykle obsahuje dva profily publikování, které lze použít v aplikaci Visual Studio, jeden pro nasazení pomocí Nasazení webu a druhý pro nasazení pomocí protokolu FTP. Předchozí kód ukazuje profil Nasazení webu. Oba profily budou importovány později po importu profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v aplikaci Visual Studio a nasazení

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili soubor nastavení publikování, importovali jste ho do sady Visual Studio a nasadili jste aplikaci ASP.NET, která Azure App Service. Můžete chtít přehled možností publikování v aplikaci Visual Studio.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
