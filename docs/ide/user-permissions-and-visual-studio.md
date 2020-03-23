---
title: Spustit jako správce
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927031b4755644aeac553367a4f8a08faa0c0992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75718633"
---
# <a name="user-permissions-and-visual-studio"></a>Uživatelská oprávnění a Visual Studio

Z důvodu zabezpečení byste měli spustit visual studio jako typický uživatel, kdykoli je to možné.

> [!WARNING]
> Je třeba zajistit, aby nebylo kompilováno, spouštěno nebo laděno jakékoli řešení systému Visual Studio, které nebylo získáno od důvěryhodné osoby nebo z důvěryhodného zdroje.

V rozhraní IDE sady Visual Studio můžete jako typický uživatel provést téměř vše. K dokončení následujících úloh potřebujete oprávnění správce:

|Oblast|Úkol|Další informace|
|----------|----------| - |
|Instalace|Instalace nebo úprava sady Visual Studio.|[Instalace sady Visual Studio](../install/install-visual-studio.md), [úprava sady Visual Studio](../install/modify-visual-studio.md)|
||Nainstalujte, aktualizujte nebo odeberte obsah místní nápovědy.|[Instalace a správa obsahu místní nápovědy](../help-viewer/install-manage-local-content.md)|
|Sada nástrojů|Přidejte do **panelu nástrojů**klasické ovládací prvky COM .|[Sada nástrojů](../ide/reference/toolbox.md)|
|Sestavování|Použijte události po sestavení, které registrují komponentu.|[Principy kroků vlastního sestavení a vytváření událostí](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Při vytváření projektů jazyka C++ zahrňte krok registrace.||
|ladění|Ladění aplikací, které běží se zvýšenými oprávněními.|[Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)|
||Ladění aplikací, které běží pod jiným uživatelským účtem, například ASP.NET weby.|[Ladění aplikací ASP.NET a AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Ladění v zóně pro aplikace prohlížeče XAML (XBAP).|[Hostitel WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Pomocí emulátoru můžete ladit projekty cloudových služeb pro Microsoft Azure.|[Ladění cloudové služby v sadě Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Nakonfigurujte bránu firewall pro vzdálené ladění.|[Vzdálené ladění](../debugger/remote-debugging.md)|
|Nástroje pro měření výkonu|Připojení ke zvýšené aplikaci.|[Průvodce profilováním výkonu pro začátečníky](../profiling/beginners-guide-to-performance-profiling.md)|
||Použijte profiler GPU.|[Profilování GPU](../profiling/gpu-usage.md)|
|Nasazení|Nasazení webové aplikace do Internetové informační služby (IIS) v místním počítači.|[Nasazení webové aplikace ASP.NET pomocí Visual Studia](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Spuštění sady Visual Studio jako správce

Pokud potřebujete spustit Visual Studio jako správce, otevřete rozhraní IDE následujícím postupem:

> [!NOTE]
> Tyto pokyny jsou pro Windows 10. Jsou podobné pro jiné verze systému Windows.

::: moniker range="vs-2017"

1. Otevřete nabídku **Start** a přejděte na Visual Studio 2017.

1. V nabídce Visual Studia **2017**nebo v místní nabídce vyberte **Další** > **spuštění jako správce**.

   Při spuštění sady Visual Studio se **(Správce)** zobrazí za názvem produktu v záhlaví.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete nabídku **Start** a přejděte do Visual Studia 2019.

1. V nabídce Visual Studia **2019**nebo v místní nabídce vyberte **Další** > **spuštění jako správce**.

   Při spuštění sady Visual Studio se **(Správce)** zobrazí za názvem produktu v záhlaví.

::: moniker-end

Zástupce aplikace můžete také upravit tak, aby byl vždy spuštěn s oprávněními správce.

## <a name="see-also"></a>Viz také

- [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Instalace sady Visual Studio](../install/install-visual-studio.md)
