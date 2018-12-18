---
title: Práce s daty metrik kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ca9d384b8c7b6d49e44826c65a156d715baa0786
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775885"
---
# <a name="working-with-code-metrics-data"></a>Práce s daty metrik kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Výsledků metrik kódu** okně se zobrazí data, která je vygenerován nástrojem analýza kódu metriky. Další informace o hodnoty dat metrik kódu najdete v tématu [hodnoty metrik kódu](../code-quality/code-metrics-values.md).  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Okno výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Zobrazení výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtrování výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Přidání, odebrání a změna uspořádání dat sloupců](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Kopírování dat do schránky nebo aplikace Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Vytváření pracovních položek na základě výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Okno výsledků metrik kódu  
 **Výsledků metrik kódu** okno s panelem nástrojů v horní a sloupce, které chcete zobrazit vypočtené výsledky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**hierarchie**|**Hierarchie** sloupec obsahuje strom hierarchie kódu, které můžete rozbalit nebo sbalit úroveň podrobností, které chcete zobrazit. Zbývající sloupce zobrazení počítané výsledky. Můžete skrýt nebo chcete uspořádat sloupce výsledku.|  
|**udržovatelnosti**|**Udržovatelnosti** sloupec obsahuje ikonu kromě číselného výsledku. Zelená ikona značí relativně vysoký stupeň udržovatelnost. Žluté ikony označuje střední stupeň udržovatelnost. Červená ikona označuje nízkou udržovatelnost a potenciální potíže s místě. Tyto indikátory barva odpovídají kategorií závažnosti, které jsou používány AvoidUnmaintainableCode pravidlo FxCop. Toto pravidlo je vyvoláno chybu, pokud je index udržovatelnosti nižší než 10, upozornění, pokud je index mezi 10 a 20 a chyby ani upozornění, pokud je vyšší než 20 index. Index udržovatelnosti je syntézu tří metrik: cyklomatická složitost řádků kódu a výpočetní složitost. Jeho hodnoty nejsou vyjádřena v jednotkách.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Zobrazení výsledků metrik kódu  
 Při generování výsledků metrik kódu se automaticky zobrazí okno výsledků metrik kódu. Kdykoli můžete také zobrazit okna.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Chcete-li zobrazit okno výsledků metrik kódu  
  
-   Na **analyzovat** nabídky, klikněte na tlačítko **Windows** a potom klikněte na tlačítko **výsledků metrik kódu**.  
  
     \- nebo –  
  
-   Na **zobrazení** nabídky, přejděte k **ostatní Windows** a potom klikněte na tlačítko **výsledků metrik kódu**.  
  
     I v případě, že neobsahuje žádné výsledky, zobrazí se okno výsledků metrik kódu.  
  
#### <a name="to-view-code-metrics-details"></a>Chcete-li zobrazit podrobnosti metrik kódu  
  
-   Pokud byly vytvořeny výsledky metrik kódu, rozbalte ve stromu v **hierarchie** sloupce.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Filtrování výsledků metrik kódu  
 Můžete filtrovat výsledky, které jsou zobrazeny v **výsledků metrik kódu** pomocí panelu nástrojů v horní části okna. Například můžete chtít zobrazit pouze výsledky, které mají index udržovatelnosti pod 65.  
  
 **Filtr** rozevírací seznam obsahuje názvy sloupců výsledky. Když je definována filtr, přidá se do dolní části seznamu spolu s odsazení. Seznam může obsahovat posledních deset filtry, které byly definovány.  
  
#### <a name="to-filter-the-code-metrics-results"></a>K filtrování výsledků metrik kódu  
  
1.  Z **filtr** seznamu, vyberte název sloupce.  
  
2.  V **Min**, zadejte minimální hodnotu, který se má zobrazit.  
  
3.  V **maximální**, zadejte maximální hodnotu, který se má zobrazit.  
  
4.  Klikněte na tlačítko **použít filtr** tlačítko.  
  
5.  Pokud chcete zobrazit podrobnosti výsledku, rozbalte stromovou strukturu hierarchie.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Přidání, odebrání a změna uspořádání dat sloupců  
 Můžete přidat nebo odebrat výsledky ze sloupce **výsledků metrik kódu** okna. Kromě toho můžete změnit uspořádání sloupců výsledky tak, aby byly zobrazeny v pořadí, ve kterém chcete.  
  
#### <a name="to-remove-a-column"></a>Pokud chcete odebrat sloupec  
  
1.  Klikněte na tlačítko **Přidat/odebrat sloupce** tlačítko.  
  
     \- nebo –  
  
     Klikněte pravým tlačítkem na záhlaví libovolného sloupce a potom klikněte na tlačítko **Přidat/odebrat sloupce**.  
  
2.  V **Přidat/odebrat sloupce** dialogové okno, zrušte zaškrtnutí políčka pro sloupce, které chcete odebrat a pak klikněte na tlačítko **OK**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Chcete-li přidat dříve odebrané sloupce  
  
1.  Klikněte na tlačítko **Přidat/odebrat sloupce** tlačítko.  
  
     \- nebo –  
  
     Klikněte pravým tlačítkem na záhlaví libovolného sloupce a potom klikněte na tlačítko **Přidat/odebrat sloupce**.  
  
2.  V **Přidat/odebrat sloupce** dialogového okna, vyberte zaškrtávací políčko pro sloupec, který chcete přidat a potom klikněte na tlačítko **OK**.  
  
#### <a name="to-rearrange-columns"></a>Chcete-li změnit uspořádání sloupců  
  
1.  Klikněte na tlačítko **Přidat/odebrat sloupce** tlačítko.  
  
     \- nebo –  
  
     Klikněte pravým tlačítkem na záhlaví libovolného sloupce a potom klikněte na tlačítko **Přidat/odebrat sloupce**.  
  
2.  V **Přidat/odebrat sloupce** dialogového okna, vyberte sloupec, který chcete přesunout a potom klikněte na šipku nahoru nebo šipku dolů.  
  
3.  Když sloupec je umístěn, kam chcete, klikněte na tlačítko **OK**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Kopírování dat do schránky nebo aplikace Excel  
 Můžete vybrat a kopírovat vybraného řádku dat metrik kódu do schránky jako textový řetězec, který obsahuje jeden řádek pro název a hodnotu každého sloupce data. Můžete také kliknout na **Otevřít seznam v aplikaci Microsoft Excel** exportovat všechny výsledky metrik kódu do Excelové tabulky  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Vytváření pracovních položek na základě výsledků metrik kódu  
 Můžete vytvořit [!INCLUDE[esprfound](../includes/esprfound-md.md)] pracovní položku, která je založena na vede **výsledků metrik kódu** okno. Při vytvoření pracovní položky [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky zadá název **název** pole a kód dat metrik v části **historie** kartu.  
  
 Další informace o tom, jak vytvořit pracovní položky, naleznete v tématu [vytvořit pracovní položku &#91;přesměrováno&#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Chcete-li vytvořit pracovní položku podle výsledku  
  
1.  Klikněte pravým tlačítkem na výsledek.  
  
2.  Přejděte na **vytvořit pracovní položku**a potom klikněte na typ pracovní položky, kterou chcete vytvořit (**chyb**, **úloh**a tak dále).  
  
3.  Vyplňte formulář pracovní položky vyplnění všech povinných polích.  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** k uložení pracovní položky.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Vytvořit chybu na základě výsledku  
  
1.  Klikněte na výsledek a vyberte ji.  
  
2.  Klikněte na tlačítko **vytvořit pracovní položku** tlačítko.  
  
3.  Vyplňte formulář pracovní položky vyplnění všech povinných polích.  
  
4.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** k uložení pracovní položky.  
  
## <a name="see-also"></a>Viz také  
 [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Postupy: Vygenerování dat metrik kódu](../code-quality/how-to-generate-code-metrics-data.md)



