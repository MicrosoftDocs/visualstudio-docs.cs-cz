---
title: Průzkumník proměnných pro R
description: Průzkumník proměnných v sadě Visual Studio zobrazuje všechny proměnné v daném oboru v aktuální relaci jazyka R:.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: fbd20c362c407148262d8e1e61e15d22d9cbcf2f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978122"
---
# <a name="variable-explorer"></a>Průzkumník proměnných

**Průzkumníka proměnných** okno otevřít pomocí **nástroje R** > **Windows** > **Průzkumníka proměnných** (nebo **Ctrl**+**8** Pokud jste použili **nástroje R** > **nastavení pro datové vědy**), zobrazí všechny proměnné v daném oboru v aktuální relaci jazyka R: Například, pokud otevřete **Průzkumníka proměnných** a zadejte následující řádky [interaktivní okno](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**Průzkumníka proměnných** zobrazí se okno následujícím způsobem:

![Okno Průzkumníka proměnných v sadě Visual Studio](media/variable-explorer-window.png)

Pokud máte složitější datového rámce R, který je definovaný v relaci, můžete přejít k datům. Například po spuštění `cars <- mtcars` datovou sadu můžete procházet tak, že rozbalíte různé uzly v **Průzkumníka proměnných**:

![Rozšířené zobrazení Průzkumníka proměnných](media/variable-explorer-expanded-results.png)

Odstranění proměnných, klikněte pravým tlačítkem a vyberte **odstranit**, nebo vyberte proměnnou a stiskněte klávesu **odstranit** klíč.

Můžete také vyhledat hodnotu v datovém rámci Přírůstkové hledání. Nejprve rozbalte uzly v rámci dat, který chcete vyhledat a pak do vyhledávacího pole zadejte hledaný text.

## <a name="details-table-view"></a>Zobrazení podrobností (tabulka)

Protože je často tabulkových dat, můžete zobrazit libovolný typ komplexní data jako do samostatné tabulky výběrem ikony lupy nebo kliknete pravým tlačítkem a výběrem **zobrazit podrobnosti**.

![Zobrazení tabulky proměnných Průzkumníka](media/variable-explorer-table-view.png)

Kliknutím na záhlaví sloupce seřadí data podle sloupce (přepínání mezi vzestupným a sestupným). Podržte **Shift** a kliknutím na další sloupce přidá tyto sloupce pro řazení i. Kliknutím na sloupec bez **Shift** vrátí do jednoho sloupce řazení.

Pořadí, ve kterém můžete klepnutím na záhlaví sloupce určuje pořadí, ve kterém se provádí při řazení. Například **Shift**+**klikněte na tlačítko** **cyl** sloupec, pak **Shift**+**klikněte na tlačítko** **mpg** sloupce seřadíte seznam pro cylindrů vzestupným a sestupným mil za paliva dvakrát:

![Zobrazení tabulky dat řazení podle dva sloupce.](media/variable-explorer-table-view-sorting.png)

Protože **Průzkumníka proměnných** a zobrazení tabulek jsou v samostatných okna sady Visual Studio, můžete je uspořádat ale potřebujete pro práci vedle sebe. Zobrazit [přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) obecné pokyny.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otevřít v aplikaci Excel (nebo jiné aplikace podporující sdíleného svazku clusteru)

Pro další zpracování a analýzu často je užitečné pro export proměnné relace do sdíleného svazku clusteru. Export se provádí pomocí malá ikona Excelu (![ikonu exportu Excel](media/variable-explorer-excel-icon.png)) vedle každého uzlu v **Průzkumníka proměnných**, nebo kliknutím pravým tlačítkem myši na položku a výběrem **otevřít v aplikaci sdíleného svazku clusteru**. Vyberte ikonu zapisuje data do nového souboru CSV v *%userprofile%\Documents\RTVS_CSV_Exports* složku a potom spustí je přidružené k tento soubor, který se otevře v libovolné aplikace *CSV*rozšíření.

## <a name="scopes"></a>Obory

Ve výchozím nastavení **Průzkumníka proměnných** otevře pro globální obor. Obor balíčku můžete přepnout výběrem balíček z rozevíracího seznamu v horní části okna.

![Průzkumník proměnných znázorňující obor balíčku](media/variable-explorer-package-scopes.png)

Můžete také přepnout na rozsah funkce při zastavení na zarážce v ladicí program (Všimněte si, že **Průzkumníka proměnných** neznamená automatické přepnutí do oboru funkce laděného kódu):

![Průzkumník proměnných zobrazující datového rámce během ladění](media/variable-explorer-as-locals-window.png)

**Průzkumník proměnných** automaticky změny fungovat oboru tak, jak procházet kód v ladicím programu, jako je například zobrazující lokálních proměnných ve funkci.

## <a name="import-data-into-variable-explorer"></a>Import dat do Průzkumníka proměnných

Dva příkazy na **Průzkumníka proměnných** nástrojů, které jsou k dispozici prostřednictvím **nástroje R** > **Data** nabídky, externí sdílený svazek clusteru datové sady importu do vašeho jazyka R relace: **importovat datovou sadu do relace jazyka R z webové adresy URL** a **importovat datovou sadu do relace jazyka R z textového souboru**.

Jakmile identifikujete importovat soubor CSV, zobrazí Visual Studio **importovat datovou sadu** dialogové okno, ve kterém máte možnosti řídit, jak analyzovat data souboru (to znamená, co oddělovač polí je a jak bude zpracováván uvozovky). Můžete také zobrazit náhled importované datového rámce a původní datový soubor:

![Dialogové okno importu v datové sadě](media/variable-explorer-import-dataset-dialog.png)
