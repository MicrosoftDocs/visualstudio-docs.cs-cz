---
title: Ladění živého přenosu ASP.NET čase na virtuálním počítači Azure
description: Zjistěte, jak zaznamenávat a přehrávat živé ASP.NET na virtuálních počítačích Azure pomocí Snapshot Debugger.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798450"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Záznam a přehrávání živých ASP.NET na virtuálních počítačích Azure pomocí Snapshot Debugger

Ladění cesty v čase (TTD) ve verzi Preview v Visual Studio Enterprise umožňuje zaznamenat webovou aplikaci běžící na virtuálním počítači Azure a pak přesně rekonstruovat a přehrát cestu provádění. TTD se integruje s Snapshot Debugger a umožňuje přetáhnou a přehrát každý řádek kódu libovolným počtem opakování, což vám pomůže izolovat a identifikovat problémy, ke kterým může dojít pouze v produkčních prostředích.

Zachycení záznamu TTD aplikaci zastaví. Záznam TDD ale výrazně zvyšuje režijní náklady na běžící proces a zpomaluje ho na základě faktorů, které zahrnují velikost procesu a počet aktivních vláken.

Tato funkce je ve verzi Preview pro verzi Visual Studio 2019 s licencí Go Live.

V tomto kurzu:

> [!div class="checklist"]
> * Spuštění aplikace Snapshot Debugger s povoleným laděním cesty v čase
> * Nastavení snappointu a shromáždění záznamu cesty v čase
> * Spuštění ladění záznamu cesty v čase

## <a name="prerequisites"></a>Požadavky

* Ladění cesty v čase pro Azure Virtual Machines (VM) je k dispozici pouze pro Visual Studio 2019 Enterprise nebo vyšší s úlohou **Vývoj pro Azure.** (Na kartě **Jednotlivé komponenty** ji najdete v části Ladění **a testování.**  >  **Ladicí program snímků**.)

    Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/vs/)

* Ladění cesty v čase je k dispozici pro následující webové aplikace virtuálních počítače Azure:
  * ASP.NET aplikace (AMD64) běžící na .NET Framework 4.8 nebo novějším.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Spuštění aplikace Snapshot Debugger s povoleným laděním cesty v čase

1. Otevřete projekt, pro který chcete shromáždit záznam cesty v čase.

    > [!IMPORTANT]
    > Pokud chcete spustit TTD,  musíte otevřít stejnou verzi zdrojového kódu, která je publikovaná ve službě virtuálního počítače Azure.

1. Zvolit **ladění > připojit Snapshot Debugger...**. Vyberte virtuální počítač Azure, ve kterém je webová aplikace nasazená, a účet úložiště Azure. Vyberte možnost **Povolit náhled času cestovního ladění** a pak klikněte na **připojit**.

      ![Vybrat prostředek Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Při prvním výběru **připojit Snapshot Debugger** pro váš virtuální počítač se služba IIS automaticky restartuje.

    Metadata pro **moduly** nejsou zpočátku aktivována. Přejděte do webové aplikace a klikněte na tlačítko **Spustit shromažďování** a pak se aktivuje. Visual Studio je teď v režimu ladění snímků.

   ![Režim ladění snímků](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Rozšíření Application Insights lokality také podporuje ladění snímků. Pokud narazíte na chybovou zprávu "rozšíření webu je zastaralé", přečtěte si téma [tipy pro řešení potíží a známé problémy ladění snímků](../debugger/debug-live-azure-apps-troubleshooting.md) pro upgrade podrobností.

   V okně **moduly** se zobrazí, když se načtou všechny moduly pro virtuální počítač Azure (pro otevření tohoto okna vyberte **> moduly pro ladění > Windows** ).

   ![Kontrolovat okno modulů](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Nastavení snímkovací bod a shromáždění časového cestovního záznamu

1. V editoru kódu klikněte na levé hřbety v metodě, kterou vás zajímá, abyste nastavili snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

   ![Nastavení snímkovací bod](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Klikněte pravým tlačítkem myši na ikonu snímkovací bod (prázdná koule) a vyberte **Akce**. V okně **nastavení snímku** zaškrtněte políčko **Akce** . Potom zaškrtněte políčko **shromáždit čas cestovního trasování na konci této metody** .

   ![Shromáždit trasování času na konci metody](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Kliknutím **na Spustit** kolekci zapněte modul snappoint.

   ![Zapnutí bodu snappoint](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Pořízení snímku

Když je modul snappoint zapnutý, zachytí snímek vždy, když se spustí řádek kódu, na kterém je umístěný. Toto spuštění může být způsobeno skutečným požadavkem na vašem serveru. Pokud chcete vynutit, aby se váš bod snappointu dostal, přejděte do zobrazení prohlížeče vašeho webu a udělejte všechny požadované akce, které způsobí, že se váš snappoint využije.

## <a name="start-debugging-a-time-travel-recording"></a>Spuštění ladění záznamu cesty v čase

1. Po spuštění snímku se v okně snímku Diagnostické nástroje snímku. Pokud chcete toto okno otevřít, zvolte **Ladit > Windows > Zobrazit Diagnostické nástroje**.

   ![Otevření bodu snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Kliknutím na odkaz View Snapshot (Zobrazit snímek) otevřete záznam cesty v editoru kódu.
  
   Každý řádek kódu zaznamenaný pomocí TTD můžete spustit pomocí tlačítek **Continue (Pokračovat)** a **Reverse Continue (Pokračovat).** Kromě toho **lze pomocí** panelu nástrojů Ladění zobrazit další příkaz **,** krokovat s krokem do **,** krokovat přes **,** krokovat **ven,** **krokovat** zpět do **,** krokovat zpět přes , krok zpět **ven**.

   ![Spuštění ladění](../debugger/media/time-travel-debugging-step-commands.png)

   Můžete také použít okna **Místní hodnoty** **,** Sleduje a Zásobník **volání** a také vyhodnotit výrazy.

   ![Kontrola dat snímků](../debugger/media/time-travel-debugging-start-debugging.png)

    Samotný web je stále aktivní a koncoví uživatelé nejsou ovlivněni žádnou další aktivitou TTD. Ve výchozím nastavení se pro každý bod snímku zachytá jenom jeden snímek: po zachycení snímku se modul snappoint vypne. Pokud chcete na snímku snímku zapnout další snímek, můžete ho znovu zapnout kliknutím na **Aktualizovat kolekci.**

**Potřebujete pomoc?** Podívejte se na [stránky Řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a Nejčastější dotazy k [ladění](../debugger/debug-live-azure-apps-faq.yml) snímků.

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného bodu snappointu

Pokud je obtížné znovu vytvořit konkrétní stav ve vaší aplikaci, zvažte, zda může pomáhat použití podmíněného snímkovací bod. Podmíněné snímkovací body vám pomůžou se vyhnout shromažďování času na nahrávání, dokud aplikace nevstoupí do požadovaného stavu, například když má proměnná určitou konkrétní hodnotu, kterou chcete zkontrolovat. [Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu volání](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak shromáždit Virtual Machines pro službu Azure na více časových cestách. Možná budete chtít přečíst si další podrobnosti o Snapshot Debugger.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.yml)