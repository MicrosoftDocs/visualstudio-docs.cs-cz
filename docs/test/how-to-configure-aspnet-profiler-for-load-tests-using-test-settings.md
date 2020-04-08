---
title: Konfigurace ASP.NET profileru pro zátěžové testy
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07df32104394dffcd61d1561309b77e61593f6e6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880231"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Postup: Konfigurace ASP.NET profileru pro zátěžové testy pomocí nastavení testu v sadě Visual Studio

Pomocí adaptéru diagnostických dat ASP.NET profileru můžete shromažďovat informace ASP.NET profileru. Tento adaptér diagnostických dat shromažďuje údaje o výkonu pro ASP.NET aplikace.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Tento adaptér diagnostických dat nelze použít pro testy, které jsou spuštěny pomocí Správce testů společnosti Microsoft (zastaralé v sadě Visual Studio 2017). Diagnostický adaptér ASP.NET Profiler můžete použít s zátěžovými testy pouze pomocí webů, což vyžaduje Visual Studio Enterprise.

Adaptér diagnostických dat ASP.NET profileru umožňuje shromažďovat data ASP.NET profileru z aplikační vrstvy při spuštění zátěžového testu. Profiler by neměl být spouštěn pro dlouho trvající testy, například pro zátěžové testy, které trvají déle než jednu hodinu. Důvodem je, že soubor profileru může dosáhnout velikosti až stovek megabajtů. Místo toho spusťte kratší zátěžové testy pomocí ASP.NET profileru, který vám stále poskytne výhodu hluboké diagnostiky problémů s výkonem.

> [!NOTE]
> Adaptér diagnostických dat ASP.NET profileru profiluje proces Internetové informační služby (IIS). Proto nebude fungovat proti vývojový webový server. Chcete-li profilovat web v zátěžovém testu, je nutné nainstalovat testovacího agenta do počítače, na kterém je služba IIS spuštěna. Testovací agent nebude generovat zátěž, ale bude to agent pouze pro sběr. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

Další informace naleznete v [tématu Postup: Vytvoření testovacího nastavení pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfigurace ASP.NET profileru pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testu z aplikace Visual Studio a vybrat stránku **Data a diagnostika.**

1. Vyberte roli, která se má použít ke shromažďování dat ASP.NET profileru.

    > [!WARNING]
    > Tato role musí být webový server.

2. Výběrem **ASP.NET profileru** povolíte shromažďování dat profilování ASP.NET a pak zvolte **Konfigurovat**.

     Zobrazí se dialogové okno pro konfiguraci ASP.NET shromažďování dat profilování.

3. Do **intervalu vzorkování profileru**zadejte hodnotu, která označuje, kolik nezastavených cyklů hodin procesoru má čekat mezi odběrem vzorků ASP.NET profilování.

4. Chcete-li povolit profilování interakce vrstvy, vyberte **povolit profilování interakce vrstvy**.

     Profilování interakce úrovně počítá počet požadavků, které jsou odeslány na webový server pro každý artefakt (například *MyPage.aspx* nebo *CompanyLogo.gif)* a čas, který trval na servis každého požadavku. Profilování interakce vrstev dále shromažďuje informace o tom, která připojení ADO.NET byla použita jako součást požadavku na stránku a kolik dotazů a volání uložené procedury bylo provedeno jako součást řešení této žádosti.

     Jsou shromažďovány dvě různé sady informací o časování:

    - Informace o časování (minimum, maximum, průměr a součet) pro obsluhu každého webového požadavku.

    - Informace o časování (minimum, maximum, průměr a součet) spuštění každého dotazu.

Díky adaptéru diagnostických dat ASP.NET profileru nakonfigurovanému v nastavení testu můžete nyní shromažďovat data ASP.NET profilování ve vaší webové aplikaci ASP.NET.

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Postup: Vytvoření testovacího nastavení pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)