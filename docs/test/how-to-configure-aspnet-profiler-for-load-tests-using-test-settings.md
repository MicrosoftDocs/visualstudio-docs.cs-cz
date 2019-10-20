---
title: Konfigurace profileru ASP.NET pro zátěžové testy
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de7e890c60374730e297296116cb56828fa256b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643760"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Postupy: Konfigurace profileru ASP.NET pro zátěžové testy pomocí nastavení testu v aplikaci Visual Studio

Adaptér diagnostiky dat profileru ASP.NET můžete použít ke shromažďování informací o profileru ASP.NET. Tento adaptér diagnostických dat shromažďuje údaje o výkonu pro aplikace ASP.NET.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Tento adaptér diagnostických dat nelze použít pro testy, které jsou spouštěny pomocí Microsoft Test Manager. Můžete použít diagnostický adaptér ASP.NET Profiler s testy zatížení pouze pomocí webů, které vyžadují Visual Studio Enterprise.

Adaptér diagnostiky dat profileru ASP.NET umožňuje shromažďovat data profileru ASP.NET z aplikační vrstvy při spuštění zátěžového testu. Profiler by neměl být spouštěn pro dlouho trvající testy, například pro zátěžové testy, které trvají déle než jednu hodinu. Důvodem je, že soubor profileru může dosáhnout velikosti až stovek megabajtů. Místo toho spouštějte kratší zátěžové testy pomocí profileru ASP.NET, který vám pořád poskytne výhody hloubkové diagnostiky problémů s výkonem.

> [!NOTE]
> Adaptér diagnostiky dat profileru ASP.NET profiluje proces Internetová informační služba (IIS). Proto nebude fungovat na vývojovém webovém serveru. Chcete-li profilovat web v rámci zátěžového testu, je nutné nainstalovat testovacího agenta na počítači, na kterém je služba IIS spuštěna. Testovací agent nebude generovat zátěž, ale bude to agent pouze pro sběr. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

Další informace naleznete v tématu [Postupy: Vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Konfigurace profileru ASP.NET pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testu ze sady Visual Studio a vybrat stránku **data a diagnostika** .

1. Vyberte roli, která se má použít ke shromáždění dat profileru ASP.NET.

    > [!WARNING]
    > Tato role musí být webovým serverem.

2. Vyberte **ASP.NET Profiler** pro povolení shromažďování dat profilování ASP.NET a pak zvolte **Konfigurovat**.

     Zobrazí se dialogové okno pro konfiguraci shromažďování dat profilování ASP.NET.

3. Do **číselníku interval vzorkování profileru**zadejte hodnotu, která indikuje počet nezastavených cyklů hodin procesoru, které se mají čekat mezi pořizováním ukázek ASP.NET profilace.

4. Chcete-li povolit profilaci interakce vrstev, vyberte možnost **Povolit Profilování interakce vrstev**.

     Profilace interakce vrstev počítá počet požadavků, které jsou odeslány na webový server pro každý artefakt (například *MyPage. aspx* nebo *CompanyLogo. gif*), a dobu, kterou trvalo obsluhu jednotlivých požadavků. Profilování interakce vrstev dále shromažďuje informace o tom, která připojení ADO.NET byla použita jako součást požadavku na stránku a kolik dotazů a volání uložené procedury bylo provedeno jako součást řešení této žádosti.

     Jsou shromažďovány dvě různé sady informací o časování:

    - Informace o časování (minimum, maximum, průměr a součet) pro obsluhu každého webového požadavku.

    - Informace o časování (minimum, maximum, průměr a součet) spuštění každého dotazu.

Pomocí adaptéru diagnostických dat profileru ASP.NET, který je nakonfigurovaný v nastavení testu, teď můžete shromažďovat data ASP.NET profilování ve vaší webové aplikaci ASP.NET.

## <a name="see-also"></a>Viz také:

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Postupy: Vytvoření nastavení testu pro distribuovaný zátěžový test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)