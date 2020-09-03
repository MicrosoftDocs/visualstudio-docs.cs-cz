---
title: Vizualizace dat pomocí jazyka R
description: Jak vykreslovat data z programů R v aplikaci Visual Studio pomocí oken vykreslení.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: dbb3984385e0042c669f8aad1d5bb4a2f64de917
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801617"
---
# <a name="create-visual-data-plots-with-r"></a>Vytváření vizuálních dat pomocí jazyka R

Vykreslení je klíčovou součástí pracovního postupu pro odborníky přes data. V Nástroje R pro Visual Studio (RTVS) se všechna vykreslící aktivity pohybují kolem jednoho nebo více oken plotru, které jsou navržené pro zlepšení produktivity s touto klíčovou aktivitou.

![Vykreslování obrázku Hero](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![ikona filmové kamery pro video](../install/media/video-icon.png "Přehrát video")
    :::column-end:::
    :::column:::
        [Podívejte se na video (YouTube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) při vykreslování pomocí R (2 min 02s).
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>Okno vykreslení

Okno vykreslení obsahuje řadu ploch, kde je každý graf vygenerován `plot` příkazem. Například použití `plot(1:100)` vytvoří nové okno vykreslení, pokud již není k dispozici:

![1 až 100 lineární vykreslení](media/plotting-1-to-100.png)

Technicky řečeno, příkazy jazyka R `plot` vykreslují výstup do grafického zařízení r. okno vykreslování vykreslí obsah grafického zařízení r, což znamená, že každé okno vykreslení má číslo zařízení.

Okna grafu jsou nezávislá na projektech sady Visual Studio a zůstanou otevřená při načítání a zavírání projektů.

Generování vykreslení používá aktivní okno vykreslení a ukládá z něj předchozí vykreslení historie vykreslení (viz [Historie vykreslení](#plot-history)). Například zadejte `plot(100:1)` a první vykreslení je nahrazeno svislou čárou.

Stejně jako všechny ostatní okna sady Visual Studio. okno vykreslení podporuje přizpůsobená rozložení (viz [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Okna grafu lze ukotvit na různých místech v rámci rámce sady Visual Studio, měnit jeho velikost v rámci tohoto rámce nebo zcela mimo rámec pro nezávislé změny velikosti.

Změna velikosti okna vykreslení vždy znovu vykreslí vykreslení, aby poskytovala nejlepší kvalitu obrazu. Obvykle budete chtít změnit velikost grafu před exportem grafu do souboru nebo do schránky pomocí příkazů popsaných v následující části.

## <a name="plot-window-commands"></a>Příkazy okna grafu

Panel nástrojů grafu obsahuje příslušné příkazy, většina z nich je také k dispozici v nabídce **Nástroje jazyka R**  >  **Plots** .

| Tlačítko | Příkaz | Popis |
| --- | --- | --- |
| ![Tlačítko pro nové okno grafu](media/plotting-toolbar-01-new-plot-window.png) | Nové okno vykreslení | Vytvoří samostatné okno vykreslení s vlastní historií. Zobrazit [několik oken vykreslení](#multiple-plot-windows) |
| ![Aktivovat tlačítko okna grafu](media/plotting-toolbar-02-activate-plot-window.png) | Aktivovat okno vykreslení | Nastaví aktuální okno grafu jako aktivní okno, aby `plot` byly do tohoto okna vykresleny další příkazy. Zobrazit [několik oken vykreslení](#multiple-plot-windows) Zobrazit [několik oken vykreslení](#multiple-plot-windows) |
| ![Tlačítko okna Historie vykreslení](media/plotting-toolbar-03-plot-history.png) | Okno historie grafu | Otevře okno se všemi zobrazeními v historii zobrazenými jako miniatury. Viz [Historie vykreslení](#plot-history). |
| ![Tlačítka historie vykreslení](media/plotting-toolbar-04-plot-history-arrows.png) | Předchozí/další vykreslení |  Přejde na předchozí nebo další vykreslení v historii. Můžete také přejít k historii pomocí kombinace kláves CTRL + ALT + F11 (předchozí) a Ctrl + Alt + F12 (další). Viz [Historie vykreslení](#plot-history). |
| ![Tlačítko Uložit jako obrázek](media/plotting-toolbar-05-save-as-image.png)| Uložit jako obrázek | Zobrazí výzvu k zadání názvu souboru a uloží aktuální vykreslení (obsah okna, v okně velikost okna) do souboru obrázku. Dostupné formáty jsou `.png` , `.jpg` , `.bmp` a `.tif` . |
| ![Tlačítko Uložit jako PDF](media/plotting-toolbar-06-save-as-pdf.png)| Uložit jako PDF | Uloží aktuální vykreslení do souboru PDF pomocí velikosti aktuálního okna. Vykreslení se znovu vykreslí, pokud se změní velikost PDF. |
| ![Tlačítko Kopírovat jako rastrové obrázky](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopírovat jako rastrový obrázek | Zkopíruje vykreslení do schránky jako rastrový rastrový obrázek pomocí velikosti aktuálního okna. |
| ![Tlačítko Kopírovat jako metasoubor](media/plotting-toolbar-08-copy-as-metafile.png)| Kopírovat jako metasoubor | Zkopíruje vykreslení do schránky jako [metasoubor systému Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedii). |
| ![Odebrat tlačítko vykreslení](media/plotting-toolbar-09-remove-plot.png)| Odebrat vykreslení | Odebere aktuální vykreslení z historie. |
| ![Tlačítko pro vymazání všech ploch](media/plotting-toolbar-10-clear-all-plots.png) | Zrušit výběr všech ploch | Odebere všechny z historie (zobrazí výzvu k potvrzení). |

## <a name="multiple-plot-windows"></a>Více oken s vykreslováním

Vzhledem k tomu, že odborníci na data často pracují s mnoha sestavami z mnoha různých datových sad, umožňuje RTVS vytvořit tolik nezávislých oken vykreslení. Tato okna pak můžete uspořádat, například v rámci rámce sady Visual Studio nebo mimo tento rámec. (Viz [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) pro obecné informace o dokování a změně velikosti oken.)

Nové okno vykreslení vytvoříte pomocí tlačítka panelu nástrojů nebo **nástrojů R**, které  >  **vykresluje**  >  **nové okno vykreslení**. Nové okno vykreslení se zobrazí jako *aktivní* okno, kde se vykreslují nové ovládací okno. Chcete-li změnit aktivní okno, přepněte na něj a vyberte tlačítko **aktivovat okno** panelu nástrojů nebo **nástroje R**zobrazit  >  **Plots**  >  **okno aktivovat**.

Jsou to také nezávislé objekty, což znamená, že je můžete kopírovat nebo přesouvat mezi okny vykreslování pomocí myši nebo pomocí myši nebo pomocí příkazů **kopírování**, **vyjmutí**a **vložení** v kontextu a **úpravách** v nabídce klikněte pravým tlačítkem myši.

Výchozí chování při přetahování je kopií; Pokud se chcete pohybovat, přetáhnutím klávesy **SHIFT** můžete přetahovat myší.

## <a name="plot-history"></a>Historie grafu

Příkazy vykreslení jsou uchovávány v historii diagramu pro každé okno, což zajišťuje zachování všech vykreslení v rámci relace. Pokud chcete přejít k historii, použijte tlačítka se šipkami na panelu nástrojů okna výkresu nebo **CTRL** + **+** + **F11** a **CTRL** + **+** + **F12**. Pomocí tlačítek na panelu nástrojů nebo příkazů v nabídce **Nástroje jazyka R**můžete také odebrat jednotlivá vykreslení nebo zrušit zaškrtnutí všech zkusných panelů  >  **Plots** .

Chcete-li zobrazit celou kolekci ploch, otevřete okno historie vykreslení pomocí tlačítka panelu nástrojů nebo **nástrojů R**  >  **Plots**  >  **okna s historií grafu**.
Historie nabízí seznam miniatur pro zobrazení zobrazené v tomto okně seskupené podle různých oken vykreslení (nebo zařízení). Použití tlačítek zvětšení na panelu nástrojů změní velikost miniatur.

![Okno historie grafu](media/plotting-plot-history-window.png)

Chcete-li otevřít vykreslení v přidruženém okně, dvakrát klikněte na tento graf, vyberte jej a pak vyberte tlačítko **Zobrazit** panel nástrojů pro vykreslení. Můžete také kliknout pravým tlačítkem myši na vykreslení a vybrat **Zobrazit graf**. Můžete také vybrat jednotlivé vykreslení a kopírovat, vyjmout nebo odstranit v místních nebo **upravitelných** nabídkách.

Doba života historie grafu napříč všemi okny je vázána na celou dobu života interaktivní relace jazyka R. Pokud resetujete relaci jazyka R nebo ukončíte a restartujete aplikaci Visual Studio, vaše historie vykreslení se resetuje.

## <a name="programmatically-manipulate-plot-windows"></a>Programové manipulace s okny grafu

Můžete programově manipulovat s okny grafu z kódu R pomocí čísel zařízení a identifikovat konkrétní okna s vykreslováním.

- `dev.list()`: Vypíše všechna grafická zařízení v rámci aktuální relace jazyka R.
- `dev.new()`: Vytvořit nové grafické zařízení (nové okno grafu).
- `dev.set(<device number>)`: Nastavte aktivní grafické zařízení.
- `dev.off()`: Odstranit aktivní zařízení.
