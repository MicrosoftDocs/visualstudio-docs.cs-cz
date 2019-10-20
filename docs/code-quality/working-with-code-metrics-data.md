---
title: Okno metriky kódu
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0824fe608ad1bac86ef904702bd1be907bc9ce7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648997"
---
# <a name="use-the-code-metrics-results-window"></a>Použití okna výsledků metrik kódu

Okno **Výsledky metrik kódu** zobrazuje data generovaná analýzou metrik kódu. Další informace o hodnotách dat metrik kódu naleznete v tématu [hodnoty metrik kódu](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Zobrazit výsledky metrik kódu

Okno **Výsledky metrik kódu** se zobrazí automaticky při generování výsledků metrik kódu. Okno můžete také kdykoli zobrazit.

Můžete zobrazit okno výsledků metrik kódu pomocí jedné z následujících sekvencí nabídky:

- V nabídce **analyzovat** vyberte**Výsledky metrik kódu** **Windows** > .

- V nabídce **zobrazení** vyberte jiné**Výsledky metrik kódu** **Windows** > .

Otevře se okno **výsledků metrik kódu** , a to i v případě, že neobsahuje žádné výsledky.

### <a name="to-view-code-metrics-details"></a>Zobrazení podrobností o metrikách kódu

Pokud byly vygenerovány Výsledky metrik kódu, rozbalte strom ve sloupci **hierarchie** .

## <a name="filter-code-metrics-results"></a>Filtrování výsledků metrik kódu

Výsledky, které se zobrazí v okně **výsledků metrik kódu** , můžete filtrovat pomocí panelu nástrojů v horní části. Například můžete chtít zobrazit pouze výsledky, které mají index udržovatelnosti pod 65.

Rozevírací seznam **filtru** obsahuje názvy sloupců výsledků. Když je definovaný filtr, přidá se do dolní části seznamu spolu s odsazením. Seznam může obsahovat posledních 10 filtrů, které byly definovány.

### <a name="to-filter-the-code-metrics-results"></a>Filtrování výsledků metrik kódu

1. V seznamu **Filtr** vyberte název sloupce.

2. V poli **min**zadejte minimální hodnotu, která se má zobrazit.

3. V poli **Max**(maximální) zadejte maximální hodnotu, která se má zobrazit.

4. Klikněte na tlačítko **použít filtr** .

5. Chcete-li zobrazit podrobnosti výsledku, rozbalte strom hierarchie.

## <a name="add-remove-and-rearrange-data-columns"></a>Přidat, odebrat a změnit uspořádání sloupců dat

Můžete přidat nebo odebrat sloupce výsledků z okna **výsledků metrik kódu** . Kromě toho můžete změnit uspořádání sloupců výsledků tak, aby se zobrazily v pořadí, které chcete.

### <a name="add-or-remove-a-column"></a>Přidat nebo odebrat sloupec

1. Klikněte na tlačítko **Přidat nebo odebrat sloupce** nebo klikněte pravým tlačítkem na záhlaví sloupce a potom klikněte na **Přidat nebo odebrat sloupce**.

1. V dialogovém okně **Přidat nebo odebrat sloupce** zaškrtněte nebo zrušte zaškrtnutí políčka u sloupce, který chcete přidat nebo odebrat, a pak zvolte **OK**.

### <a name="rearrange-columns"></a>Změnit uspořádání sloupců

1. Klikněte na tlačítko **Přidat nebo odebrat sloupce** .

1. V dialogovém okně **Přidat nebo odebrat sloupce** vyberte sloupec, který chcete přesunout, a pak zvolte buď šipku nahoru nebo šipka dolů.

1. Když je sloupec umístěný tam, kde chcete, klikněte na **tlačítko OK**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Kopírovat data do schránky nebo Excelu

Vybraný řádek dat metriky kódu můžete vybrat a zkopírovat do schránky jako textový řetězec, který obsahuje jeden řádek pro název a hodnotu každého sloupce dat. Můžete také kliknout na **otevřít výběr v aplikaci Microsoft Excel** a exportovat výsledky metriky kódu do excelové tabulky.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Vytvořit pracovní položku na základě výsledků metrik kódu

Můžete vytvořit [Azure boards](/azure/devops/boards/index?view=vsts) pracovní položku, která je založena na výsledcích v okně **výsledků metrik kódu** . Když je pracovní položka vytvořena, Visual Studio automaticky zadá název do pole **název** a data metriky kódu na kartě **Historie** .

Další informace o Azure Boards pracovních položek naleznete v tématu [work items](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Vytvoření pracovní položky na základě výsledku

1. Klikněte pravým tlačítkem na výsledek.

2. Přejděte na **vytvořit pracovní položku**a potom klikněte na typ pracovní položky, kterou chcete vytvořit (**Chyba**, **úkol**a tak dále).

3. Vyplňte formulář pracovní položky vyplněním všech povinných polí.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte pracovní položku.

### <a name="to-create-a-bug-based-on-a-result"></a>Vytvoření chyby na základě výsledku

1. Kliknutím vyberte výsledek.

2. Klikněte na tlačítko **vytvořit pracovní položku** .

3. Vyplňte formulář pracovní položky vyplněním všech povinných polí.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte pracovní položku.

## <a name="see-also"></a>Viz také:

- [Hodnoty metrik kódu](../code-quality/code-metrics-values.md)
- [Postupy: generování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)
