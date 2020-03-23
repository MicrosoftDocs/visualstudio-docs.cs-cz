---
title: Publikovat do služby IIS importem nastavení publikování
description: Vytvoření a import profilu publikování pro nasazení aplikace z aplikace Visual Studio do služby IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e0c7309f52fbc8056f09e5a59afcfdefaa8d0bf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "65680140"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikování aplikace do služby IIS importem nastavení publikování v sadě Visual Studio

Pomocí nástroje **Publikovat** můžete importovat nastavení publikování a pak aplikaci nasadit. V tomto článku používáme nastavení publikování pro službu IIS, ale můžete použít podobné kroky k importu nastavení publikování pro [službu Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). V některých případech může být použití profilu nastavení publikování rychlejší než ruční konfigurace nasazení do služby IIS pro každou instalaci sady Visual Studio.

Tyto kroky platí pro aplikace ASP.NET, ASP.NET Core a .NET Core v sadě Visual Studio.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Konfigurace služby IIS tak, aby bylo možné vygenerovat soubor nastavení publikování
> * Vytvoření souboru nastavení publikování
> * Import souboru nastavení publikování do sady Visual Studio
> * Nasazení aplikace do služby IIS

Soubor nastavení publikování (*\*.publishsettings*) se liší od profilu publikování (*\*.pubxml*) vytvořeného v sadě Visual Studio. Soubor nastavení publikování je vytvořen službou IIS nebo službou Azure App Service nebo jej lze vytvořit ručně a pak jej importovat do sady Visual Studio.

> [!NOTE]
> Pokud potřebujete pouze zkopírovat profil publikování\*sady Visual Studio (soubor PubXML) z jedné instalace sady Visual Studio do jiné, najdete profil publikování, * \<název\>profilu .pubxml*, ve složce * \\<název\>projektu \Properties\PublishProfiles* pro spravované typy projektů. Weby nahlédnou do složky *\App_Data.* Profily publikování jsou soubory XML MSBuild.

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* Musíte mít nainstalovanou Visual Studio 2019 a **ASP.NET a zatížení vývoje webu.**

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.
::: moniker-end

::: moniker range="vs-2017"

* Musíte mít nainstalovanou Visual Studio 2017 a **úlohy ASP.NET a vývoj webových** aplikací.

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.
::: moniker-end

* Na serveru musíte mít spuštěn systém Windows Server 2012 nebo Windows Server 2016 a musíte mít správně [nainstalovanou roli webového serveru služby IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (nutné ke generování souboru nastavení publikování (*\*.publishsettings*)). Na serveru musí být nainstalována také ASP.NET 4.5 nebo ASP.NET Core. Chcete-li nastavit ASP.NET 4.5, přečtěte si informace [o použití ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Informace o nastavení ASP.NET jádra naleznete v [tématu Hostitel ASP.NET jádra ve službě Windows se službou IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Vytvoření nového projektu ASP.NET v sadě Visual Studio

1. V počítači se systémem Visual Studio vytvořte nový projekt.

    Zvolte správnou šablonu. V tomto příkladu zvolte **buď ASP.NET webovou aplikaci (.NET Framework)** nebo (pouze pro C#) **ASP.NET základní webovou aplikaci**a klepněte na tlačítko **OK**.

    Pokud zadané šablony projektu nevidíte, klikněte v levém podokně dialogového okna **Nový projekt** na odkaz Otevřít instalační program sady Visual **Studio.** Spustí se instalační program pro Visual Studio. Nainstalujte **úlohu ASP.NET a vývoje webu.**

    Šablona projektu, kterou zvolíte (ASP.NET nebo ASP.NET core), musí odpovídat verzi ASP.NET nainstalované na webovém serveru.

1. Zvolte **buď MVC** (.NET Framework) nebo **webovou aplikaci (Model-View-Controller)** (pro .NET Core), a ujistěte se, že je **vybráno žádné ověřování,** a klepněte na tlačítko **OK**.

1. Zadejte název jako **MyWebApp** a klepněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

1. Zvolte **sestavení** > **sestavení řešení** k sestavení projektu.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalace a konfigurace nasazení webu v systému Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Vytvoření souboru nastavení publikování ve službě IIS v systému Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Import nastavení publikování v Sadě Visual Studio a nasazení

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po úspěšném nasazení aplikace by se měla spustit automaticky. Pokud nespustí z Visual Studia, spusťte aplikaci ve správě IIS. Pro ASP.NET jádra, musíte se ujistit, že pole fondu aplikací pro **DefaultAppPool** je nastavena na **žádný spravovaný kód**.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili soubor nastavení publikování, importovali ho do sady Visual Studio a nasadili ASP.NET aplikaci do služby IIS. Můžete chtít přehled dalších možností publikování v sadě Visual Studio.

> [!div class="nextstepaction"]
> [První seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md)
