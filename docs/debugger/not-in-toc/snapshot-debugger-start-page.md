---
title: Úvodní stránka pro Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62905245"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Začínáme s Snapshot Debugger

Visual Studio Snapshot Debugger je teď připojený ke službě a vy můžete začít shromažďovat snímky, které vám pomůžou s laděním.

Pokud chcete použít Snapshot Debugger, nastavte v kódu snímkovací body, klikněte na tlačítko a začněte shromažďovat snímky a potom scénář spusťte. Při spuštění kódu, ve kterém jste nastavili snímkovací bod, se vytvoří snímek aplikace. Pak otevřete snímek kliknutím na něj v aplikaci Visual Studio v okně Diagnostické nástroje. Nyní můžete tento snímek z vaší služby ladit stejně jako místní. Podrobné pokyny najdete v tématu o tom, jak dál číst.

## <a name="collect-and-view-snapshots"></a>Shromažďování a zobrazování snímků

Snapshot Debugger shromažďuje snímky z vaší aplikace. Snímky jsou jako obrázky Appication v určitém časovém okamžiku. Aplikaci Visual Studio sdělíte, kdy a kde se má shromáždit snímek nastavením snímkovací bod v kódu. V snímkovací bod můžete nastavit podmínky, které potřebujete, abyste měli jistotu, že získáte snímek problému, který zkoumáte.

### <a name="set-a-snappoint"></a>Nastavení snímkovací bod

1. V editoru kódu klikněte na levé tlačítko vedle řádku kódu, který vás zajímá, a nastavte snímkovací bod. Ujistěte se, že se jedná o kód, který víte, že se spustí.

    ![Nastavení snímkovací bod v editoru](../media/snapshot-startpage-set-snappoint.png)

    Po kliknutí na levou stranu se zobrazí fialový šestiúhelník.

2. Kliknutím na **Spustit shromažďování** zapněte snímkovací bod.

### <a name="open-a-snapshot"></a>Otevření snímku

1. Když je dosaženo snímkovací bod, zobrazí se snímek v okně Diagnostické nástroje napravo. Pokud se okno neotevře, můžete ho otevřít výběrem možnosti **ladit**  >  **Windows**  >  **Zobrazit diagnostické nástroje**.

    ![Snímek v okně Diagnostické nástroje](../media/snapshot-startpage-diagsession-window.png)

2. Dvakrát klikněte na snímek a otevřete ho.

### <a name="inspect-snapshot-data"></a>Kontrola dat snímku

Z tohoto zobrazení můžete na proměnné umístit ukazatel myši a zobrazit tak tipy, použít místní okna, kukátka a zásobník volání a také vyhodnotit výrazy.

Samotný web je stále živý a koncoví uživatelé na něj nebudou mít vliv. Ve výchozím nastavení je pro každý snímkovací bod zachycen pouze jeden snímek. To znamená, že po zachycení snímku se snímkovací bod vypne. Pokud chcete zachytit jiný snímek na snímkovací bod, můžete snímkovací bod znovu zapnout kliknutím na **aktualizovat kolekci**.

### <a name="set-a-logpoint"></a>Nastavení protokolovací bod

1. Klikněte pravým tlačítkem myši na ikonu snímkovací bod (purpurový šestiúhelník) a vyberte **Nastavení**.

2. V okně **Nastavení snímkovací bod** vyberte **Akce**.

    ![Podmínky snímkovací bod](../media/snapshot-startpage-logpoint.png)

3. Do pole **zpráva** zadejte protokolovou zprávu, kterou chcete protokolovat. Můžete také vyhodnotit proměnné ve zprávě protokolu jejich umístěním do složených závorek.

    Pokud zvolíte možnost **Odeslat do okno výstup**, zpráva se zobrazí v okně diagnostické nástroje, když se protokolovací bod.

    Pokud zvolíte **Odeslat do protokolu aplikace**, zobrazí se zpráva kdekoli, kde můžete zobrazit zprávy z `System.Diagnostics.Trace` (nebo `ILogger` v .NET Core), jako je například App Insights, když se protokolovací bod.

## <a name="learn-more"></a>Další informace

Další informace o Snapshot Debugger najdete na [stránce docs](../debug-live-azure-applications.md). Přečtěte si další informace o nastavení podmínek usnadňujících vyhledání chyb.

## <a name="dont-show-me-this-again"></a>Tento dialog už příště nezobrazovat

Chcete-li nikdy po připojení Snapshot Debugger znovu zobrazit úvodní stránku Snapshot debugger, změňte možnost **Zobrazit stránku Začínáme při spuštění relace** v **nabídce**  >  **Možnosti**nástroje  >  **Snapshot Debugger**.

![Stránka možností nástroje Snapshot Debugger](../media/snapshot-startpage-tools-options.png)
