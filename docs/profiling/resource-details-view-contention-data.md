---
title: Zobrazení podrobností o zdroji – data konfliktů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e66432fd2f5d8b1532bece9d76e7dfc2a261e4b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771587"
---
# <a name="resource-details-view---contention-data"></a>Zobrazení podrobností o prostředku – data kolizí
Zobrazení Podrobnosti o prostředku představuje graf časové osy blokování událostí, které byly způsobeny konflikty nad vybraným zdrojem. Blokování událost nastane, když vlákno je nucenpozastavit spuštění, protože jiné vlákno má uzamčen přístup k prostředku.

 Toto zobrazení představuje časovou osu provádění každého vlákna jako vodorovný pruh a představuje každou událost blokování jako svislý pruh na časové ose vlákna. V případě potřeby můžete zvětšit část časové osy a zobrazit jednotlivé události. Chcete-li zobrazit cestu spuštění (zásobník volání) funkcí, které vedly k události, klikněte na panel událostí. Funkce se zobrazí v okně **Zásobník volání.** Pokud je k dispozici zdrojový kód funkce, můžete klepnutím na název funkce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]upravit zdrojový soubor v rozhraní pro aplikaci .

## <a name="procedures"></a>Procedury

#### <a name="to-magnify-a-timeline-segment"></a>Zvětšení segmentu časové osy

- Přetáhněte ukazatel myši přes oblast časové osy.

     Když uvolníte tlačítko myši, zobrazení se přiblíží k vybranému časovému segmentu. Proces můžete zopakovat, abyste segment dále zvětšili. Posuvník na posuvníku času představuje relativní velikost časového segmentu, který se zobrazí v zobrazení.

#### <a name="to-zoom-out-on-a-timeline"></a>Oddálení na časové ose

- Proveďte jeden z následujících kroků:

  - Kliknutím na **Oddálit** se vrátíte na předchozí úroveň přiblížení.

  - Kliknutím na **Reset lupy** zobrazíte celou časovou osu v zobrazení.

#### <a name="to-view-the-call-stack-of-an-event"></a>Zobrazení zásobníku volání události

- V grafu časové osy klikněte na panel událostí.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Zobrazení nebo úprava zdrojového kódu funkce v zásobníku volání

- V okně **Zásobník volání** klikněte na název funkce.

  Zdrojový kód funkce musí být součástí aktuálního projektu.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Zobrazení stromu volání konfliktních událostí pro prostředek

- V grafu časové osy klikněte na **Součet**.

     Zobrazí se zobrazení Tvrzení pro prostředek. Další informace naleznete v tématu [Zobrazení konfliktů prostředků](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Zobrazení všech konfliktních událostí vlákna

- V grafu časové osy klikněte na název nebo ID vlákna.

     Zobrazí se pro vybrané vlákno zobrazení podrobností vlákna. Další informace naleznete v [tématu Thread Details View](../profiling/thread-details-view-contention-data.md).
