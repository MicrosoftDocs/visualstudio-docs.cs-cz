---
title: Analýza mezních pravidel v zátěžových testech
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a20c5e3f30a6d006175e78fc70dab79d0b9bf8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591278"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analýza mezních pravidel v zátěžových testech pomocí Analyzéru zátěžového testu

Mezní pravidla jsou přidruženy konkrétních čítačů výkonu a narušení naznačují, že čítač výkonu překročil nebo klesl pod hodnotou. Při spuštění zátěžového testu můžete analyzovat porušení pravidla prahové hodnoty, které jste dřív nastavili.

Pokud došlo k porušení zásad, **mezních hodnot** hypertextového odkazu se zobrazí na **Analyzéru zátěžového testu** stavový řádek a určuje počet porušení zásad, ke kterým došlo. Můžete zvolit hypertextový odkaz na zobrazení tabulky porušení prahové hodnoty. Můžete také zobrazit porušení prahové hodnoty v **čítače** okna a v grafu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Zobrazení překročení mezní hodnoty v tabulce

Tabulka porušení mezních hodnot zobrazí prvních 1000 porušení zásad. Následující tabulka obsahuje tyto sloupce:

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|Čas|Doba během zátěžového testu na kterém došlo k porušení zásady.|Ano|
|Computer|Název počítače v rámci testu, na kterém došlo k porušení zásady. **Poznámka:** to je důležité při spuštění zátěžových testů v skupiny testovacích počítačů.|Ano|
|Kategorie|Kategorie čítače výkonu, na kterém došlo k porušení zásady.|Ano|
|Counter|Název čítače výkonu, na kterém došlo k porušení zásady.|Ano|
|instance|Instance čítače výkonu, na kterém došlo k porušení zásady.|Ano|
|Zpráva|Zpráva popisující porušení mezní hodnoty. Například **hodnotu 5 překračuje kritickou mezní hodnotu 0**.|Ano|

> [!NOTE]
> Seřadí tabulku kliknutím na záhlaví sloupců.

Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Zobrazení překročení mezní hodnoty na panelu čítačů

Můžete zobrazit porušení prahové hodnoty v **čítače** panelu a ve stromu, který obsahuje seznam čítačů výkonu pro zátěžový test. Ikony v **čítače** panel komunikovat mezních hodnot. Ikona bude jeden z následujících akcí:

Ikona bude jeden z následujících akcí:

![Žádná porušení prahové hodnoty](../test/media/icon_ltest_1.gif) Žádná porušení mezní hodnoty.

![Porušení kritické prahové hodnoty na posledního intervalu](../test/media/icon_ltest_2.gif) Na poslední interval došlo k porušení kritické prahové hodnoty.

![Porušení kritické prahové hodnoty na předchozí interval](../test/media/icon_ltest_3.gif) V předchozí interval došlo k porušení kritické prahové hodnoty.

![Varování porušení mezní hodnoty do posledního intervalu](../test/media/icon_ltest_4.gif) Na poslední interval došlo k porušení výstražné prahové hodnoty.

![Varování porušení mezní hodnoty na předchozí interval](../test/media/icon_ltest_5.gif) V předchozí interval došlo k porušení výstražné prahové hodnoty.

Volitelně můžete překročení mezní hodnoty mohou být zobrazeny v grafu také. V grafu vedle datový bod, kde došlo k porušení mezní hodnoty se zobrazí ikona prahovou hodnotu.

Ve stromu čítačů ikonu porušení prahové hodnoty je rozšířena z uzlu konkrétní čítač, až do kořenového uzlu. To vás upozorní na porušení čítače, která nemusí být viditelná ve stromu, protože nebyla došlo k rozbalení stromu.

## <a name="view-threshold-violations-on-the-graph"></a>Zobrazení překročení prahové hodnoty v grafu

Můžete zobrazit porušení prahové hodnoty v grafu. Podobně jako **čítače** panelu komunikovat ikony překročení mezní hodnoty v grafu. Ikony se zobrazí v grafu vedle datový bod, kde došlo k porušení mezní hodnoty. Pokud dojde k narušení prahové hodnoty čítače, které nejsou uvedené v grafu, můžete přidat ho do grafu z jeho přetažením **čítače** panelu do grafu.

Další informace najdete v tématu [výsledků zátěžového testu analyzovat v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také:

- [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
