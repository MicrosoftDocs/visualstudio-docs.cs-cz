---
title: Analýza porušení pravidel prahové hodnoty v zátěžových testech
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591278"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analýza porušení pravidel prahové hodnoty v zátěžových testech pomocí analyzátoru zátěžového testu

Prahová hodnota pravidla jsou spojeny s konkrétní čítače výkonu a porušení označují, že čítač výkonu překročena nebo klesla pod nastavenou hodnotu. Při spuštění zátěžového testu můžete analyzovat porušení, ke kterým dochází pro pravidla prahové hodnoty, která jste nastavili dříve.

Pokud došlo k porušení, na stavovém řádku **analyzátoru zátěžového testu** se zobrazí hypertextový odkaz **překročení prahové hodnoty** a určuje počet porušení, ke kterým došlo. Zvolíte-li hypertextový odkaz, zobrazíte tabulku porušení prahové hodnoty. Můžete také zobrazit porušení prahové hodnoty v okně **Čítače** a v grafu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Zobrazit porušení prahové hodnoty v tabulce

Tabulka porušení prahové hodnoty zobrazuje prvních 1 000 porušení. Následující tabulka obsahuje tyto sloupce:

|Sloupec|Popis|Viditelné ve výchozím nastavení|
|-|-|-|
|Time|Čas během zátěžového testu, při kterém došlo k porušení.|Ano|
|Počítač|Název testovce počítače, na kterém došlo k porušení. **Poznámka:**  To je důležité při spuštění zátěžových testů na plošinách.|Ano|
|Kategorie|Kategorie čítače výkonu, na kterém došlo k porušení.|Ano|
|Čítač|Název čítače výkonu, na kterém došlo k porušení.|Ano|
|Instance|Instance čítače výkonu, na kterém došlo k porušení.|Ano|
|Zpráva|Zpráva popisující porušení prahové hodnoty. **Například Hodnota 5 překračuje kritickou prahovou hodnotu 0**.|Ano|

> [!NOTE]
> Tabulku můžete seřadit výběrem záhlaví sloupců.

Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Zobrazit porušení prahové hodnoty v panelu Čítače

Porušení prahové hodnoty můžete zobrazit v panelu **Čítače** ve stromu, který obsahuje čítače výkonu pro zátěžový test. Ikony v panelu **Čítače** komunikují porušení prahové hodnoty. Ikona bude jedna z následujících:

Ikona bude jedna z následujících:

![Žádné porušení prahové hodnoty](../test/media/icon_ltest_1.gif) Žádné porušení prahové hodnoty.

![Závažné porušení prahové hodnoty v posledním intervalu](../test/media/icon_ltest_2.gif) V posledním intervalu došlo k porušení kritické prahové hodnoty.

![Závažné porušení prahové hodnoty v předchozím intervalu](../test/media/icon_ltest_3.gif) V předchozím intervalu došlo k závažnému porušení prahové hodnoty.

![Porušení prahové hodnoty upozornění v posledním intervalu](../test/media/icon_ltest_4.gif) V posledním intervalu došlo k porušení prahové hodnoty upozornění.

![Porušení prahové hodnoty upozornění v předchozím intervalu](../test/media/icon_ltest_5.gif) Porušení prahové hodnoty upozornění došlo v předchozím intervalu.

Volitelně lze porušení prahové hodnoty zobrazit také v grafu. V grafu vedle datového bodu, kde došlo k porušení prahové hodnoty, se zobrazí ikona prahové hodnoty.

Ve stromu čítačů je ikona pro porušení prahové hodnoty šířena z konkrétního uzlu čítače až do kořenového uzlu. To vás upozorní na porušení na čítači, které nemusí být viditelné ve stromu, protože strom nebyl rozbalen.

## <a name="view-threshold-violations-on-the-graph"></a>Zobrazit porušení prahové hodnoty v grafu

V grafu můžete zobrazit porušení prahové hodnoty. Podobně jako u panelu **Čítače** ikony komunikují porušení prahových hodnot v grafu. Ikony se zobrazí v grafu vedle datového bodu, kde došlo k porušení prahové hodnoty. Pokud dojde k porušení prahové hodnoty na čítači, který se v grafu nezobrazuje, můžete jej přidat do grafu přetažením z panelu **Čítače** do grafu.

Další informace naleznete [v tématu Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také

- [Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
