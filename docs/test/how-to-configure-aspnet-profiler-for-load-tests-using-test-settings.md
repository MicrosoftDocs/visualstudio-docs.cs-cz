---
title: Konfigurace technologie ASP.NET Profiler pro zátěžové testy
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 197a6c4a743f5f30e060950413b7e2214fb91b36
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068419"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Postupy: Konfigurace služby ASP.NET profiler pro zátěžové testy pomocí nastavení testu v sadě Visual Studio

Můžete použít adaptér diagnostiky dat profiler technologie ASP.NET ke shromažďování informací nástroje profilování technologie ASP.NET. Tento adaptér diagnostických dat shromažďuje údaje o výkonu pro aplikace ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Tento adaptér diagnostických dat nelze použít pro testy, které jsou spouštěny pomocí nástroje Microsoft Test Manager. Můžete použít diagnostický adaptér Profiler technologie ASP.NET se zátěžovými testy pomocí webů, což vyžaduje Visual Studio Enterprise.

Adaptér diagnostiky dat profiler technologie ASP.NET umožňuje shromažďovat data profiler technologie ASP.NET z aplikační vrstvy, při spuštění zátěžového testu. Profiler by neměl být spouštěn pro dlouho trvající testy, například pro zátěžové testy, které trvají déle než jednu hodinu. Důvodem je, že soubor profileru může dosáhnout velikosti až stovek megabajtů. Spusťte místo toho kratší zátěžové testy s použitím profiler technologie ASP.NET, které získáte výhodu hloubkové diagnostiky problémů s výkonem.

> [!NOTE]
> Adaptér diagnostiky dat profiler technologie ASP.NET profiluje proces Internetové informační služby (IIS). Proto nebude fungovat proti vývojovému webovému serveru. Chcete-li Profilovat webu v zátěžovém testu, budete muset nainstalovat testovacího agenta na počítači, na kterém běží služby IIS. Testovací agent nebude generovat zátěž, ale bude to agent pouze pro sběr. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

Další informace najdete v tématu [postupy: vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfigurace profileru technologie ASP.NET pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testů ze sady Visual Studio a vyberte **dat a diagnostiky** stránky.

1.  Vyberte roli pro shromažďování dat profiler technologie ASP.NET.

    > [!WARNING]
    > Tato role musí být webový server.

2.  Vyberte **Profiler technologie ASP.NET** Povolit shromažďování dat profilování ASP.NET, a klikněte na tlačítko **konfigurovat**.

     Zobrazí se dialogové okno Konfigurace shromažďování dat profilování ASP.NET.

3.  V **vzorkovací frekvence Profiler**, zadejte hodnotu, která označuje, kolik procesoru nepřerušených hodinových cyklů čekat mezi pořizováním vzorků profilování technologie ASP.NET.

4.  Chcete-li povolit profilaci interakce vrstev, vyberte **povolit profilaci interakce vrstev**.

     Profilování interakce vrstev počítá počet požadavků, které se odesílají do webového serveru pro každý artefakt (například *MyPage.aspx* nebo *CompanyLogo.gif*) a dobu obsloužení jednotlivých požadavků. Profilování interakce vrstev dále shromažďuje informace o tom, která připojení ADO.NET byla použita jako součást požadavku na stránku a kolik dotazů a volání uložené procedury bylo provedeno jako součást řešení této žádosti.

     Jsou shromažďovány dvě různé sady informací o časování:

    -   Informace o časování (minimum, maximum, průměr a součet) pro obsluhu každého webového požadavku.

    -   Informace o časování (minimum, maximum, průměr a součet) spuštění každého dotazu.

Pomocí technologie ASP.NET profiler diagnostických dat adaptéru nakonfigurované v nastavení testu lze shromažďovat data ve webové aplikaci ASP.NET profilování technologie ASP.NET.

## <a name="see-also"></a>Viz také:

- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
- [Postupy: vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)