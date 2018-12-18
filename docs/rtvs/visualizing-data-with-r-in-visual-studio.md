---
title: Vizualizace dat s R
description: Jak k vykreslení dat z aplikací R v sadě Visual Studio pomocí výkresu systému windows.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: f44ba213defef153acd2f5d1ef247bb093448263
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238328"
---
# <a name="create-visual-data-plots-with-r"></a>Vytvoření pozemků vizuální data s R

Vykreslení je klíčovou součástí vědecký pracovník dat pracovního postupu. V R nástrojů pro Visual Studio (RTVS) veškeré aktivity související s výkresu soustředí kolem jeden nebo více výkresu windows, které jsou určeny ke zlepšení efektivity práce se tato aktivita klíče.

![Vykreslení hrdina Image](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (webu youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) na vykreslení s R (2 m 02s). |

## <a name="the-plot-window"></a>Okno vykreslení.

Okno výkresu obsahuje řadu pozemků, kde je generován každý výkresu `plot` příkaz. Například pomocí `plot(1:100)` vytvoří nové okno vykreslení. Pokud jedna již není k dispozici:

![Lineární výkresu 1 až 100.](media/plotting-1-to-100.png)

Technicky platí, že R `plot` příkazy vykreslení jejich výstup do zařízení s R grafiky; okno výkresu vykreslí obsah grafiky zařízení R, což je proto každé okno výkresu je zadané číslo zařízení.

Vykreslení windows jsou nezávislé na projektů sady Visual Studio a zůstane otevřená, jak načíst a zavřete projekty.

Generování vykreslení používá okno "aktivní" výkresu ukládání všechny předchozí ho vykreslení historie vykreslení (v tématu [vykreslení historie](#plot-history)). Zadejte například `plot(100:1)` a první výkresu nahrazena klesající řádku.

Podobně jako všechny ostatní sady Visual Studio windows. okno výkresu podporuje vlastní rozložení (viz [přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Vykreslení windows můžete ukotven v různých umístěních v rámci sady Visual Studio, po změně velikosti v rámci tohoto rámečku nebo vyžádat mimo rámec zcela pro nezávislé změnu velikosti. 

Změna velikosti okna výkresu vždy znovu vykreslí výkresu zajistit nejlepší kvalitu obrazu. Obvykle je vhodné ke změně velikosti vykreslení před exportováním výkresu do souboru nebo do schránky pomocí příkazů popsaných v další části.

## <a name="plot-window-commands"></a>Příkazy okna vykreslení.

Obsahuje použít příkazy, většina z nich jsou také k dispozici prostřednictvím nástrojů okna výkresu **R nástroje** > **pozemků** nabídky.

| Tlačítko | Příkaz | Popis | 
| --- | --- | --- |
| ![Tlačítko nové okno vykreslení.](media/plotting-toolbar-01-new-plot-window.png) | Nové okno vykreslení. | Vytvoří okno samostatné výkresu s vlastním historie. V tématu [více oken výkresu](#multiple-plot-windows). |
| ![Aktivovat tlačítko okno vykreslení.](media/plotting-toolbar-02-activate-plot-window.png) | Aktivovat okno vykreslení. | Nastaví aktuální okno výkresu jako aktivní okno, takže to následné `plot` příkazy jsou vykreslovány do tohoto okna. V tématu [více oken výkresu](#multiple-plot-windows). V tématu [více oken výkresu](#multiple-plot-windows). |
| ![Tlačítko okno historie vykreslení.](media/plotting-toolbar-03-plot-history.png) | Okno historie vykreslení. | Otevře se okno s všechny pozemků v historii zobrazené jako miniatury. V tématu [vykreslení historie](#plot-history). |
| ![Vykreslení historie tlačítka](media/plotting-toolbar-04-plot-history-arrows.png) | Předchozí či následující vykreslení. |  Přejde na předchozí nebo další vykreslení v historii. Můžete taky přejít historie pomocí kombinace kláves Ctrl + Alt + F11 (předchozí) a Ctrl + Alt + F12 (Další). V tématu [vykreslení historie](#plot-history). |
| ![Uložit jako obrázek tlačítka](media/plotting-toolbar-05-save-as-image.png)| Uložit jako Image | Vyzve k zadání pro název souboru a uloží aktuální vykreslení (okno obsahu, na velikost okna) se souborem bitové kopie. Jsou k dispozici formáty `.png`, `.jpg`, `.bmp`, a `.tif`. |
| ![Uložit jako tlačítko PDF](media/plotting-toolbar-06-save-as-pdf.png)| Uložit ve formátu PDF | Uloží aktuální výkresu do souboru PDF, pomocí aktuální velikost okna. Při změně měřítka PDF, bude znovu zpracovat vykreslení. |
| ![Kopírovat jako rastrový obrázek tlačítka](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopírovat jako rastrového obrázku | Zkopíruje vykreslení do schránky jako rastrový obrázek rastrových, pomocí aktuální velikost okna. | 
| ![Kopírovat jako metafile tlačítka](media/plotting-toolbar-08-copy-as-metafile.png)| Kopírovat jako Metafile | Zkopíruje vykreslení do schránky jako [WMF](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). | 
| ![Odebrat tlačítko vykreslení.](media/plotting-toolbar-09-remove-plot.png)| Odebrat vykreslení. | Odebere aktuální výkresu z historie. |
| ![Vymazat všechna ukazuje zeměpisný tlačítko](media/plotting-toolbar-10-clear-all-plots.png) | Ukazuje zeměpisný Vymazat vše | Odebere všechny pozemků z historie (vyzve k potvrzení). |

## <a name="multiple-plot-windows"></a>Více oken vykreslení.

Protože datových vědců často pracovat s mnoha pozemků z mnoha různých datových sad, RTVS umožňuje vytvářet tolik nezávislé výkresu windows. Potom můžete uspořádat tyto windows ale chcete zcela v rámci sady Visual Studio nebo mimo rámec. (Viz [přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) obecné informace o ukotvení a změna velikosti windows.)

Vytvoření nového okna výkresu pomocí tlačítka panelu nástrojů nebo **R nástroje** > **pozemků** > **nové okno výkresu**. Stane se nové okno výkresu *active* okno, které je, kde jsou vykreslovány nové pozemků. Chcete-li změnit aktivní okno, přejděte do něj a vyberte **aktivovat vykreslení okno** tlačítka panelu nástrojů nebo **R nástroje** > **ukazuje zeměpisný**  >  **Aktivovat okno výkresu**.

Jsou příliš, pozemků, nezávislé objekty, což znamená, můžete zkopírovat nebo je přesouvat mezi windows výkresu pomocí buď přetažení myší pomocí myši nebo pomocí **kopie**, **Vyjmout**, a **vložení** příkazy v kontextu klikněte pravým tlačítkem a **upravit** nabídky.

Výchozí chování pro přetažení myší je kopie; Chcete přesunout, a přetáhněte stisknutým **Shift** klíč.

## <a name="plot-history"></a>Vykreslení historie

Vykreslení příkazy jsou zachována ve výkresu historii jednotlivých období, zajistíte, že všechny vaše vykreslení v rámci relace se zachová. Přejděte v historii, pomocí tlačítek na panelu nástrojů okna výkresu nebo **Ctrl**+**Alt**+**F11** a **Ctrl** + **Alt**+**F12**. Můžete také odebrat jednoho pozemků nebo zrušte všechny pozemků z okna znovu pomocí tlačítka panelu nástrojů nebo **R nástroje** > **ukazuje zeměpisný** příkazy nabídky.

Pokud chcete zobrazit celou kolekci pozemků, otevřete okno historie výkresu pomocí tlačítka panelu nástrojů nebo **R nástroje** > **ukazuje zeměpisný** > **okno historie výkresu**.
Historie poskytuje seznam miniatury o zobrazené v okně, seskupené podle různých výkresu windows (nebo zařízení). Pomocí zvětšení tlačítek na panelu nástrojů změní velikost miniatur.

![Okno historie vykreslení.](media/plotting-plot-history-window.png)

Otevřete vykreslení v jeho přidružené okně, dvakrát klikněte na tento výkresu, vyberte ho a pak vyberte **zobrazit výkresu** tlačítka panelu nástrojů nebo klikněte pravým tlačítkem a vyberte **zobrazit výkresu**. Můžete také vybrat konkrétního výkresu a zkopírujte, Vyjmout, nebo odstraňte z kontextu klikněte pravým tlačítkem nebo **upravit** nabídky.

Životnost interaktivní relace R je vázána životnost historii výkresu mezi všechny systémy windows. Pokud resetování relace R, nebo ukončete a restartujte Visual Studio, je resetovat historii vykreslení.

## <a name="programmatically-manipulate-plot-windows"></a>Programově měnit windows vykreslení.

Vykreslení windows z kódu jazyka R, můžete upravit prostřednictvím kódu programu pomocí čísla zařízení identifikovat konkrétní výkresu windows. 

- `dev.list()`: Seznam všech zařízení grafiky v aktuální relaci R.
- `dev.new()`: Vytvoření nového zařízení grafiky (nové okno výkresu).
- `dev.set(<device number>)`: Nastavte aktivní grafiky zařízení.
- `dev.off()`: Odstraňte aktivní zařízení.
