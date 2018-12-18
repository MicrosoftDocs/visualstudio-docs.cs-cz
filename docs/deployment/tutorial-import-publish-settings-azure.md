---
title: Publikování do Azure pomocí importu nastavení publikování
description: Vytváření a import profilu publikování k nasazení aplikace v sadě Visual Studio do služby Azure App Service
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 804965df5142ddb18c1857a2540c5c69c08c4f9a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058491"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby Azure App Service pomocí importu nastavení publikování v sadě Visual Studio

Můžete použít **publikovat** nástroj k importu nastavení publikování a pak nasadíte aplikaci. V tomto článku používáme nastavení publikování pro Azure App Service, ale můžete použít podobným způsobem k importu nastavení publikování z [IIS](../deployment/tutorial-import-publish-settings-iis.md). V některých scénářích použití publikování profilu nastavení může být rychlejší než ruční konfigurace nasazení do služby pro každou instalaci sady Visual Studio.

Tento postup platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v sadě Visual Studio. Můžete také importovat nastavení publikování pro [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aplikace. Kroky odpovídají Visual Studio 2017 verze 15.6.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Generovat soubor nastavení publikování z Azure App Service
> * Importovat soubor nastavení publikování do sady Visual Studio
> * Nasaďte aplikaci do služby Azure App Service

Soubor nastavení publikování (*\*.publishsettings*) se liší od profil publikování (*\*.pubxml*) vytvořené v sadě Visual Studio. Soubor nastavení publikování se vytvoří ve službě Azure App Service, a pak mohou být naimportovány do sady Visual Studio.

> [!NOTE]
> Pokud potřebujete jenom zkopírujte sady Visual Studio profil publikování (*\*.pubxml* souboru) z jedné instalace sady Visual Studio na jiný, můžete najít profil publikování,  *\<profilename\>.pubxml*v  *\\< projectname\>\Properties\PublishProfiles* složku pro typy spravovaných projektů. Pro moduly websites, podívejte se do části *\App_Data* složky. Publikování profilů jsou soubory XML nástroje MSBuild.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou sadu Visual Studio 2017 a **ASP.NET** a. **NET Framework** úlohy pro vývoj. Pro aplikace .NET Core, musíte také. **.NET Core** pracovního vytížení.

    Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

* Vytvoření služby Azure App Service. Podrobné pokyny najdete v tématu [nasazení webové aplikace ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v sadě Visual Studio

1. Na počítači se systémem Visual Studio, zvolte **souboru** > **nový projekt**.

1. V části **Visual C#**  nebo **jazyka Visual Basic**, zvolte **webové**a potom v prostředním podokně zvolte buď **webová aplikace ASP.NET (.NET Framework)** nebo (C# pouze) **webové aplikace ASP.NET Core**a potom klikněte na tlačítko **OK**.

    Pokud nevidíte zadaný projekt šablony, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Viz požadavky v tomto článku k identifikaci požadované úlohy sady Visual Studio, které je nutné nainstalovat.

1. Zvolte buď **MVC** (.NET Framework) nebo **webové aplikace (Model-View-Controller)** (pro .NET Core) a ujistěte se, že **bez ověřování** je vybrána a potom klikněte na **OK**.

1. Zadejte název, například **MyWebApp** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

1. Zvolte **sestavení** > **sestavit řešení** k sestavení projektu.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Vytvořit soubor nastavení publikování ve službě Azure App Service

1. Na webu Azure Portal otevřete službu Azure App Service.

1. Klikněte na tlačítko **získat profil publikování** profil a uložte ho místně.

    ![Získat profil publikování](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Soubor s *.publishsettings* přípona souboru byl vytvořen v umístění, kam jste jej uložili. Následující kód ukazuje příklad částečného souboru (v přehlednějším formátování).

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
    Předchozí soubor *.publishsettings obvykle obsahuje dva profily publikování, které můžete použít v sadě Visual Studio, z nich se má nasadit pomocí nasazení webu a jeden pro nasazení přes FTP. Předchozí kód zobrazí profil nasazení webu. Oba profily se naimportují později při importu profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v sadě Visual Studio a nasazení

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Další kroky

V tomto kurzu se vytvoří soubor nastavení publikování, importovat ho do sady Visual Studio a nasazení aplikace ASP.NET do služby Azure App Service. Přehled možností publikování v sadě Visual Studio může být vhodné.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
