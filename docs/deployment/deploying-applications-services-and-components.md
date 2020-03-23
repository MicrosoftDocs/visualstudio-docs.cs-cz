---
title: První seznámení s nasazováním
description: Přečtěte si o možnostech nasazování aplikací z Visual Studia.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 006ecdffd7b109c32f7063fee5f454e43c6c4597
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806927"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>První pohled na nasazení v sadě Visual Studio

Nasazením aplikace, služby nebo součásti je distribuujete pro instalaci na jiných počítačích, zařízeních nebo serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení. (Mnoho typů aplikací podporuje další nástroje nasazení, jako je nasazení příkazového řádku, které zde nejsou popsány.)

Podrobné pokyny k nasazení naleznete v pokynech pro rychlé starty a kurzy. Přehled možností nasazení najdete v tématu [Jaké možnosti publikování jsou pro mě to pravé?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Nasazení do místní složky

Nasazení do místní složky se obvykle používá k testování nebo k zahájení fázovaného nasazení, ve kterém se pro konečné nasazení používá jiný nástroj.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**a . **NET Core**: Pomocí nástroje publikování nasadit do místní složky. Přesné dostupné možnosti závisí na typu aplikace. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat**. (Pokud jste dříve nenakonfigurovali žádné profily publikování, musíte klepnout na tlačítko **Vytvořit nový profil**.) Dále zvolte **Složka**. Další informace naleznete v [tématu Deploy to a local folder](quickstart-deploy-to-local-folder.md).

    ![Zvolte Publikovat](../deployment/media/quickstart-publish.png)

- **Plocha systému Windows** Desktopovou aplikaci systému Windows můžete publikovat do složky pomocí nasazení ClickOnce. Uživatelé pak mohou aplikaci nainstalovat jediným kliknutím. Další informace najdete [v tématu Nasazení aplikace klasické pracovní plochy pomocí ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# a Visual Basic). V jazyce C++/CLI [najdete v tématu Nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo v případě C/C++ najdete v [tématu Nasazení nativní aplikace pomocí instalačního projektu](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publikování aplikací do Azure

- **ASP.NET**, **ASP.NET Core**, **Python**a **Node.js**: Publikování do služby Azure App Service nebo Azure App Service Linux (pomocí kontejnerů) pomocí jedné z následujících metod.

  - Pro průběžné (nebo automatizované) nasazení aplikací použijte Azure DevOps s [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - Pro jednorázové (nebo ruční) nasazení aplikací použijte nástroj **publikovat** v sadě Visual Studio.

  Pro nasazení, které poskytuje více přizpůsobené konfigurace serveru, můžete také použít nástroj **publikovat** k nasazení aplikací do virtuálního počítače Azure.

  Chcete-li použít nástroj **publikovat,** klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **Publikovat**. (Pokud jste dříve nakonfigurovali profily publikování, musíte klepnout na tlačítko **Vytvořit nový profil**.) V dialogovém okně Publikovat zvolte buď **službu App Service,** nebo **virtuální počítače Azure**a postupujte podle pokynů konfigurace.

  ![Zvolte službu Azure App Service](../deployment/media/quickstart-publish-azure.png "Zvolte službu Azure App Service")

  Počínaje Visual Studio 2017 verze 15.7, můžete nasadit ASP.NET základní aplikace do **app service pro Linux**.

  Pro aplikace pythonu najdete také v [tématu Python – publikování do služby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Rychlý úvod najdete v [tématech Publikování v Azure](quickstart-deploy-to-azure.md) a [Publikování na Linuxu](quickstart-deploy-to-linux.md). Taky najdete [v tématu Publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Nasazení pomocí Gitu najdete [v tématu Průběžné nasazení ASP.NET Core do Azure s Gitem](/aspnet/core/publishing/azure-continuous-deployment).

  Informace o importu profilu publikování z Azure App Service do Visual Studia najdete v [tématu Import nastavení publikování a nasazení do Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Pokud ještě nemáte účet Azure, můžete [se zaregistrovat zde](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publikovat na webu nebo nasadit do sdílené síťové složky

- **ASP.NET**, **ASP.NET Jádro**, **Node.js**a **Python**: Pomocí nástroje Publikovat můžete nasadit na web pomocí FTP nebo Nasazení webu. Další informace naleznete [v tématu Deploy to a weby](quickstart-deploy-to-a-web-site.md).

    V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a zvolte **Publikovat**. (Pokud jste dříve nakonfigurovali profily publikování, musíte klepnout na tlačítko **Vytvořit nový profil**.) V nástroji Publikovat zvolte požadovanou možnost a postupujte podle pokynů konfigurace.

    ![Zvolte IIS, FTP atd.](../deployment/media/quickstart-publish-iis-ftp.png)

    Informace o importu profilu publikování v sadě Visual Studio naleznete v [tématu Import nastavení publikování a nasazení do služby IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Můžete také nasadit ASP.NET aplikace a služby v mnoha dalšími způsoby. Další informace naleznete v [tématu Nasazení ASP.NET webových aplikací a služeb](/aspnet/mvc/overview/deployment/).

- **Plocha systému Windows** Desktopovou aplikaci systému Windows můžete publikovat na webovém serveru nebo ve sdílené síťové složce pomocí nasazení ClickOnce. Uživatelé pak mohou aplikaci nainstalovat jediným kliknutím. Další informace najdete [v tématu Nasazení aplikace klasické pracovní plochy pomocí ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# a Visual Basic). V jazyce C++/CLI [najdete v tématu Nasazení nativní aplikace pomocí ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) nebo v případě C/C++ najdete v [tématu Nasazení nativní aplikace pomocí instalačního projektu](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publikovat v Microsoft Storu

V sadě Visual Studio můžete vytvářet balíčky aplikací pro nasazení do Microsoft Storu.

- **UPW**: Aplikaci můžete zabalit a nasadit pomocí položek nabídky. Další informace naleznete [v tématu Balíček aplikace UPW pomocí sady Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Vytvoření balíčku aplikace](../deployment/media/feature-tour-create-app-package.jpg)

- **Plocha Windows**: Můžete nasadit do Microsoft Storu počínaje Visual Studio 2017 verze 15.4. Chcete-li to provést, začněte vytvořením projektu balení aplikací systému Windows. Další informace najdete [v tématu Balíček desktopové aplikace pro Microsoft Store](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

    ![Balení aplikace klasické pracovní plochy](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>Nasazení balíčků .NET do NuGet.org

Chcete-li nasadit svázaný kód do "balíčků", které obsahují kompilovaný kód (jako knihovny DLL) spolu s dalším obsahem potřebným v projektech, které tyto balíčky spotřebovávají, můžete pomocí sady Visual Studio vytvořit balíček NuGet a nástroj příkazu příkazu příkazu příkazu příkazu příkazu pro konečné nasazení.

- [Vytvoření a publikování balíčku .NET Standard](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Vytvoření a publikování balíčku rozhraní .NET Framework](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Nasazení do zařízení (UPW)

Pokud nasazujete aplikaci UPW pro testování na zařízení, přečtěte si téma [Spuštění aplikací UPW na vzdáleném počítači ve Visual Studiu](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Vytvoření instalačního balíčku (plocha systému Windows)

Pokud požadujete složitější instalaci desktopové aplikace, než může [clickonce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) poskytnout, můžete vytvořit balíček Instalační služby systému Windows (instalační soubor MSI nebo EXE) nebo vlastní zaváděcí nástroj.

- Instalační balíček založený na MSI lze vytvořit pomocí [rozšíření sady nástrojů WiX](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset). Toto je sada nástrojů příkazového řádku.

   ::: moniker range=">=vs-2019"
   Pro Visual Studio 2019 získáte [rozšíření Sady nástrojů WiX Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension).
   ::: moniker-end

- Instalační balíček MSI nebo EXE lze vytvořit pomocí [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) od Flexera Software. Program InstallShield lze použít s Visual Studio 2017 a novějšími verzemi (funkce Community Edition není podporována). Všimněte si, že InstallShield Limitovaná edice již není součástí sady Visual Studio a není podporována v sadě Visual Studio 2017 a novějších verzích. o budoucí dostupnosti se poraďte se [společností Flexera Software.](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio)

- Instalační balíček MSI nebo EXE lze vytvořit pomocí projektu instalace (vdproj). Chcete-li použít tuto možnost, nainstalujte [rozšíření Aplikace Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Můžete také nainstalovat nezbytné součásti pro desktopové aplikace konfigurací obecného instalačního programu, který se označuje jako zaváděcí nástroj. Další informace naleznete v [tématu Požadavky na nasazení aplikací](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Nasazení do testovací laboratoře

Můžete povolit složitější vývoj a testování nasazením aplikací do virtuálních prostředí. Další informace naleznete v [tématu Test v testovacím prostředí](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Průběžné nasazování

Azure Pipelines můžete použít k povolení průběžného nasazení vaší aplikace. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) a [Deploy to Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deploy-a-sql-database"></a>Nasazení databáze SQL

- [Změna cílové platformy a publikování databázového projektu (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Nasazení projektu služby Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Nasazení projektů a balíčků integračních služeb (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Sestavení a nasazení v místní databázi](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Nasazení pro jiné typy aplikací

| Typ aplikace | Scénář nasazení | Odkaz |
| --- | --- | --- |
| **Aplikace Office** | Doplněk pro Office můžete publikovat z Visual Studia. | [Nasazení a publikování doplňku Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Služba WCF nebo OData** | Jiné aplikace mohou používat služby WCF RIA, které nasadíte na webový server. | [Vývoj a nasazení datových služeb WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch už není podporován od Visual Studia 2017, ale pořád se dá nasadit z Visual Studia 2015 a staršího. | [Nasazení aplikací LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se rychle podívali na možnosti nasazení pro různé aplikace.

> [!div class="nextstepaction"]
> [Jaké možnosti publikování jsou pro mě to pravé?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
