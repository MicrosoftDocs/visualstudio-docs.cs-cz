---
title: Publikování do služby IIS pomocí importu nastavení publikování
description: Vytváření a import profilu publikování k nasazení aplikace do služby IIS ze sady Visual Studio
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
ms.openlocfilehash: 4da4a45566fc6d773f185a6a34f7e02cb093fff5
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348517"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby IIS pomocí importu nastavení publikování v sadě Visual Studio

Můžete použít **publikovat** nástroj k importu nastavení publikování a pak nasadíte aplikaci. V tomto článku používáme nastavení publikování pro službu IIS, ale můžete použít podobným způsobem k importu nastavení publikování pro [služby Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). V některých scénářích použití publikování profilu nastavení může být rychlejší než ruční konfigurace nasazení do služby IIS pro každou instalaci sady Visual Studio.

Tento postup platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v sadě Visual Studio. Kroky odpovídají Visual Studio 2017 verze 15.6.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Nakonfigurovat službu IIS tak, aby můžete vygenerovat soubor nastavení publikování
> * Vytvořit soubor nastavení publikování
> * Importovat soubor nastavení publikování do sady Visual Studio
> * Nasaďte aplikaci do služby IIS

Soubor nastavení publikování (*\*.publishsettings*) se liší od profil publikování (*\*.pubxml*) vytvořené v sadě Visual Studio. Soubor nastavení publikování se vytvoří ve službě IIS nebo Azure App Service, nebo ji můžete ručně vytvořit a pak může být importován do sady Visual Studio.

> [!NOTE]
> Pokud potřebujete jenom zkopírujte sady Visual Studio profil publikování (\*souboru .pubxml) z jedné instalace sady Visual Studio na jiný, můžete najít profil publikování,  *\<profilename\>.pubxml*, v  *\\< projectname\>\Properties\PublishProfiles* složku pro typy spravovaných projektů. Pro moduly websites, podívejte se do části *\App_Data* složky. Publikování profilů jsou soubory XML nástroje MSBuild.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou sadu Visual Studio 2017 a **ASP.NET** a **rozhraní .NET Framework** úlohy pro vývoj. Pro aplikace .NET Core, musíte také **.NET Core** pracovního vytížení.

    Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

* Generovat soubor nastavení publikování ze služby IIS, musíte mít počítač se systémem Windows Server 2012 nebo Windows Server 2016 a musí mít roli Webový Server služby IIS správně nakonfigurován. Musí také nainstalovaná technologie ASP.NET 4.5 nebo ASP.NET Core. ASP.NET Core, najdete v části [publikování do služby IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). ASP.NET 4.5 naleznete v tématu [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v sadě Visual Studio

1. Na počítači se systémem Visual Studio, zvolte **souboru** > **nový projekt**.

1. V části **Visual C#**  nebo **jazyka Visual Basic**, zvolte **webové**a potom v prostředním podokně zvolte buď **webová aplikace ASP.NET (.NET Framework)** nebo (C# pouze) **webové aplikace ASP.NET Core**a potom klikněte na tlačítko **OK**.

    Pokud nevidíte zadaný projekt šablony, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Viz požadavky v tomto článku k identifikaci požadované úlohy sady Visual Studio, které je nutné nainstalovat.

1. Zvolte buď **MVC** (.NET Framework) nebo **webové aplikace (Model-View-Controller)** (pro .NET Core) a ujistěte se, že **bez ověřování** je vybrána a potom klikněte na **OK**.

1. Zadejte název, například **MyWebApp** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

1. Zvolte **sestavení** > **sestavit řešení** k sestavení projektu.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalace a konfigurace nasazení webu v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvořit soubor nastavení publikování ve službě IIS v systému Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v sadě Visual Studio a nasazení

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Jakmile se aplikace nasadí úspěšně, by se měl spustit automaticky. Pokud se nespustí ze sady Visual Studio, spusťte aplikaci ve službě IIS. Pro ASP.NET Core, budete muset Ujistěte se, že se fond aplikací pro pole **DefaultAppPool** je nastavena na **bez spravovaného kódu**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu se vytvoří soubor nastavení publikování, importovat do sady Visual Studio a nasazení aplikace ASP.NET do služby IIS. Přehled o další možnosti publikování v sadě Visual Studio může být vhodné.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
