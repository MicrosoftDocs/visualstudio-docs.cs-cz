---
title: Přidání a odstranění čítačů pro grafy ve výsledcích zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acb08edf74d3ca35a2449f588976681d679caeb4
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115188"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Postupy: Přidání a odstranění čítačů pro grafy ve výsledcích zátěžového testu

Můžete použít **čítače** panel k přidání čítačů výkonu do grafu.

![Přidání čítačů do grafu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Aspekty Interval vzorkování čítače výkonu**

Zvolte hodnotu **vzorkovací frekvence** vlastnost v zátěžovém testu běhu na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pěti sekund, vyžaduje více místa v databázi výsledků zátěžového testu. Pro delší zátěžové testy vzorkovací frekvence snižuje množství dat, která shromažďujete. Další informace najdete v tématu [postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Zde jsou uvedeny pokyny pro vzorkovací frekvence:

|Doba trvání zátěžového testu|Doporučená frekvence vzorkování|
|-|-----------------------------|
|\< 1 hodina|5 sekund|
|1 - 8 hodin|15 sekund|
|8 - 24 hodin|30 sekund|
|> 24 hodin|60 sekund|

**Důležité informace týkající se včetně podrobnosti časování pro shromažďování dat**

V nastavení testu v editoru zátěžových testů s názvem existuje vlastnost **úložiště podrobností časování**. Pokud **úložiště podrobností časování** vlastnost je povolená, pak čas ke spuštění každé jednotlivé testy, transakce a stránky během zátěžového testu uložen v úložišti výsledků zátěžového testu. To umožňuje 90. percentil. a 95. percentil dat zobrazený v **Analyzéru zátěžového testu** v tabulkách testy, transakce a stránky.

Existují dvě volby pro povolení **úložiště podrobností časování** vlastnosti v vlastností parametrů spuštění s názvem **StatisticsOnly** a **AllIndividualDetails**. Obě možnosti všechny individuální testy, stránky a transakce jsou časovány a data percentilu se vypočtou z jednotlivých dat časování. Rozdíl je, že u **StatisticsOnly** ihned poté, co byla vypočtena data pro percentil, možnost jednotlivá časová data odstraněna z úložiště. To snižuje množství místa potřebné v úložišti použijete podrobnosti časování. Pokročilí uživatelé mohou však chtít zpracovat podrobná data časování jiným způsobem, pomocí nástroje SQL. Pokud tomu tak, **AllIndividualDetails** by měl být použit, tak, aby podrobná data časování byla k dispozici pro zpracování. Navíc pokud nastavíte vlastnost na **AllIndividualDetails**, pak lze analyzovat aktivity virtuálního uživatele pomocí **aktivity virtuálního uživatele** graf **Analyzéru zátěžového testu** po dokončení zátěžového testu. Další informace najdete v tématu [analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Množství místa potřebné v úložišti výsledků zátěžového testu k ukládání dat s podrobnosti časování může být značné, zejména pro delší zkoušky zatížení. Také čas pro ukládání těchto dat v úložišti výsledků zátěžového testu na konci zátěžového testu je delší, protože tato data jsou uložena v agentech zátěžového testu, dokud zátěžový test neskončí. Po dokončení zátěžového testu jsou data uložena do úložiště. Ve výchozím nastavení **úložiště podrobností časování** je povolena vlastnost. Pokud je to problém pro testovací prostředí, můžete chtít nastavit **úložiště podrobností časování** k **žádný**.

Další informace najdete v tématu [postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Chcete-li zobrazit konkrétního čítače výkonu v grafu zátěžového testu

1. Po dokončení zátěžového testu nebo po načtení výsledků testu v Analyzéru zátěžového testu na panelu nástrojů, zvolte **grafy**.

     **Čítače** panelu se zobrazí v zobrazení grafů.

    > [!NOTE]
    > Pokud **čítače** panelu není zobrazen, zvolte **zobrazit Panel čítačů** na panelu nástrojů.

2. V **čítače** panelu, rozbalte uzly v hierarchii, dokud nenajdete, kterou chcete zobrazit graficky čítače výkonu.

     Například pokud chcete zobrazit dostupné paměti v počítači, ve kterém jsou testy spuštěny, rozbalte **počítače**, rozbalte uzel pro počítač a potom rozbalte **paměti**. Zobrazí se **počet MB k dispozici** čítače.

3. Vyberte graf, na kterém chcete zobrazit čítače výkonu.

4. Pravým tlačítkem myši na čítač výkonu v **čítače** panelu a vyberte **zobrazit čítač v grafu**.

    > [!TIP]
    > Dočasné zastavení, zobrazení dat čítače výkonu v grafu, zrušte zaškrtnutí políčka pro čítač výkonu v legendě. To umožňuje statistiky minimum, Maximum a průměr stále analyzovat bez zobrazení trendovou linii do grafu. To může být užitečné, pokud graf obsahuje několik překrývající se vykreslení čítače výkonu při analýze problémy. Další informace najdete v tématu [použití legendy zobrazení grafů k analýze zátěžových testů](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Z grafu odebrat data čítače výkonu, pravým tlačítkem myši na čítač výkonu v **čítač** sloupce legendy a vyberte **odstranit**.

     \- nebo –

     Klikněte pravým tlačítkem na řádek dat v grafu a výběr **odstranit**.

     \- nebo –

     Zvolte čítače výkonu ve **čítač** sloupce legendy nebo data řádku v grafu a potom stiskněte klávesu **odstranit** klíč.

    > [!NOTE]
    > Můžete také umístit v legendě, ale ne na graf čítače výkonu pomocí **přidat čítač v legendě** příkazu.

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Postupy: vytváření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)
