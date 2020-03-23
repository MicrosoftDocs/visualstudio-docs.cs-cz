---
title: Publikování do Azure importem nastavení publikování
description: Vytvoření a import profilu publikování pro nasazení aplikace z Visual Studia do služby Azure App Service
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd040b613a5b982050d651f341456c5fafc2954b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679189"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby Azure App Service importem nastavení publikování ve Visual Studiu

Pomocí nástroje **Publikovat** můžete importovat nastavení publikování a pak aplikaci nasadit. V tomto článku používáme nastavení publikování pro službu Azure App Service, ale můžete použít podobné kroky k importu nastavení publikování ze [služby IIS](../deployment/tutorial-import-publish-settings-iis.md). V některých případech může být použití profilu nastavení publikování rychlejší než ruční konfigurace nasazení služby pro každou instalaci sady Visual Studio.

Tyto kroky platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v sadě Visual Studio. Můžete také importovat nastavení publikování pro aplikace [Pythonu.](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Generování souboru nastavení publikování ze služby Azure App Service
> * Import souboru nastavení publikování do sady Visual Studio
> * Nasazení aplikace do služby Azure App Service

Soubor nastavení publikování (*\*.publishsettings*) se liší od profilu publikování (*\*.pubxml*) vytvořeného v sadě Visual Studio. Soubor nastavení publikování je vytvořen službou Azure App Service a pak ho můžete importovat do Sady Visual Studio.

> [!NOTE]
> Pokud potřebujete pouze zkopírovat profil publikování sady Visual Studio*\*(soubor PubXML)* z jedné instalace sady Visual Studio do jiné, můžete najít profil publikování, * \<název\>profilu .pubxml*, ve * \\ složce<název\>projektu \Properties\PublishProfiles* pro spravované typy projektů. Weby nahlédnou do složky *\App_Data.* Profily publikování jsou soubory XML MSBuild.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* Musíte mít nainstalovanou Visual Studio 2019 a **ASP.NET a zatížení vývoje webu.**

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.
::: moniker-end

::: moniker range="vs-2017"

* Musíte mít nainstalovanou Visual Studio 2017 a **úlohy ASP.NET a vývoj webových** aplikací.

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.
::: moniker-end

* Vytvořte službu Aplikace Azure. Podrobné pokyny najdete [v tématu Nasazení webové aplikace ASP.NET Core do Azure pomocí Visual Studia](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v sadě Visual Studio

1. V počítači se systémem Visual Studio vytvořte nový projekt.

    Zvolte správnou šablonu. V tomto příkladu zvolte **buď ASP.NET webovou aplikaci (.NET Framework)** nebo (pouze pro C#) **ASP.NET základní webovou aplikaci**a klepněte na tlačítko **OK**.

    Pokud zadané šablony projektu nevidíte, klikněte v levém podokně dialogového okna **Nový projekt** na odkaz Otevřít instalační program sady Visual **Studio.** Spustí se instalační program pro Visual Studio. Nainstalujte **úlohu ASP.NET a vývoje webu.**

    Šablona projektu, kterou zvolíte (ASP.NET nebo ASP.NET core), musí odpovídat verzi ASP.NET nainstalované na webovém serveru.

1. Zvolte **buď MVC** (.NET Framework) nebo **webovou aplikaci (Model-View-Controller)** (pro .NET Core), a ujistěte se, že je **vybráno žádné ověřování,** a klepněte na tlačítko **OK**.

1. Zadejte název jako **MyWebApp** a klepněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

1. Zvolte **sestavení** > **sestavení řešení** k sestavení projektu.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Vytvoření souboru nastavení publikování ve službě Azure App Service

1. Na webu Azure Portal otevřete službu Azure App Service.

1. Klikněte na **Získat profil publikování** a uložte profil místně.

    ![Získání profilu publikování](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Soubor s příponou *souboru .publishsettings* byl vygenerován v umístění, kam jste jej uložili. Následující kód ukazuje částečný příklad souboru (v čitelnějším formátování).

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

    Předchozí soubor *.publishsettings obvykle obsahuje dva profily publikování, které můžete použít v sadě Visual Studio, jeden k nasazení pomocí nasazení webu a jeden pro nasazení pomocí protokolu FTP. Předchozí kód zobrazuje profil nasazení webu. Oba profily budou importovány později při importu profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v Sadě Visual Studio a nasazení

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili soubor nastavení publikování, importovali ho do Sady Visual Studio a nasadili ASP.NET aplikaci do služby Azure App Service. Můžete chtít přehled možností publikování v sadě Visual Studio.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
