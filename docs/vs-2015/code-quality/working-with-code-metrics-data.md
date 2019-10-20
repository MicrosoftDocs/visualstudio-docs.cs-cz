---
title: Práce s daty metrik kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645709"
---
# <a name="working-with-code-metrics-data"></a>Práce s daty metrik kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **Výsledky metrik kódu** zobrazuje data generovaná analýzou metrik kódu. Další informace o hodnotách dat metrik kódu naleznete v tématu [hodnoty metrik kódu](../code-quality/code-metrics-values.md).

 Toto téma obsahuje následující oddíly:

- [Okno výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Zobrazení výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtrování výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Přidání, odebrání a změna uspořádání datových sloupců](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Kopírování dat do schránky nebo Excelu](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Vytvoření pracovní položky na základě výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="BKMK_CodeMetricsResultsWindow"></a>Okno výsledků metrik kódu
 Okno **výsledků metriky kódu** má panel nástrojů v horní části a sloupce pro zobrazení počítaných výsledků.

|Kolo|Popis|
|------------|-----------------|
|**Hierarchie**|Sloupec **Hierarchy** obsahuje stromové zobrazení hierarchie kódu, které můžete rozbalit nebo sbalit a zobrazit požadovanou úroveň podrobností. Zbývající sloupce znázorňují počítané výsledky. Sloupce výsledků můžete podle potřeby skrýt nebo uspořádat.|
|**Udržovatelnost**|Sloupec **udržovatelnosti** obsahuje kromě číselného výsledku i ikonu. Zelená ikona indikuje poměrně vysokou míru udržovatelnosti. Žlutá ikona indikuje střední stupeň udržovatelnosti. Červená ikona označuje nízkou udržovatelnost a potenciální problémové místo. Tyto barevné indikátory odpovídají kategoriím závažnosti, které používá pravidlo FxCop AvoidUnmaintainableCode. Toto pravidlo vyvolá chybu, pokud je index udržovatelnosti menší než 10, upozornění, pokud je index mezi 10 a 20, a ani chyba, ani upozornění, pokud je index vyšší než 20. Index udržovatelnosti je souhrn tří metrik: Cyklomatická složitost, řádky kódu a výpočetní složitost. Hodnoty nejsou vyjádřeny v jednotkách.|

## <a name="BKMK_DisplayingCodeMetricsResults"></a>Zobrazení výsledků metrik kódu
 Okno Výsledky metrik kódu se zobrazí automaticky při generování výsledků metrik kódu. Okno můžete také kdykoli zobrazit.

#### <a name="to-display-the-code-metrics-results-window"></a>Zobrazení okna výsledků metrik kódu

- V nabídce **analyzovat** klikněte na **Windows** a pak klikněte na **Výsledky metrik kódu**.

     \- nebo-

- V nabídce **zobrazení** přejděte na položku **ostatní okna** a klikněte na příkaz **Výsledky metrik kódu**.

     Okno Výsledky metrik kódu se zobrazí i v případě, že neobsahuje žádné výsledky.

#### <a name="to-view-code-metrics-details"></a>Zobrazení podrobností o metrikách kódu

- Pokud byly vygenerovány Výsledky metrik kódu, rozbalte strom ve sloupci **hierarchie** .

## <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrování výsledků metrik kódu
 Výsledky, které se zobrazí v okně **výsledků metrik kódu** , můžete filtrovat pomocí panelu nástrojů v horní části. Například můžete chtít zobrazit pouze výsledky, které mají index udržovatelnosti pod 65.

 Rozevírací seznam **filtru** obsahuje názvy sloupců výsledků. Když je definovaný filtr, přidá se do dolní části seznamu spolu s odsazením. Seznam může obsahovat posledních deset filtrů, které byly definovány.

#### <a name="to-filter-the-code-metrics-results"></a>Filtrování výsledků metrik kódu

1. V seznamu **Filtr** vyberte název sloupce.

2. V poli **min**zadejte minimální hodnotu, která se má zobrazit.

3. V poli **Max**(maximální) zadejte maximální hodnotu, která se má zobrazit.

4. Klikněte na tlačítko **použít filtr** .

5. Chcete-li zobrazit podrobnosti výsledku, rozbalte strom hierarchie.

## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Přidání, odebrání a změna uspořádání datových sloupců
 Můžete přidat nebo odebrat sloupce výsledků z okna **výsledků metrik kódu** . Kromě toho můžete změnit uspořádání sloupců výsledků tak, aby se zobrazily v pořadí, které chcete.

#### <a name="to-remove-a-column"></a>Odebrání sloupce

1. Klikněte na tlačítko **Přidat nebo odebrat sloupce** .

     \- nebo-

     Klikněte pravým tlačítkem na záhlaví sloupce a pak klikněte na **Přidat nebo odebrat sloupce**.

2. V dialogovém okně **Přidat nebo odebrat sloupce** zrušte zaškrtnutí políčka u sloupce, který chcete odebrat, a poté klikněte na tlačítko **OK**.

#### <a name="to-add-a-previously-removed-column"></a>Přidání dříve odebraného sloupce

1. Klikněte na tlačítko **Přidat nebo odebrat sloupce** .

     \- nebo-

     Klikněte pravým tlačítkem na záhlaví sloupce a pak klikněte na **Přidat nebo odebrat sloupce**.

2. V dialogovém okně **Přidat nebo odebrat sloupce** zaškrtněte políčko u sloupce, který chcete přidat, a poté klikněte na tlačítko **OK**.

#### <a name="to-rearrange-columns"></a>Změna uspořádání sloupců

1. Klikněte na tlačítko **Přidat nebo odebrat sloupce** .

     \- nebo-

     Klikněte pravým tlačítkem na záhlaví sloupce a pak klikněte na **Přidat nebo odebrat sloupce**.

2. V dialogovém okně **Přidat nebo odebrat sloupce** vyberte sloupec, který chcete přesunout, a potom klikněte buď na šipku nahoru, nebo na šipku dolů.

3. Když je sloupec umístěn tam, kde chcete, klikněte na tlačítko **OK**.

## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Kopírování dat do schránky nebo Excelu
 Vybraný řádek dat metriky kódu můžete vybrat a zkopírovat do schránky jako textový řetězec, který obsahuje jeden řádek pro název a hodnotu každého sloupce dat. Můžete také kliknout na **otevřít seznam v aplikaci Microsoft Excel** a exportovat výsledky metriky kódu do excelové tabulky.

## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Vytvoření pracovní položky na základě výsledků metrik kódu
 Můžete vytvořit [!INCLUDE[esprfound](../includes/esprfound-md.md)] pracovní položku, která je založena na výsledcích v okně **výsledků metrik kódu** . Při vytvoření pracovní položky [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky zadá název do pole **název** a data metriky kódu na kartě **Historie** .

 Další informace o tom, jak vytvořit pracovní položky, naleznete v tématu [Vytvoření přesměrované &#91;&#93;pracovní položky](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Vytvoření pracovní položky na základě výsledku

1. Klikněte pravým tlačítkem na výsledek.

2. Přejděte na **vytvořit pracovní položku**a potom klikněte na typ pracovní položky, kterou chcete vytvořit (**Chyba**, **úkol**a tak dále).

3. Vyplňte formulář pracovní položky vyplněním všech povinných polí.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte pracovní položku.

#### <a name="to-create-a-bug-based-on-a-result"></a>Vytvoření chyby na základě výsledku

1. Kliknutím vyberte výsledek.

2. Klikněte na tlačítko **vytvořit pracovní položku** .

3. Vyplňte formulář pracovní položky vyplněním všech povinných polí.

4. V nabídce **soubor** klikněte na **Uložit vše** a uložte pracovní položku.

## <a name="see-also"></a>Viz také
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [Postupy: generování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)
