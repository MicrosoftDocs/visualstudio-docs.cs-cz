---
title: Ladění – vizualizace dat
description: Ladění je běžnou a nezbytnou součástí programování. Visual Studio pro Mac obsahuje celou sadu funkcí, které usnadňují ladění. Tento článek se zabývá různými vizualizacemi dat, které lze zobrazit při kontrole objektů v ladicím programu.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 14696040160dfc33f89b7647fb73b116b41afa16
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691731"
---
# <a name="data-visualizations"></a>Vizualizace dat

Visual Studio pro Mac zahrnuje podporu ui pro ladicí program, který umožňuje vizualizace hodnot proměnné, pole nebo vlastnost při ladění. Tyto vizualizéry dat zobrazit rozšířenou verzi dat a umožňují vývojářům kontrolovat známé struktury, například zobrazující barvu struktury barev.

Vizualizéry v plyšové **matné** ploše Local pad lze zobrazit kliknutím na ikonu náhledu, která se zobrazí vpravo od hodnoty, když uživatel najede myší na řádek:

![Místní podložka](media/data-visualizations-image9.png)

Níže uvedený seznam se zabývá mnoha novými vizualizacemi, které jsou k dispozici při ladění v sadě Visual Studio for Mac.

## <a name="point"></a>Bod
Point/PointF nebo CGPoint v iOS a Macu se vykreslí jako n-tice zobrazující hodnoty X a Y v ladicí ploše:

![Vizualizace bodů](media/data-visualizations-image10.png)

## <a name="size"></a>Velikost
Velikost/VelikostF nebo CGSize v iOS a Macu se vykreslí jako obdélník. Je nakreslena na měřítko, dokud dimenze zvětší kolem 250 px, v tomto okamžiku bude měřítko obdélník s největší rozměr jako 250 px:

[Vizualizace velikosti](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Obdélník
Rectangle/RectangleF nebo CGRect v iOS a Macu zobrazí rozměry a počátek. Podobně jako velikost, je nakreslena na měřítko, dokud dimenze roste kolem 250 px:

![Vizualizace obdélníku](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Koordinovat
Souřadnice jsou vykresleny na mapě s umístěním připnutým ke středu:

[Koordinovat vizualizaci](media/data-visualizations-image13.png)

## <a name="color"></a>Barvy
Zobrazí se vlastnosti UIColor, CGColor a Color zobrazující náhled barev, komponenty RGBA, hodnoty sytost odstínu a šestnáctkové hodnoty barvy:

![Vizualizace barev](media/data-visualizations-image14.png)

## <a name="images"></a>Image

Média budou vykreslena v měřítku až do maximálního rozměru 250 px a bude zmenšena tak, aby se vešla, když obraz překročí 250 px:

![Vizualizace obrazu](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bezierovy křivky

Vizualizér `NSBezierPath`zobrazí :

![Vizualizace Bezierovy křivky](media/data-visualizations-image16.png)

## <a name="string"></a>Řetězec

Řetězec méně než 100 znaků se zobrazí v plném rozsahu, bez náhledu. Delší řetězce jsou zobrazeny v plném rozsahu v náhledu. Řetězce jsou upravitelné a vizualizér je doplněn tlačítkem pro úpravy, které umožňuje úpravu hodnoty řetězce v náhledu nebo v editoru hodnot řetězců, jak je znázorněno níže:

![Vizualizace řetězce](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Malé řetězce:
![Vizualizace malých řetězců](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Středně dlouhé řetězce:
![Vizualizace s vodíš](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

![Vizualizace editoru](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Ienumerable

IEnumerable enumerates všechny hodnoty; hodnoty každého z nich lze zobrazit klepnutím na tlačítko **Zobrazit** hodnoty. Možnost IEnumerable nezobrazí hodnoty pro `Array`objekty, jako je například , `ArrayList`, `List<>` `Dictionary<,>` protože mají své vlastní vizualizéry ladicího programu.

![Vizualizace iEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Další vizualizéry

Některé další typy, které mají také své vlastní inline vizualizéry jsou uvedeny níže:

![Další vizualizace](media/data-visualizations-image23.png)

* **Primitiva**
  * Zobrazí se nezpracovaná hodnota primitivního typu.
* **Výčet**
  * Zobrazí se hodnota pole bez kvalifikátoru typu výčtu.
* **Tuple**
  * Zobrazeno ve formátu (,)
* **Null**
  * Zobrazí hodnotu null.
* **Adresa URL**
  * Zobrazí se hypertextový odkaz, na který lze kliknout.
* **Intptr**
  * Zobrazí se šestnáctková reprezentace IntPtr.

## <a name="see-also"></a>Viz také

- [Kontrola proměnných v oknech Autos a Locals (Visual Studio v systému Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Zobrazení řetězců ve vizualizéru (Visual Studio v systému Windows)](/visualstudio/debugger/string-visualizer-dialog-box)