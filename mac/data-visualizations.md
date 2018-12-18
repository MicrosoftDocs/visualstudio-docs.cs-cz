---
title: Ladění - vizualizace dat
description: Ladění je běžné a potřeby součástí programování. Visual Studio for Mac obsahuje celou sadu funkcí pro zajištění snadné ladění. Tento článek ukazuje různé datové vizualizace, které si můžou prohlédnout při kontrole objektů v ladicím programu.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 896fa055c536f9f3ee693773ad4f4ae0edd7e7fe
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349436"
---
# <a name="data-visualizations"></a>Vizualizace dat

Visual Studio for Mac obsahuje podporu uživatelského rozhraní pro ladicí program umožní vizualizace hodnoty proměnné, pole nebo vlastnost při ladění. Tyto vizualizérů dat zobrazit rozšířenou verzi data a umožňují vývojářům ke kontrole známé struktury, například zobrazení barvy, barvy struktury.

Vizualizéry v ladění **místní** panel lze zobrazit kliknutím na ikonu ve verzi preview, která se zobrazí napravo od hodnoty, když uživatel najede myší na řádku:

![Místní panel](media/data-visualizations-image9.png)

Níže uvedeného seznamu vypadá na řadu nových vizualizací, které jsou k dispozici při ladění v sadě Visual Studio pro Mac.

## <a name="point"></a>Bod
Bod/PointF nebo CGPoint v iOS a Mac, zobrazí se takto řazené kolekce členů zobrazují hodnoty X a Y v panelu ladění:

![Bod vizualizace](media/data-visualizations-image10.png)

## <a name="size"></a>Velikost
O velikosti/SizeF nebo CGSize v iOS a Mac, zobrazí se takto obdélníku. Jeho vykreslení škálování, dokud dimenze roste posledních 250 px, v tomto okamžiku škálovaly obdélníku s největší dimenze jako 250 px:

[Velikost vizualizace](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Obdélník
Obdélník/RectangleF nebo CGRect v iOS a Mac, se zobrazí, dimenze a původu. Podobně jako když velikost, byl vykreslený na škálování, dokud dimenze roste posledních 250 px:

![Vizualizace obdélník](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Souřadnice
Souřadnice jsou zobrazeny na mapě, umístěním připnutá k centru pro:

[Souřadnice vizualizace](media/data-visualizations-image13.png)

## <a name="color"></a>Barva
Zobrazí se vlastnosti UIColor, CGColor a barvu znázorňující náhled barvy, komponenty RGBA, hodnoty Hue-sytost světlosti a šestnáctková hodnota barvy:

![Barva vizualizace](media/data-visualizations-image14.png)

## <a name="images"></a>Obrázky

Zobrazí se médií škálovat až na maximální dimenze 250 px a bude škálovat podle při obrázek překračuje 250 px:

![Obrázek vizualizace](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bézierovy křivky

Vizualizéru se zobrazí `NSBezierPath`:

![Vizualizace Bézierovu křivku](media/data-visualizations-image16.png)

## <a name="string"></a>String

Řetězec méně než 100 znaků se zobrazí v plné výši bez ve verzi preview. Delší řetězce jsou zobrazeny v plném rozsahu ve verzi preview. Řetězce se upravovat a vizualizéru se sadou tlačítko pro úpravy, řetězec hodnoty upravit buď ve verzi preview, nebo v řetězci hodnotu editoru je uvedeno níže:

![Řetězec vizualizace](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Malé řetězce:
![Malé řetězec vizualizace](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Střední délky řetězce:
![Střední řetězec vizualizace](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

![Editor vizualizace](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable vytvoří výčet všech hodnot. jejich hodnoty můžete zobrazit kliknutím **zobrazit** tlačítko hodnoty. Možnost IEnumerable nezobrazí hodnoty pro objekty, jako `Array`, `ArrayList`, `List<>`, `Dictionary<,>` jako ty se musí vlastních vizualizérů ladění.

![Vizualizace IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Další Vizualizérech

Některé typy, které zároveň mají své vlastní vizualizéry vložené jsou uvedeny níže:

![Ostatní vizualizace](media/data-visualizations-image23.png)

*   **Primitiva**
    *   Tím se zobrazí nezpracované hodnotě primitivního typu.
*   **Výčet**
    *   Zobrazí se hodnota pole bez kvalifikátoru typu výčtu.
*   **Řazené kolekce členů**
    *   Zobrazují ve formátu ()
*   **Hodnotu Null**
    *   Zobrazí hodnotu "null".
*   **ADRESA URL**
    *   Tím se zobrazí po kliknutí hypertextový odkaz.
*   **IntPtr**
    *   Tato akce zobrazí šestnáctkovou reprezentací IntPtr.

## <a name="see-also"></a>Viz také:

- [Kontrolovat proměnné v okně Automatické hodnoty a místní hodnoty (Visual Studio na Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Zobrazení řetězců ve vizualizéru (Visual Studio na Windows)](/visualstudio/debugger/string-visualizer-dialog-box)