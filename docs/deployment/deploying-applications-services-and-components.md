---
title: První seznámení s nasazováním
description: Seznamte se s možnostmi pro nasazování aplikací ze sady Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8933127940cd8155bbf0854fd19c559022bceecb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912162"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>První pohled na nasazení v aplikaci Visual Studio

Nasazením aplikace, služby nebo součásti ji distribuujete pro instalaci na jiné počítače, zařízení nebo servery nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení. (Mnoho typů aplikací podporuje i další nástroje pro nasazení, jako je například nasazení z příkazového řádku nebo NuGet, které zde nejsou popsané.)

Podrobné pokyny k nasazení najdete v tématu rychlé starty a kurzy. Přehled možností nasazení najdete v tématu [Jaké možnosti publikování jsou pro mě nejvhodnější?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Nasazení do místní složky

Nasazení do místní složky se obvykle používá pro testování nebo pro zahájení dvoufázového nasazení, ve kterém se pro konečné nasazení používá jiný nástroj.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** a. **.NET Core**: k nasazení do místní složky použijte nástroj pro **publikování** . Přesné možnosti, které jsou k dispozici, závisí na typu vaší aplikace. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **Publish** (Publikovat). (Pokud jste dosud nenakonfigurovali žádné publikační profily, musíte vybrat možnost **vytvořit nový profil**.) Pak vyberte **Složka**. Další informace najdete v tématu [nasazení do místní složky](quickstart-deploy-to-local-folder.md).

    ![Snímek obrazovky, který zobrazuje výběr možnosti Publikovat.](../deployment/media/quickstart-publish.png)

- **Plocha Windows**: desktopovou aplikaci pro Windows můžete publikovat do složky pomocí nasazení ClickOnce. Uživatelé pak mohou aplikaci nainstalovat jediným kliknutím. Další informace najdete v následujících článcích:

  - [Nasazení .NET Framework desktopové aplikace pro Windows pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [Nasazení aplikace klasické pracovní plochy Windows pomocí technologie ClickOnce](quickstart-deploy-using-clickonce-folder.md).
  - [Nasazení aplikace C++/CLR pomocí technologie ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo, v případě jazyka C/C++, naleznete v tématu [nasazení nativní aplikace pomocí projektu instalace](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publikování do Azure

- **ASP.NET**, **ASP.NET Core**, **Python** a **Node.js**: publikování do Azure App Service nebo Azure App Service na platformě Linux (pomocí kontejnerů) pomocí jedné z následujících metod:

  - Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).
  - Pro jednorázové (nebo ruční) nasazení aplikací použijte nástroj **publikování** v aplikaci Visual Studio.

  Pro nasazení, které poskytuje přizpůsobenější konfiguraci serveru, můžete k nasazení aplikací na virtuální počítač Azure použít taky nástroj **publikovat** .

  Chcete-li použít nástroj **publikovat** , klikněte pravým tlačítkem myši na projekt v Průzkumník řešení a vyberte **publikovat**. (Pokud jste dříve nakonfigurovali všechny publikační profily, musíte vybrat **vytvořit nový profil**.) V dialogovém okně **publikovat** vyberte možnost **App Service** nebo **Azure Virtual Machines** a pak postupujte podle kroků konfigurace.

  ![Snímek obrazovky, který zobrazuje výběr Azure App Service.](../deployment/media/quickstart-publish-azure-new.png "Zvolit Azure App Service")

  Počínaje verzí Visual Studio 2017 verze 15,7 můžete nasadit aplikace ASP.NET Core pro App Service v systému Linux.

  V případě aplikací v Pythonu se také zobrazuje téma [publikování v Pythonu do Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Úvodní informace najdete v tématu [publikování do Azure](quickstart-deploy-to-azure.md) a [publikování na Linux](quickstart-deploy-to-linux.md). Viz také téma [publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Informace o nasazení pomocí Gitu najdete v tématu [průběžné nasazování ASP.NET Core do Azure pomocí Gitu](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Pokud ještě nemáte účet Azure, můžete se [zaregistrovat tady](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Publikování na webu nebo nasazení do sdílené síťové složky

- **ASP.NET**, **ASP.NET Core**, **Node.js** a **Python**: k nasazení na web pomocí protokolu FTP nebo nasazení webu můžete použít nástroj pro **publikování** . Další informace najdete v tématu [nasazení na web](quickstart-deploy-to-a-web-site.md).

    V Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat**. (Pokud jste dříve nakonfigurovali všechny publikační profily, musíte vybrat **vytvořit nový profil**.) V nástroji **publikování** vyberte požadovanou možnost a postupujte podle kroků konfigurace.

    ![Snímek obrazovky, který zobrazuje výběr služby IIS.](../deployment/media/quickstart-publish-iis.png)

    Informace o importu profilu publikování v aplikaci Visual Studio naleznete v tématu [Import nastavení publikování a nasazení do služby IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Aplikace a služby ASP.NET můžete také nasadit různými způsoby. Další informace najdete v tématu [nasazení webových aplikací a služeb ASP.NET](/aspnet/overview/deployment).

- **Plocha Windows**: pomocí nasazení ClickOnce můžete publikovat desktopovou aplikaci pro Windows na webový server nebo do síťové sdílené složky. Uživatelé pak mohou aplikaci nainstalovat jediným kliknutím. Další informace najdete v následujících článcích:

  - [Nasazení .NET Framework desktopové aplikace pro Windows pomocí technologie ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [Nasazení desktopové aplikace pro Windows .NET pomocí technologie ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [Nasazení aplikace C++/CLR pomocí technologie ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Publikovat do Microsoft Store

Ze sady Visual Studio můžete vytvořit balíčky aplikací pro nasazení do Microsoft Store.

- **UWP**: aplikaci můžete zabalit a nasadit pomocí položek nabídky. Další informace najdete v tématu [zabalení aplikace pro UWP pomocí sady Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Snímek obrazovky, který ukazuje vytvoření balíčku aplikace](../deployment/media/feature-tour-create-app-package.png)

- **Plocha Windows**: nasazení můžete nasadit do Microsoft Store pomocí mostu pro stolní počítače, který začíná v rámci sady Visual Studio 2017 verze 15,4. Pokud to chcete provést, Začněte vytvořením projektu pro vytváření balíčků aplikací pro Windows. Další informace najdete v tématu [zabalení desktopové aplikace pro Microsoft Store (most pro stolní počítače)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Snímek obrazovky, který ukazuje výběr projektu pro balení aplikace systému Windows.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Nasazení do zařízení (UWP)

Pokud nasazujete aplikaci UWP pro testování na zařízení, přečtěte si téma [spuštění aplikací pro UWP ve vzdáleném počítači v aplikaci Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Vytvoření instalačního balíčku (Windows Desktop)

Pokud vyžadujete komplexnější instalaci desktopové aplikace, než je ClickOnce, můžete vytvořit balíček Instalační služba systému Windows (instalační soubor MSI nebo EXE) nebo vlastní zaváděcí nástroj.

- Instalační balíček založený na MSI se dá vytvořit pomocí [rozšíření sady nástrojů WIX sady Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension). Toto je sada nástrojů příkazového řádku.
- Instalační balíček MSI nebo EXE se dá vytvořit pomocí programu [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) ze Flexera softwaru. Program InstallShield lze použít se sadou Visual Studio 2017 a novějšími verzemi. Edice Community není podporovaná.

  > [!NOTE]
  > Aplikace InstallShield omezená Edition již není součástí sady Visual Studio a není podporována v aplikaci Visual Studio 2017 a novějších verzích. Podívejte se na [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o budoucí dostupnost.

- Instalační balíček MSI nebo EXE se dá vytvořit pomocí projektu instalace (vdproj). Chcete-li použít tuto možnost, nainstalujte [rozšíření instalační program pro Visual Studio projekty](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).
- Požadované součásti pro desktopové aplikace můžete nainstalovat také tak, že nakonfigurujete obecný instalační program, který se označuje jako zaváděcí nástroj. Další informace najdete v tématu [požadavky na nasazení aplikací](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-a-test-lab"></a>Nasazení do testovacího prostředí

Nasazením aplikací do virtuálních prostředí můžete povolit pokročilejší vývoj a testování. Další informace najdete v tématu [testování v testovacím prostředí](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Průběžné nasazování

K povolení průběžného nasazování aplikace můžete použít Azure Pipelines. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) a [nasazení do Azure](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>Nasazení databáze SQL

- [Změna cílové platformy a publikování databázového projektu (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Nasazení Analysis Servicesho projektu (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Nasazení projektů a balíčků služby SSIS (Integration Services)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Sestavení a nasazení do místní databáze](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Nasazení pro jiné typy aplikací

| Typ aplikace | Scénář nasazení | Odkaz |
| --- | --- | --- |
| **Aplikace Office** | Doplněk pro Office můžete publikovat ze sady Visual Studio. | [Nasazení a publikování doplňku pro Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF nebo služba OData** | Jiné aplikace mohou používat služby WCF RIA, které nasadíte na webový server. | [Vývoj a nasazení Datové služby WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch již není v sadě Visual Studio 2017 podporován, ale lze jej stále nasadit ze sady Visual Studio 2015 a starší. | [Nasazení aplikací LightSwitch](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste si vybrali rychlý přehled možností nasazení pro různé aplikace.

> [!div class="nextstepaction"]
> [Jaké možnosti publikování jsou pro mě nejvhodnější?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)