---
title: Vizualizace dat pomocí R
description: Jak vykreslit data z programů R v sadě Visual Studio pomocí vykreslovacích oken.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a48ad7800f8ea2b992e848cfbf6b4fdac99b2062
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62811067"
---
# <a name="create-visual-data-plots-with-r"></a>Vytváření vizuálních datových parcel pomocí jazyka R

Vykreslování je klíčovou součástí pracovního postupu datového vědce. V nástroji R pro visual studio (RTVS) se všechny vykreslovací aktivity soustředí kolem jednoho nebo více vykreslovacích oken, které jsou navrženy tak, aby s touto klíčovou aktivitou zlepšily vaši produktivitu.

![Vykreslení obrázku hrdiny](media/plotting-hero-image.png)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | Podívejte se na [video (youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) o vykreslování s R (2m 02s). |

## <a name="the-plot-window"></a>Okno parcely

Okno parcely obsahuje řadu parcel, kde je každý `plot` obrázek generován příkazem. Například pomocí `plot(1:100)` vytvoří nové okno vykreslování, pokud ještě není k dispozici:

![1 až 100 Lineární obrázek](media/plotting-1-to-100.png)

Technicky vzato, Příkazy R `plot` vykreslují svůj výstup do grafického zařízení R; okno vykreslování vykreslení obsahu grafického zařízení R, což je důvod, proč každé okno vykreslování je uveden číslo zařízení.

Vykreslovací okna jsou nezávislá na projektech sady Visual Studio a zůstávají otevřená při načítání a zavírání projektů.

Generování množení použije okno "aktivního" vykreslení a uloží mu všechny předchozí vykreslení do historie vykreslení (viz [Historie vykreslování](#plot-history)). Zadejte `plot(100:1)` například a první obrázek se nahradí sestupnou čárou.

Stejně jako všechna ostatní okna sady Visual Studio. okno parcely podporuje přizpůsobená rozložení (viz [Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Vykreslovací okna mohou být ukotvena na různých místech v rámci sady Visual Studio, její velikost v rámci nebo vytažena z rámečku zcela pro nezávislou velikost.

Změna velikosti zobrazovat okno vždy re-renders vykreslí vykreslování tak, aby v nejlepší kvalitě obrazu. Obvykle chcete změnit velikost obrázku před exportem vykreslování do souboru nebo do schránky pomocí příkazů popsaných v další části.

## <a name="plot-window-commands"></a>Příkazy okna vykreslení

Panel nástrojů vykreslovacím okně obsahuje příslušné příkazy, z nichž většina je také k dispozici prostřednictvím nabídky > **Vykreslení** **nástrojů R.**

| Tlačítko | Příkaz | Popis |
| --- | --- | --- |
| ![Nové tlačítko okna parcely](media/plotting-toolbar-01-new-plot-window.png) | Nové okno parcely | Vytvoří samostatné okno parcely s vlastní historií. Viz [Více vykreslování oken](#multiple-plot-windows). |
| ![Tlačítko Aktivovat okno vykreslování](media/plotting-toolbar-02-activate-plot-window.png) | Aktivovat okno parcely | Nastaví aktuální okno vykreslení jako aktivní `plot` okno tak, aby následné příkazy byly vykresleny do tohoto okna. Viz [Více vykreslování oken](#multiple-plot-windows). Viz [Více vykreslování oken](#multiple-plot-windows). |
| ![Tlačítko okna Historie vykreslování](media/plotting-toolbar-03-plot-history.png) | Okno historie vykreslování | Otevře okno se všemi obrázky v historii zobrazenými jako miniatury. Viz [Historie vykreslování](#plot-history). |
| ![Tlačítka historie vykreslování](media/plotting-toolbar-04-plot-history-arrows.png) | Předchozí/Další vykreslování |  Přejde na předchozí nebo další obrázek v historii. Historii můžete také procházet pomocí ctrl+alt+f11 (předchozí) a ctrl+alt+f12 (další). Viz [Historie vykreslování](#plot-history). |
| ![Tlačítko Uložit jako obrázek](media/plotting-toolbar-05-save-as-image.png)| Uložit jako obrázek | Zobrazí výzvu k zadání názvu souboru a uloží aktuální obrázek (obsah okna při velikosti okna) do souboru obrázku. Dostupné formáty `.png` `.jpg`jsou `.bmp`, `.tif`, , a . |
| ![Tlačítko Uložit jako PDF](media/plotting-toolbar-06-save-as-pdf.png)| Uložit jako PDF | Uloží aktuální vykreslení do souboru PDF s použitím aktuální velikosti okna. Vykreslení se znovu vykreslí, pokud se změní velikost PDF. |
| ![Tlačítko Kopírovat jako bitmapu](media/plotting-toolbar-07-copy-as-bitmap.png)| Kopírovat jako bitmapu | Zkopíruje vykreslení do schránky jako rastrovou bitmapu pomocí aktuální velikosti okna. |
| ![Tlačítko Kopírovat jako metasoubor](media/plotting-toolbar-08-copy-as-metafile.png)| Kopírovat jako metasoubor | Zkopíruje parcelu do schránky jako [metasoubor systému Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedie). |
| ![Tlačítko Odstranit vykreslování](media/plotting-toolbar-09-remove-plot.png)| Odebrat obrázek | Odebere aktuální obrázek z historie. |
| ![Vymazat tlačítko Vymazat všechny parcely](media/plotting-toolbar-10-clear-all-plots.png) | Vymazat všechny parcely | Odebere všechny parcely z historie (výzvy k potvrzení). |

## <a name="multiple-plot-windows"></a>Více vykreslování oken

Vzhledem k tomu, že datoví vědci často pracují s mnoha obrázky z mnoha různých datových sad, rtvs umožňuje vytvořit tolik nezávislých oken vykreslování. Potom můžete uspořádat tato okna však chcete v rámci sady Visual Studio nebo mimo tento rámec úplně. (Obecné informace o ukotvení a změna velikosti oken najdete [v tématu Přizpůsobení rozložení oken v sadě Visual Studio.)](../ide/customizing-window-layouts-in-visual-studio.md)

Nové okno vykreslení vytvoříte pomocí tlačítka panelu nástrojů nebo **nástroje** > R Vykreslí**nové okno vykreslování****Plots** > . Nové okno parcely se stane *aktivním* oknem, což je místo, kde jsou vykresleny nové parcely. Chcete-li změnit aktivní okno, přepněte na něj a vyberte tlačítko Aktivovat panel nástrojů **okno vykreslit** nebo **nástroje** > R**Nástroje Vykreslit** > **aktivovat okno vykreslení**.

Vykreslování jsou také nezávislé objekty, což znamená, že je můžete kopírovat nebo přesouvat mezi okny vykreslování pomocí přetažení myší nebo pomocí příkazů **Kopírovat**, **Vyjmout**a **Vložit** v kontextu pravým tlačítkem myši a **Upravit** nabídky.

Výchozí chování pro přetažení je kopírovat; můžete se pohybovat, přetahovat a podržet klávesu **Shift.**

## <a name="plot-history"></a>Historie vykreslování

Příkazy vykreslení jsou udržovány v historii vykreslování pro každé okno a zajišťují, že všechny vykreslování v rámci relace zůstane zachováno. Chcete-li procházet historii, použijte tlačítka se šipkami na panelu nástrojů okna vykreslování nebo **Ctrl**+**Alt**+**F11** a **Ctrl**+**Alt**+**F12**. Můžete také odstranit jednotlivé parcely nebo vymazat všechny obrázky z okna znovu pomocí tlačítek panelu nástrojů nebo příkazů nabídky**Nástroje** **R.** > 

Chcete-li zobrazit celou kolekci parcel, otevřete okno historie vykreslování pomocí tlačítka panelu nástrojů nebo okna Historie**vykreslení** >  **nástrojů** > Nástroje Nástroje Nástroje **.**
Historie poskytuje seznam miniatur obrázků, které byly zobrazeny v tomto okně, seskupené podle různých oken vykreslování (nebo zařízení). Pomocí tlačítek lupy na panelu nástrojů se změní velikost miniatur.

![Okno historie vykreslování](media/plotting-plot-history-window.png)

Chcete-li otevřít obrázek v přidruženém okně, poklepejte na něj, vyberte ho a pak vyberte tlačítko Zobrazit panel nástrojů **Vykreslit** nebo klepněte pravým tlačítkem myši a vyberte **Zobrazit vykreslení**. Můžete také vybrat jednotlivé obrázky a zkopírovat, vyjmout nebo odstranit z kontextového nebo **upravit** nabídky.

Životnost historie vykreslování ve všech oknech je vázána na životnost interaktivní relace R. Pokud obnovíte relaci R nebo ukončíte a restartujete visual studio, historie vykreslování se vynuluje.

## <a name="programmatically-manipulate-plot-windows"></a>Programově manipulovat s okny parcel

Můžete programově manipulovat s vykreslovacími okny z kódu R pomocí čísel zařízení k identifikaci konkrétních vykreslovacích oken.

- `dev.list()`: Seznam všech grafických zařízení v rámci aktuální relace R.
- `dev.new()`: Vytvoření nového grafického zařízení (nové okno parcely).
- `dev.set(<device number>)`: Nastavte aktivní grafické zařízení.
- `dev.off()`: Odstraňte aktivní zařízení.
