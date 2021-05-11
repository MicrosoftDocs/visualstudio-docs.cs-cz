---
title: Publikování do služby IIS importem nastavení publikování
description: Vytvoření a import profilu publikování pro nasazení aplikace z Visual Studio do služby IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aeaaff68ab0abe85838456e8c8b69e2520295689
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729270"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby IIS importem nastavení publikování v Visual Studio

K importu **nastavení publikování** a nasazení aplikace můžete použít nástroj Publikovat. V tomto článku používáme nastavení publikování pro službu IIS, ale podobným postupem můžete importovat nastavení publikování pro [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). V některých scénářích může být použití profilu nastavení publikování rychlejší než ruční konfigurace nasazení do služby IIS pro každou instalaci Visual Studio.

Tyto kroky platí pro ASP.NET, ASP.NET Core a .NET Core v Visual Studio.

V tomto kurzu:

> [!div class="checklist"]
> * Nakonfigurujte službu IIS tak, abyste mohli vygenerovat soubor nastavení publikování.
> * Vytvoření souboru nastavení publikování
> * Import souboru nastavení publikování do Visual Studio
> * Nasazení aplikace do služby IIS

Soubor nastavení publikování (*\* .publishsettings*) se liší od profilu publikování (*\* .pubxml*) vytvořeného v Visual Studio. Soubor nastavení publikování je vytvořen službou IIS nebo Azure App Service, nebo je možné ho vytvořit ručně a pak ho můžete importovat do Visual Studio.

> [!NOTE]
> Pokud potřebujete zkopírovat profil publikování Visual Studio ( soubor .pubxml) z jedné instalace Visual Studio do jiné, najdete profil publikování \* *\<profilename\> .pubxml* ve složce *\\<název_projektu \> \Properties\PublishProfiles* pro spravované typy projektů. Weby vyhledejte ve *složce \App_Data.* Profily publikování jsou soubory XML nástroje MSBuild.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* Musíte mít nainstalovanou Visual Studio 2019 a úlohu **vývoje ASP.NET a** webu.

    Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.
::: moniker-end

::: moniker range="vs-2017"

* Musíte mít nainstalovanou Visual Studio 2017 a úlohu **vývoje ASP.NET a** webu.

    Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ho zdarma.
::: moniker-end

* Na vašem serveru musí být spuštěný systém Windows Server 2012, Windows Server 2016 nebo Windows Server 2019 a musíte mít správně nainstalovanou [roli webový server služby IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (vyžaduje se pro vygenerování souboru nastavení publikování (*\* . publishsettings*)). Na serveru musí být nainstalován také ASP.NET 4,5 nebo ASP.NET Core. Pokud chcete nastavit ASP.NET 4,5, přečtěte si téma [IIS 8,0 s ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Pokud chcete nastavit ASP.NET Core, přečtěte si téma [hostitelská ASP.NET Core ve Windows se službou IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). V případě ASP.NET Core se ujistěte, že nakonfigurujete fond aplikací tak, aby nepoužíval **žádný spravovaný kód**, jak je popsáno v článku.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v aplikaci Visual Studio

1. V počítači se sadou Visual Studio vytvořte nový projekt.

    Vyberte správnou šablonu. V tomto příkladu zvolte buď **ASP.NET webová aplikace (.NET Framework)** , nebo (pouze pro C#) **ASP.NET Core webové aplikace** a pak vyberte **OK**.

    Pokud se zadané šablony projektu nezobrazuje, přejděte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Nainstalujte úlohu **vývoje ASP.NET a webu** .

    Šablona projektu, kterou zvolíte (ASP.NET nebo ASP.NET Core), musí odpovídat verzi ASP.NET nainstalované na webovém serveru.

1. Zvolte **MVC** (.NET Framework) nebo **Webová aplikace (Model-View-Controller)** (pro .NET Core) a ujistěte se, že není vybrané **žádné ověřování** , a pak vyberte **OK**.

1. Zadejte název jako **MyWebApp** a vyberte **OK**.

    Visual Studio vytvoří projekt.

1. Zvolte **sestavit sestavení**  >  **řešení** (nebo stiskněte **CTRL**  +  **+ SHIFT**  +  **B**) a sestavte projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalace a konfigurace Nasazení webu na Windows serveru

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru s nastavením publikování ve službě IIS na Windows serveru

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v aplikaci Visual Studio a nasazení

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud se nespustí z Visual Studio, spusťte aplikaci ve službě IIS. Pro ASP.NET Core je potřeba se ujistit, že pole Fond aplikací pro **DefaultAppPool** je nastavené na **Žádný spravovaný kód.**

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili soubor nastavení publikování, naimportoval ho do Visual Studio a nasadili jste aplikaci ASP.NET iis. Můžete chtít přehled o dalších možnostech publikování v Visual Studio.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
