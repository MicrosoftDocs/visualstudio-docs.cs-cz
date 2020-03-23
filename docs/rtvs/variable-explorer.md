---
title: Průzkumník proměnných pro R
description: Průzkumník proměnných v sadě Visual Studio zobrazuje všechny proměnné v daném oboru v aktuální relaci R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809796"
---
# <a name="variable-explorer"></a>Průzkumník proměnných

Okno **Průzkumník proměnných,** které bylo otevřeno pomocí**průzkumníka proměnných** **systému** > **Windows** > (nebo **ctrl**+**8,** pokud jste použili nastavení datové**vědy**nástroje **R** > ), zobrazuje všechny proměnné v daném oboru v aktuální relaci R. Pokud například otevřete **Průzkumník proměnných** a do [interaktivního okna](interactive-repl-for-r-in-visual-studio.md)zadáte následující řádky :

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Okno **Průzkumník proměnných** se pak zobrazí takto:

![Okno průzkumníka proměnných v sadě Visual Studio](media/variable-explorer-window.png)

Pokud máte v relaci definovaný složitější datový snímek R, můžete přejít do dat. Například po `cars <- mtcars` spuštění můžete procházet datovou sadou rozbalením různých uzlů v **Průzkumníku proměnných**:

![Rozšířené zobrazení Průzkumníka proměnných](media/variable-explorer-expanded-results.png)

Chcete-li odstranit proměnné, klepněte pravým tlačítkem myši a vyberte **příkaz Odstranit**nebo vyberte proměnnou a stiskněte klávesu **Delete.**

Pozorování můžete také vyhledat v datovém rámci pomocí přírůstkového vyhledávání. Nejprve rozbalte uzly v datovém rámci, který chcete prohledat, a pak do vyhledávacího pole zadejte hledané výrazy.

## <a name="details-table-view"></a>Zobrazení podrobností (tabulka)

Vzhledem k tomu, že data jsou často tabulková, můžete zobrazit libovolný složitý datový typ jako samostatnou tabulku výběrem ikony lupy nebo kliknutím pravým tlačítkem myši a výběrem **možnosti Zobrazit podrobnosti**.

![Zobrazení tabulky Průzkumník a proměnné](media/variable-explorer-table-view.png)

Kliknutím na záhlaví sloupce seřadíte data podle sloupce (střídající se mezi vzestupně a sestupně). Podržením **klávesy Shift** a kliknutím na další sloupce přidáte tyto sloupce také k řazení. Kliknutím na sloupec bez **shift** se vrátí tezi na jeden sloupec.

Pořadí, ve kterém klepnete na záhlaví sloupců určuje pořadí, ve kterém je řazení provedeno. Například **Shift**+**klepněte na** **cyl** sloupec, pak **Shift**+**klepněte na** sloupec **mpg** dvakrát seřadit seznam pro vzestupné válce a sestupné míle na galon:

![Zobrazení tabulky řazení dat podle dvou sloupců.](media/variable-explorer-table-view-sorting.png)

Vzhledem k **tomu, že Průzkumník proměnných** a zobrazení tabulek jsou v samostatných oknech sady Visual Studio, můžete je uspořádat však chcete pro práci vedle sebe. Obecné pokyny najdete [v tématu Přizpůsobení rozložení oken v sadě Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otevřít v Excelu (nebo jiné aplikaci podporující CSV)

Pro další manipulaci a analýzu je často užitečné exportovat proměnné relace do csv. Export se provádí pomocí malé![ikony aplikace](media/variable-explorer-excel-icon.png)Excel ( ikona exportu aplikace Excel ) vedle každého uzlu v **Průzkumníku proměnných**nebo kliknutím pravým tlačítkem myši na položku a výběrem **možnosti Otevřít v aplikaci CSV**. Výběrem ikony zapíšete data do nového souboru CSV ve složce *%userprofile%\Documents\RTVS_CSV_Exports* a poté tento soubor spustí, který jej otevře v libovolné aplikaci přidružené k příponě *.csv.*

## <a name="scopes"></a>Obory

Ve výchozím nastavení **se Průzkumník proměnných** otevře do globálního oboru. Do oboru balíčku můžete přepnout výběrem balíčku z rozevíracího souboru v horní části okna.

![Průzkumník proměnných zobrazující obor balíčku](media/variable-explorer-package-scopes.png)

Můžete také přepnout na rozsah funkce při zastavení na zarážky v ladicím programu (všimněte si, že **Průzkumník proměnných** automaticky nepřepne na rozsah funkce kódu, který je laděn):

![Průzkumník proměnných zobrazující datový rámec během ladění](media/variable-explorer-as-locals-window.png)

**Průzkumník proměnných** automaticky změní rozsah funkce při procházení kódu v ladicím programu, například zobrazení místních proměnných ve funkci.

## <a name="import-data-into-variable-explorer"></a>Import dat do Průzkumníka proměnných

Dva příkazy na panelu nástrojů **Průzkumník proměnných,** které jsou také k dispozici prostřednictvím nabídky**Data** **nástrojů** > R, importují externí datové sady CSV do relace R: **Importdatové sady do relace R z webové adresy URL** a **Importovat datovou sadu do relace R z textového souboru**.

Po identifikaci souboru CSV k importu visual studio zobrazí dialogové okno **importdatové sady,** ve kterém máte možnosti řídit, jak je tento datový soubor analyzován (to znamená, co je oddělovač pole a jak zpracovat uvozovky). Můžete také zobrazit náhled importovaného datového rámce a původního datového souboru:

![Dialogové okno Importovat datovou sadu](media/variable-explorer-import-dataset-dialog.png)
