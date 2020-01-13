---
title: Oprávnění pro uživatele | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918998"
---
# <a name="user-permissions-and-visual-studio"></a>Uživatelská oprávnění a sada Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z důvodu bezpečnosti by měl být systém Visual Studio spuštěn s normálním uživatelským přístupem, kdykoli je to možné.

> [!WARNING]
> Je třeba zajistit, aby nebylo kompilováno, spouštěno nebo laděno jakékoli řešení systému Visual Studio, které nebylo získáno od důvěryhodné osoby nebo z důvěryhodného zdroje.

 V režimu normálního uživatele lze v integrovaném vývojovém prostředí IDE aplikace Visual Studio provádět téměř cokoli, ale pro provedení následujících úkolů je potřeba mít administrátorská oprávnění:

|Plošný|Úloha|Další informace|
|----------|----------|--------------------------|
|Instalace služby|Instalace sady Visual Studio|[Instalaci sady Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Upgrade ze zkušební edice sady Visual Studio|[Postupy: Upgrade ze zkušební edice sady Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalace, aktualizace nebo odebrání obsahu místní nápovědy|[Instalace a správa místního obsahu](../ide/install-and-manage-local-content.md)|
|Typy aplikací|Vývoj řešení pro SharePoint 2010|[Požadavky na vývoj řešení služby SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Získání vývojářské licence pro [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Získejte licenci vývojáře (aplikace pro Windows Store)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Sada nástrojů|Přidání klasického modelu COM ovládacích prvků do **nástrojů**.|[Používání sady nástrojů](../ide/using-the-toolbox.md)|
|Doplňky|Instalace a používání doplňků, které byly vytvořeny pomocí klasického modelu COM v rozhraní IDE|[Vytváření doplňků a průvodců](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Sestavování|Použití událostí po sestavení, které registrují komponentu|[Seznámení s kroky vlastního sestavení a s událostmi sestavení](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Zahrnutí registračního kroku do sestavování projektů v jazyce C++|[Seznámení s kroky vlastního sestavení a s událostmi sestavení](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Ladění|Ladění aplikací spouštěných se zvýšenými oprávněními|[Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)|
||Ladění aplikací, které běží pod jiným uživatelským účtem, jako jsou weby ASP.NET|[Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Ladění v zóně pro aplikace prohlížeče XAML (XBAP)|[Hostitel WPF (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Použití emulátoru k ladění projektů cloudových služeb pro Microsoft Azure.|[Ladění cloudové služby v sadě Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Konfigurace brány firewall pro vzdálené ladění|[Nastavení nástroje Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Nástroje pro měření výkonu|Profilace aplikace|[Průvodce začátečníka profilací výkonu](../profiling/beginners-guide-to-performance-profiling.md)|
|Nasazení|Nasazení webové aplikace do Internetové informační služby (IIS) v místním počítači|[Nasazení webové aplikace ASP.NET u poskytovatele hostingu pomocí sady Visual Studio nebo Visual Web Developer: nasazení do služby IIS jako testovacího prostředí](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Poskytování zpětné vazby společnosti Microsoft|Změna způsobu účasti v programu Visual Studio Customer Experience Program|[Postupy: odeslání názoru](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Spuštění sady Visual Studio jako správce
 Sadu Visual Studio můžete spustit s oprávněními správce při každém spuštění rozhraní IDE nebo můžete upravit zástupce sady tak, aby se vždy spustila s oprávněními správce. Další informace naleznete v nápovědě pro Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Spuštění sady Visual Studio s oprávněními správce [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)], nebo [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. Na **Start** zadejte **sady Visual Studio**. Měli byste vidět verzi nebo verze systému Visual Studio, které jste nainstalovali.

2. Vyberte verzi systému Visual Studio, kterou chcete spustit, a následně vyvolejte místní nabídku (zobrazí se v dolní části obrazovky). Zvolte **spustit jako správce**.

     Při spuštění sady Visual Studio **(správce)** se zobrazí za názvem produktu v záhlaví programu.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>Spuštění sady Visual Studio s oprávněními správce [!INCLUDE[win7](../includes/win7-md.md)] nebo [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. Na **Start** nabídce zvolte **všechny programy**.

2. V **sady Microsoft Visual Studio** *verze* vyberte složku **sady Visual Studio** *verze* otevřete místní nabídku a zvolte  **Spustit jako správce**.

     Při spuštění sady Visual Studio **(správce)** se zobrazí za názvem produktu v záhlaví programu.

## <a name="see-also"></a>Viz také
 [Přenosy, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [instalaci sady Visual Studio 2015](../install/install-visual-studio-2015.md)
