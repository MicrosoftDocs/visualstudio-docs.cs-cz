---
title: Analýza porušení pravidel mezních hodnot v zátěžových testech
description: Naučte se, jak zobrazit porušení mezních pravidel, která jste nastavili, abyste mohli analyzovat porušení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 519a908b85c6cdf3dbecc38e032d72ac223a8bdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948046"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analýza porušení pravidel mezních hodnot v zátěžových testech pomocí analyzátoru zátěžového testu

Prahová pravidla jsou spojena s konkrétními čítači výkonu a porušení označují, že čítač výkonu překročil nebo poklesl pod nastavenou hodnotou. Při spuštění zátěžového testu můžete analyzovat porušení, ke kterým dojde, pro prahová pravidla, která jste nastavili dříve.

V případě, že došlo k narušení, na stavovém řádku **analyzátoru zátěžového testu** se zobrazí hypertextový odkaz **porušení mezních hodnot** a určuje počet narušení, ke kterým došlo. Kliknutím na hypertextový odkaz zobrazíte tabulku porušení mezních hodnot. Můžete také zobrazit překročení mezních hodnot v okně **čítače** a v grafu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Zobrazit porušení mezních hodnot v tabulce

V tabulce porušení mezních hodnot se zobrazí prvních 1 000 porušení. Následující tabulka obsahuje tyto sloupce:

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|Čas|Čas průběhu zátěžového testu, u kterého došlo k porušení.|Ano|
|Počítač|Název testovaného počítače, na kterém došlo k porušení. **Poznámka:**  To je důležité při spuštění zátěžových testů na plošinách.|Ano|
|Kategorie|Kategorie čítače výkonu, na kterých došlo k porušení.|Ano|
|Čítač|Název čítače výkonu, na kterém došlo k narušení.|Ano|
|Instance|Instance čítače výkonu, na které došlo k porušení.|Ano|
|Zpráva|Zpráva, která popisuje porušení prahové hodnoty. Například **hodnota 5 překračuje kritickou prahovou hodnotu 0**.|Ano|

> [!NOTE]
> Tabulku můžete seřadit výběrem záhlaví sloupců.

Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Zobrazení porušení mezních hodnot na panelu čítačů

Můžete zobrazit porušení mezních hodnot na panelu **čítače** ve stromové struktuře, která obsahuje čítače výkonu pro zátěžový test. Ikony na panelu **čítače** komunikují překročení prahových hodnot. Ikona bude mít jednu z těchto možností:

Ikona bude mít jednu z těchto možností:

![Bez narušení prahové hodnoty](../test/media/icon_ltest_1.gif) Bez narušení prahové hodnoty.

![Kritické porušení prahové hodnoty v posledním intervalu](../test/media/icon_ltest_2.gif) V posledním intervalu došlo k kritickému narušení prahové hodnoty.

![Kritické porušení prahové hodnoty v předchozím intervalu](../test/media/icon_ltest_3.gif) V předchozím intervalu došlo k narušení kritické prahové hodnoty.

![Porušení prahové hodnoty upozornění v posledním intervalu](../test/media/icon_ltest_4.gif) V posledním intervalu došlo k narušení prahové hodnoty upozornění.

![Porušení prahové hodnoty upozornění v předchozím intervalu](../test/media/icon_ltest_5.gif) V předchozím intervalu došlo k narušení prahové hodnoty upozornění.

V případě potřeby lze také v grafu zobrazit porušení mezních hodnot. V grafu vedle datového bodu, ve kterém došlo k překročení prahové hodnoty, se zobrazí ikona prahová hodnota.

Ve stromové struktuře čítače je ikona pro porušení prahové hodnoty rozšířena z konkrétního uzlu čítače až do kořenového uzlu. To vás upozorní na porušení čítače, které nemusí být viditelné ve stromové struktuře, protože strom nebyl rozbalen.

## <a name="view-threshold-violations-on-the-graph"></a>Zobrazit v grafu překročení mezních hodnot

V grafu můžete zobrazit překročení mezních hodnot. Podobně jako na panelu **čítače** jsou ikony sdělování porušení mezních hodnot v grafu. Ikony se zobrazí v grafu vedle datového bodu, ve kterém došlo k překročení prahové hodnoty. Pokud dojde k porušení prahové hodnoty u čítače, který se v grafu nezobrazí, můžete ho přidat do grafu přetažením z panelu **čítačů** do grafu.

Další informace naleznete v tématu [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také

- [Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
