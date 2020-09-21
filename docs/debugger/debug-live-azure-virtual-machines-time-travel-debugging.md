---
title: Doba, po kterou se na virtuálním počítači Azure naladí Live ASP.NET
description: Naučte se, jak nahrávat a přehrávat živé aplikace ASP.NET na virtuálních počítačích Azure pomocí Snapshot Debugger.
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
ms.openlocfilehash: eb0db0bab5295925f71a81645e64fdeb5f2077df
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809567"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Nahrávání a přehrávání živých aplikací ASP.NET na virtuálních počítačích Azure pomocí Snapshot Debugger

Verze Preview TTD (Time cestovné) v Visual Studio Enterprise poskytuje možnost nahrávat webovou aplikaci běžící na virtuálním počítači Azure a pak přesně rekonstruovat a přehrát cestu spuštění. TTD se integruje s Snapshot Debugger a umožňuje vám převinout a znovu přehrát jednotlivé řádky kódu, které potřebujete, a pomáhá izolovat a identifikovat problémy, které se můžou vyskytovat jenom v produkčních prostředích.

Při zachytávání záznamu TTD se aplikace neukončí. Záznam TDD však přináší významnou režii vašemu běžícímu procesu a zpomaluje ho na základě faktorů, které zahrnují velikost procesu a počet aktivních vláken.

Tato funkce je ve verzi Preview pro vydání sady Visual Studio 2019 s licencí na cestách Live.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Spuštění Snapshot Debugger s povoleným časovým laděním
> * Nastavení snímkovací bod a shromáždění časového cestovního záznamu
> * Spustit ladění pro záznam o cestě k času

## <a name="prerequisites"></a>Požadavky

* Čas cestovního ladění pro Azure Virtual Machines (VM) je k dispozici pouze pro Visual Studio 2019 Enterprise nebo vyšší s **úlohou vývoje Azure**. (Na kartě **jednotlivé součásti** najdete v části **ladění a testování**  >  **Ladicí program snímků**.)

    Pokud ještě není nainstalovaný, nainstalujte [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Čas cestovního ladění je k dispozici pro následující webové aplikace virtuálních počítačů Azure:
  * ASP.NET aplikace (AMD64) běžící na .NET Framework 4,8 nebo novějším.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Spuštění Snapshot Debugger s povoleným časovým laděním

1. Otevřete projekt, pro který chcete shromáždit záznam o cestě k času.

    > [!IMPORTANT]
    > Pokud chcete začít TTD, musíte otevřít *stejnou verzi zdrojového kódu* , která je publikovaná ve službě Azure VM Service.

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

1. Kliknutím na **Spustit shromažďování** zapněte snímkovací bod.

   ![Zapnout snímkovací bod](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Pořízení snímku

Když je zapnutá funkce snímkovací bod, zachycuje snímek pokaždé, když se spustí snímkovací bod řádek kódu. Toto spuštění může být způsobeno skutečným požadavkem na serveru. Pokud chcete vynutit, aby se váš snímkovací bod přihlédl, přejděte do zobrazení prohlížeče vašeho webu a proveďte všechny požadované akce, které způsobí, že bude dosaženo snímkovací bod.

## <a name="start-debugging-a-time-travel-recording"></a>Spustit ladění pro záznam o cestě k času

1. Když je dosaženo snímkovací bod, zobrazí se snímek v okně Diagnostické nástroje. Chcete-li otevřít toto okno, vyberte možnost **ladění > Windows > zobrazit diagnostické nástroje**.

   ![Otevřít snímkovací bod](../debugger/media/snapshot-diagsession-window.png)

1. Kliknutím na odkaz Zobrazit snímek otevřete záznam o cestě k času v editoru kódu.
  
   Můžete provést všechny řádky kódu zaznamenané TTD pomocí tlačítek **pokračovat** a **zpět pokračovat** . Kromě toho můžete panel nástrojů **ladění** použít k **zobrazení dalšího příkazu**, **Krokovat krok dovnitř**, **Krokovat**s krokem, **Krokovat**s **krokem, krokovat zpět**, krokovat **zpět**a **krokovat zpět**.

   ![Spustit ladění](../debugger/media/time-travel-debugging-step-commands.png)

   Můžete také použít okna **místní**hodnoty, **kukátka**a **zásobník volání** a také vyhodnotit výrazy.

   ![Kontrola dat snímku](../debugger/media/time-travel-debugging-start-debugging.png)

    Samotný web je stále živý a koncoví uživatelé na ni neovlivňují žádné následné aktivity TTD. Ve výchozím nastavení je zachycen pouze jeden snímek na snímkovací bod: po zachycení snímku se snímkovací bod vypne. Pokud chcete zachytit jiný snímek na snímkovací bod, můžete snímkovací bod znovu zapnout kliknutím na **aktualizovat kolekci**.

**Potřebujete pomoc?** Podívejte se na téma [řešení potíží a známé problémy](../debugger/debug-live-azure-apps-troubleshooting.md) a [Nejčastější dotazy ke stránkám ladění snímků](../debugger/debug-live-azure-apps-faq.md) .

## <a name="set-a-conditional-snappoint"></a>Nastavení podmíněného snímkovací bod

Pokud je obtížné znovu vytvořit konkrétní stav ve vaší aplikaci, zvažte, zda může pomáhat použití podmíněného snímkovací bod. Podmíněné snímkovací body vám pomůžou se vyhnout shromažďování času na nahrávání, dokud aplikace nevstoupí do požadovaného stavu, například když má proměnná určitou konkrétní hodnotu, kterou chcete zkontrolovat. [Podmínky můžete nastavit pomocí výrazů, filtrů nebo počtu volání](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak shromáždit Virtual Machines pro službu Azure na více časových cestách. Možná budete chtít přečíst si další podrobnosti o Snapshot Debugger.

> [!div class="nextstepaction"]
> [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)