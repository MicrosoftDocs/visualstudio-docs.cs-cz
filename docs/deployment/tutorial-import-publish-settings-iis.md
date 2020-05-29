---
title: Publikování v IIS pomocí importu nastavení publikování
description: Vytvoření a import profilu publikování pro nasazení aplikace ze sady Visual Studio do služby IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b18d1b123e32807575ac2c6601166891d6c25be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183298"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby IIS importem nastavení publikování v aplikaci Visual Studio

Pomocí nástroje **publikovat** můžete importovat nastavení publikování a pak aplikaci nasadit. V tomto článku používáme nastavení publikování pro službu IIS, ale podobný postup můžete použít k importu nastavení publikování pro [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). V některých scénářích může být použití profilu nastavení publikování rychlejší než ruční konfigurace nasazení služby IIS pro každou instalaci sady Visual Studio.

Tyto kroky platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v aplikaci Visual Studio.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Nakonfigurujte službu IIS tak, aby bylo možné vygenerovat soubor nastavení publikování.
> * Vytvoření souboru s nastavením publikování
> * Import souboru nastavení publikování do sady Visual Studio
> * Nasazení aplikace do služby IIS

Soubor nastavení publikování (* \* . publishsettings*) se liší od publikačního profilu (* \* . pubxml*) vytvořeného v aplikaci Visual Studio. Soubor nastavení publikování se vytvoří prostřednictvím služby IIS nebo Azure App Service, nebo se dá vytvořit ručně a pak ho můžete importovat do sady Visual Studio.

> [!NOTE]
> Pokud potřebujete kopírovat profil publikování sady Visual Studio ( \* soubor. pubxml) z jedné instalace sady Visual Studio na jiný, můžete najít profil publikování * \<profilename\> . pubxml*ve složce * \\<ProjectName \> \Properties\PublishProfiles* pro spravované typy projektů. Pro weby se podívejte do složky *\ App_Data* . Profily publikování jsou soubory XML MSBuild.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoje pro ASP.NET a web** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   a nainstalujte si ji zdarma.
::: moniker-end

::: moniker range="vs-2017"

* Musíte mít nainstalovanou aplikaci Visual Studio 2017 a úlohu **vývoje pro ASP.NET a web** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   a nainstalujte si ji zdarma.
::: moniker-end

* Na vašem serveru musí být spuštěný systém Windows Server 2012, Windows Server 2016 nebo Windows Server 2019 a musíte mít správně nainstalovanou [roli webový server služby IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (vyžaduje se pro vygenerování souboru nastavení publikování (* \* . publishsettings*)). Na serveru musí být nainstalován také ASP.NET 4,5 nebo ASP.NET Core. Pokud chcete nastavit ASP.NET 4,5, přečtěte si téma [IIS 8,0 s ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Pokud chcete nastavit ASP.NET Core, přečtěte si téma [hostitelská ASP.NET Core ve Windows se službou IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). V případě ASP.NET Core se ujistěte, že nakonfigurujete fond aplikací tak, aby nepoužíval **žádný spravovaný kód**, jak je popsáno v článku.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v aplikaci Visual Studio

1. V počítači se sadou Visual Studio vytvořte nový projekt.

    Vyberte správnou šablonu. V tomto příkladu zvolte buď **ASP.NET webová aplikace (.NET Framework)** , nebo (pouze pro C#) **ASP.NET Core webové aplikace**a klikněte na tlačítko **OK**.

    Pokud nevidíte zadané šablony projektu, klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Nainstalujte úlohu **vývoje ASP.NET a webu** .

    Šablona projektu, kterou zvolíte (ASP.NET nebo ASP.NET Core), musí odpovídat verzi ASP.NET nainstalované na webovém serveru.

1. Zvolte **MVC** (.NET Framework) nebo **Webová aplikace (Model-View-Controller)** (pro .NET Core) a ujistěte se, že není vybrané **žádné ověřování** , a pak klikněte na **OK**.

1. Zadejte název jako **MyWebApp** a klikněte na **OK**.

    Visual Studio vytvoří projekt.

1. Vyberte **sestavit sestavení**  >  **řešení** a sestavte projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalace a konfigurace Nasazení webu na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru s nastavením publikování ve službě IIS na Windows serveru

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v aplikaci Visual Studio a nasazení

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se nespustí ze sady Visual Studio, spusťte aplikaci ve službě IIS. Pro ASP.NET Core se musíte ujistit, že je pole fond aplikací pro **DefaultAppPool** nastavené na **žádný spravovaný kód**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili soubor nastavení publikování, importovali jste ho do sady Visual Studio a nasadili jste aplikaci ASP.NET do služby IIS. Můžete požadovat přehled dalších možností publikování v aplikaci Visual Studio.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
