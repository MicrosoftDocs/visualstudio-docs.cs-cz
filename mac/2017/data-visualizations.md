---
title: Ladění – vizualizace dat
description: Ladění je běžné a nezbytné, což je součást programování. Visual Studio pro Mac obsahuje celou sadu funkcí, aby bylo ladění snadné. V tomto článku se podíváme na různé vizualizace dat, které se dají zobrazit při kontrole objektů v ladicím programu.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 3355b81406d2b510dc13604a026bcd014bf9dbcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984754"
---
# <a name="data-visualizations"></a>Vizualizace dat

Visual Studio pro Mac zahrnuje podporu uživatelského rozhraní pro ladicí program, což umožňuje vizualizace hodnot proměnné, pole nebo vlastnosti při ladění. Tyto vizualizace dat zobrazují rozšířenou verzi dat a umožňují vývojářům kontrolovat známé struktury, například zobrazení barvy barevné struktury.

Vizualizace v  **místní** nabídce ladění se dají zobrazit tak, že kliknete na ikonu náhledu, která se zobrazí napravo od hodnoty, když uživatel najede na řádek:

![Místní panel](media/data-visualizations-image9.png)

Následující seznam vyhledá mnoho nových vizualizací, které jsou k dispozici při ladění v Visual Studio pro Mac.

## <a name="point"></a>Vyberte
Bod/PointF nebo CGPoint v iOS a Mac se vykreslí jako řazená kolekce členů ukazující hodnoty X a Y na panelu ladění:

![Vizualizace bodů](media/data-visualizations-image10.png)

## <a name="size"></a>Velikost
Velikost/SizeF nebo CGSize v iOS a Mac se vykreslí jako obdélník. Je vykreslený tak, aby se škáloval až do doby, kdy rozměr rozroste po 250 px, a v takovém případě bude tento obdélník škálovat s největší dimenzí jako 250 px:

[Vizualizace velikosti](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Obdélník
V případě obdélníku, RectangleF nebo CGRect v iOS a Mac se zobrazí rozměry a počátek. Podobně jako velikost se vykreslí do škály, dokud dimenze nerůstá v posledních 250 px:

![Vizualizace obdélníku](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Souřadnice
Souřadnice se vykreslují na mapě s umístěním připnutým do středu:

[Vizualizace souřadnic](media/data-visualizations-image13.png)

## <a name="color"></a>Color
Zobrazí se vlastnosti UIColor, CGColor a Color, které vysvětlují náhledy barev, komponenty RGBA, hodnoty odstín a sytost a hexadecimální hodnotu barvy:

![Vizualizace barev](media/data-visualizations-image14.png)

## <a name="images"></a>Image

Médium se bude vykreslovat pro škálování, až do maximální dimenze 250 px a bude se škálovat tak, aby se vešlo, když obrázek překročí 250 px:

![Vizualizace obrázků](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Bézierovy křivky

Vizualizér zobrazí `NSBezierPath` :

![Vizualizace Bézierovy křivky](media/data-visualizations-image16.png)

## <a name="string"></a>Řetězec

Řetězec kratší než 100 znaků se zobrazí v plném rozsahu bez náhledu. Ve verzi Preview se v plném rozsahu zobrazují i delší řetězce. Řetězce lze upravovat a Vizualizér je doprovázen tlačítkem upravit, což umožňuje, aby se hodnota řetězce upravovala buď ve verzi Preview, nebo v editoru řetězcové hodnoty, jak je uvedeno níže:

![Vizualizace řetězců](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Malé řetězce:
![Vizualizace malých řetězců](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Střední délka řetězců:
![Vizualizace středních řetězců](media/data-visualizations-image19.png)

### <a name="editor"></a>Editoru

![Vizualizace editoru](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Rozhraní

Rozhraní IEnumerable vytvoří výčet všech hodnot; hodnoty jednotlivých lze zobrazit kliknutím na tlačítko **Zobrazit** hodnoty. Možnost IEnumerable nebude zobrazovat hodnoty pro objekty, jako například `Array` ,, `ArrayList` `List<>` , `Dictionary<,>` protože mají vlastní nástroje pro vizualizaci ladicího programu.

![Vizualizace IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Další vizualizace

Některé další typy, které mají také vlastní vložené vizualizace, jsou uvedeny níže:

![Jiná vizualizace](media/data-visualizations-image23.png)

* **Primitiva**
  * Tím se zobrazí nezpracovaná hodnota primitivního typu.
* **Výčet**
  * Tím se zobrazí hodnota pole bez kvalifikátoru typu výčtu.
* **Řazené kolekce členů**
  * Zobrazuje se ve formátu (,).
* **Null**
  * Zobrazí hodnotu null.
* **Adresa URL**
  * Zobrazí se hypertextový odkaz s odkazem.
* **IntPtr**
  * Zobrazí se hexadecimální reprezentace IntPtr.

## <a name="see-also"></a>Viz také

- [Kontrola proměnných v oknech automatické hodnoty a místní hodnoty (Visual Studio ve Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Zobrazení řetězců v Vizualizér (Visual Studio ve Windows)](/visualstudio/debugger/string-visualizer-dialog-box)