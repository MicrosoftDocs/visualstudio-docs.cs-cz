---
title: Průzkumník proměnných pro R
description: Průzkumník proměnných v aplikaci Visual Studio zobrazuje všechny proměnné v daném oboru v aktuální relaci jazyka R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62809796"
---
# <a name="variable-explorer"></a>Průzkumník proměnných

Okno **Průzkumník proměnných** otevřené pomocí **nástrojů r**  >  **Windows**  >  **Průzkumník proměnných** Windows (nebo **CTRL +** + **8** Pokud jste použili **nástroje r**  >  **nastavení pro datové vědy**), zobrazí všechny proměnné v daném oboru v aktuální relaci jazyka R. Pokud například otevřete **Průzkumník proměnných** a do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md)zadejte následující řádky:

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Okno **Průzkumník proměnných** se pak zobrazí takto:

![Okno Průzkumníka proměnných v aplikaci Visual Studio](media/variable-explorer-window.png)

Pokud máte v relaci definovaný složitější datový rámec R, můžete přejít k datům. Například po spuštění můžete procházet `cars <- mtcars` datovou sadu rozbalením různých uzlů v **Průzkumník proměnných**:

![Rozšířené zobrazení Průzkumník proměnných](media/variable-explorer-expanded-results.png)

Chcete-li odstranit proměnné, klikněte pravým tlačítkem myši a vyberte možnost **Odstranit**, nebo vyberte proměnnou a stiskněte klávesu **Delete** .

Můžete také vyhledat pozorování v datovém snímku pomocí přírůstkového vyhledávání. Nejprve rozbalte uzly v datovém rámečku, který chcete vyhledat, a pak do vyhledávacího pole zadejte hledané výrazy.

## <a name="details-table-view"></a>Podrobnosti (tabulka) – zobrazení

Vzhledem k tomu, že data jsou často tabulková, můžete libovolný komplexní datový typ zobrazit jako samostatnou tabulku tak, že vyberete ikonu lupy, kliknete pravým tlačítkem myši a vyberete **Zobrazit podrobnosti**.

![Zobrazení tabulky Průzkumník proměnných](media/variable-explorer-table-view.png)

Kliknutím na záhlaví sloupce seřadíte data podle sloupce (střídavě mezi vzestupně a sestupně). Když podržíte **klávesu SHIFT** a kliknete na další sloupce, přidají se tyto sloupce taky do řazení. Kliknutím na sloupec bez příkazu **SHIFT** vrátíte do řazení s jedním sloupcem.

Pořadí, ve kterém kliknete na záhlaví sloupců, určuje pořadí, ve kterém se provádí řazení. Například můžete **Posunout** + **kliknutím** na sloupec **Cyl** a potom **stisknutím klávesy SHIFT** + dvakrát**kliknout** na sloupec **MPG** , čímž seřadíte seznam pro vzestupné válce a sestupné kilometry na galon:

![Zobrazení tabulky pro řazení dat podle dvou sloupců](media/variable-explorer-table-view-sorting.png)

Vzhledem k tomu, že **Průzkumník proměnných** a tabulková zobrazení jsou v samostatných oknech sady Visual Studio, můžete je uspořádat tak, jak chcete pro souběžnou práci. Obecné pokyny najdete v tématu [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) .

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otevřít v Excelu (nebo v jiné aplikaci podporující sdílený svazek clusteru)

Pro další manipulaci a analýzu je často užitečné exportovat proměnné relace do sdíleného svazku clusteru. Export se provádí pomocí malé ikony Excelu ( ![ ikona exportu Excelu ](media/variable-explorer-excel-icon.png) ) vedle každého uzlu v **Průzkumník proměnných**, nebo kliknutím pravým tlačítkem myši na položku a výběrem možnosti **otevřít v aplikaci sdíleného svazku clusteru**. Výběrem ikony zapíšete data do nového souboru CSV ve složce *%userprofile%\documents\ RTVS_CSV_Exports* a potom tento soubor otevřete, který se otevře v libovolné aplikaci, která je přidružená k příponě *CSV* .

## <a name="scopes"></a>Obory

Ve výchozím nastavení se **Průzkumník proměnných** otevře v globálním oboru. Můžete přepnout na rozsah balíčku výběrem balíčku v rozevíracím seznamu v horní části okna.

![Průzkumník proměnných znázorňující rozsah balíčku](media/variable-explorer-package-scopes.png)

Můžete také přepnout na rozsah funkce při zastavení na zarážce v ladicím programu (Všimněte si, že **Průzkumník proměnných** automaticky nepřepne na rozsah funkce laděného kódu):

![Průzkumník proměnných zobrazující datový rámec během ladění](media/variable-explorer-as-locals-window.png)

**Průzkumník proměnných** automaticky mění rozsah funkcí během psaní kódu v ladicím programu, jako je například zobrazení místních proměnných ve funkci.

## <a name="import-data-into-variable-explorer"></a>Importovat data do Průzkumník proměnných

Dva příkazy na panelu nástrojů **Průzkumník proměnných** , které jsou dostupné taky prostřednictvím nabídky data nástrojů jazyka **r**  >  **Data** , naimportují do relace jazyka r externí datové sady CSV: **importovat datovou sadu do relace jazyka r z webové adresy URL** a **importovat datovou sadu do relace jazyka r z textového souboru**.

Jakmile identifikujete soubor CSV pro import, sada Visual Studio zobrazí dialog **importovat datovou sadu** , ve kterém máte možnosti pro řízení způsobu, jakým se tento datový soubor analyzuje (tj. co je oddělovač polí a jak se mají zpracovat uvozovky). Můžete také zobrazit náhled importovaného datového rámce a původního datového souboru:

![Dialog importovat datovou sadu](media/variable-explorer-import-dataset-dialog.png)
