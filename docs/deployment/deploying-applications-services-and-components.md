---
title: Nasazení základních charakteristikách
description: Další informace o dostupných možnostech při nasazování aplikací ze sady Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 682010bc4235948918b3bffce70d04d5db0781af
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861628"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Rychlý start: Nejdřív se podívejte na nasazení v sadě Visual Studio

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na jiné počítače, zařízení nebo serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení. (Mnoho typů aplikací podporují další nástroje pro nasazení, jako je například nasazení příkazového řádku nebo NuGet, které nebyly popsány zde.)

Najdete v rychlých startů a kurzů pro podrobné pokyny. Přehled možností nasazení, najdete v části [jaké možnosti publikování jsou pro mě nejlepší?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Nasazení do místní složky

Nasazení do místní složky se obvykle používá pro testování, nebo začněte dvoufázové nasazení, ve kterém se používá jiný nástroj pro poslední nasazení.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, a. **.NET Core**: pomocí nástroje Publish pro nasazení do místní složky. Přesné dostupné možnosti závisí na typ vaší aplikace. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **publikovat**. (Pokud jste dříve nakonfigurovali žádné profily publikování, kterou musí a klikněte na **vytvořit nový profil**.) Dále zvolte **složky**. Další informace najdete v tématu [nasadit do místní složky](quickstart-deploy-to-local-folder.md).

    ![Tlačítko Publikovat](../deployment/media/quickstart-publish.png)

- **Modul runtime Visual C++**: můžete nasadit modulu runtime Visual C++ pomocí místní nasazení nebo statického propojení. Další informace najdete v tématu [nasazování nativních desktopových aplikací (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Publikování do Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, a **Node.js**: publikovat nástroj můžete použít k rychlému nasazení aplikací do služby Azure App Service nebo do Azure Virtual Počítač. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **publikovat**. (Pokud jste dříve nakonfigurovali žádné profily publikování, kterou musí a klikněte na **vytvořit nový profil**.) V dialogovém okně Publikovat zvolit buď **služby App Service** nebo **Azure Virtual Machines**a pak postupujte podle kroků konfigurace.

    ![Zvolte Azure App Service](../deployment/media/quickstart-publish-azure.png "zvolte služby Azure App Service")

    V sadě Visual Studio 2017 verze 15.7 nebo novější, můžete nasazovat aplikace ASP.NET Core **služby App Service pro Linux**.

    Aplikace v Pythonu, také naleznete v tématu [Python - publikování do služby Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Rychlý úvod naleznete zde [publikovat do Azure](quickstart-deploy-to-azure.md) a [publikovat do Linuxu](quickstart-deploy-to-linux.md). Viz také [publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Nasazení přes Git, najdete v tématu [průběžné nasazování ASP.NET Core do Azure pomocí Gitu](/aspnet/core/publishing/azure-continuous-deployment).

    Informace o importu profilu publikování z Azure App Service se sadou Visual Studio najdete v tématu [importovat nastavení publikování a nasazení do Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Pokud ještě nemáte účet Azure, můžete si [zaregistrovat](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publikování na Web nebo nasadit do sdílené síťové složky

- **ASP.NET**, **ASP.NET Core**, **Node.js**, a **Python**: můžete použít nástroj pro publikování nasazení webu pomocí protokolu FTP nebo Webdeploy. Další informace najdete v tématu [nasadit na webový server](quickstart-deploy-to-a-web-site.md).

    V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **publikovat**. (Pokud jste dříve nakonfigurovali žádné profily publikování, kterou musí a klikněte na **vytvořit nový profil**.) V nástroji pro publikování zvolte si možnost a postupujte podle kroků konfigurace.

    ![Zvolte službu IIS, FTP atd.](../deployment/media/quickstart-publish-iis-ftp.png)

    Informace o importu profilu publikování ve Visual Studio najdete v tématu [importovat nastavení publikování a nasazení do služby IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Můžete také nasadit aplikace ASP.NET a služby v celou řadou způsobů. Další informace najdete v tématu [nasazení webových aplikací a služeb ASP.NET](http://www.asp.net/aspnet/overview/deployment).

- **Modul runtime Visual C++**: můžete nasadit modulu runtime Visual C++ pomocí Centrální nasazení. Další informace najdete v tématu [nasazování nativních desktopových aplikací (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Windows desktop** můžete publikovat aplikace klasické pracovní plochy Windows na webový server nebo síťové sdílené pomocí nasazení ClickOnce. Uživatelé pak mohou aplikaci nainstalovat jediným kliknutím. Další informace najdete v tématu [nasazení stolní aplikace pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) a [nasazení nativní aplikace pomocí technologie ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Publikování do Microsoft Store

Ze sady Visual Studio můžete vytvořit balíčky aplikací pro nasazení na Microsoft Store.

- **UPW**: můžete balíček aplikace a nasadit ho pomocí položky nabídky. Další informace najdete v tématu [balíček aplikace pro UPW pomocí sady Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Vytvoření balíčku aplikace](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows desktop**: můžete nasadit do Microsoft Store pomocí přemostění na Desktop spuštění v sadě Visual Studio 2017 verze 15.4. Provedete to tak, začněte tím, že vytvoříte projekt Windows Application Packaging. Další informace najdete v tématu [balíček desktopové aplikace pro Microsoft Store (přemostění na Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Desktop bridge](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Nasazení do zařízení (UPW)

Pokud provádíte nasazení aplikace pro UPW pro testování na zařízení, přečtěte si téma [aplikací pro UWP spuštění na vzdáleném počítači v sadě Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Vytvoření instalačního balíčku (klienta Windows)

Pokud potřebujete více o složitou instalace aplikace pracovní plochy než [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) může poskytovat, můžete vytvořit instalační balíček, projekt instalace nebo vlastní zaváděcí nástroj.

- Instalační program na základě Instalační služby MSI WiX lze vytvořit pomocí [rozšíření Visual Studio 2017 WiX Toolset](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera softwaru může být použit s Visual Studio 2017 (Community Edition nejsou podporovány). Všimněte si, že program InstallShield Limited Edition je již součástí sady Visual Studio a v sadě Visual Studio 2017; se nepodporuje Obraťte se na [Flexera softwaru](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o budoucí dostupnosti.

- Pokud chcete vytvořit projekt instalace (vdproj), nainstalujte [projekty instalačního programu Visual Studio 2017 rozšíření](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Požadované součásti pro aplikace klasické pracovní plochy můžete nainstalovat pomocí konfigurace obecného instalačního programu, který je označován jako zaváděcí nástroj. Další informace najdete v tématu [nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Nasazení do testovací laboratoře

Můžete povolit složitější vývoj a testování nasazení aplikací ve virtuálních prostředích. Další informace najdete v tématu [testů v testovacím prostředí](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Nasazení DevOps

Ve vývojovém týmu můžete použít kanály Azure umožnit průběžné nasazování vaší aplikace. Další informace najdete v tématu [kanály Azure](/azure/devops/pipelines/index?view=vsts) a [nasadit do Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Nasazení pro další typy aplikací

| Typ aplikace | Scénář nasazení | Odkaz |
| --- | --- | --- |
| **Aplikace Office** | Můžete publikovat doplněk pro Office v sadě Visual Studio. | [Nasazení a publikování vašeho doplňku Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Služby WCF nebo OData** | Když nasadíte na webový server služby WCF RIA můžete používat další aplikace. | [Vývoj a nasazení služeb WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **Aplikace LightSwitch** | Aplikace LightSwitch je již nejsou podporovány v sadě Visual Studio 2017, ale je stále možné nasadit ze sady Visual Studio 2015 a starší. | [Nasazení aplikací LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste provedli rychlý pohled na možnosti nasazení pro různé aplikace.

> [!div class="nextstepaction"]
> [Jaké možnosti publikování jsou pro mě nejlepší?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
