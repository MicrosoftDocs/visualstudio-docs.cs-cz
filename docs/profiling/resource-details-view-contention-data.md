---
title: Zobrazení podrobností o prostředku – data kolizí | Microsoft Docs
description: Přečtěte si, jak zobrazení detailů prostředků prezentuje graf časové osy blokujících událostí, které byly způsobeny kolizí přes vybraný prostředek.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 715742221b5d8b21f574e7fb8001bd0a3c56cef5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960205"
---
# <a name="resource-details-view---contention-data"></a>Zobrazení podrobností o prostředku – data kolizí
Zobrazení Podrobnosti o prostředku představuje graf časové osy blokujících událostí, které byly způsobeny kolizí přes vybraný prostředek. K blokující události dojde, když je vlákno nuceno pozastavit provádění, protože jiné vlákno má zamčený přístup k prostředku.

 Toto zobrazení představuje časovou osu spuštění každého vlákna jako vodorovný pruh a představuje každou blokující událost jako svislou čáru na časové ose vlákna. V případě potřeby můžete zvětšit část časové osy a zobrazit jednotlivé události. Chcete-li zobrazit cestu spuštění (zásobník volání) funkcí, které vedly k události, klikněte na panel událostí. Funkce se zobrazí v okně **zásobník volání** . Pokud je zdrojový kód funkce k dispozici, můžete kliknout na název funkce a upravit zdrojový soubor v rozhraní pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="procedures"></a>Procedury

#### <a name="to-magnify-a-timeline-segment"></a>Zvětšení segmentu časové osy

- Přetáhněte ukazatel myši na oblast časové osy.

     Po uvolnění tlačítka myši se zobrazení zvětší na vybraný časový segment. Můžete opakovat proces pro další zvětšení segmentu. Posunutí posuvníku na posuvníku času představuje relativní velikost časového segmentu, který se zobrazí v zobrazení.

#### <a name="to-zoom-out-on-a-timeline"></a>Přiblížení na časovou osu

- Proveďte jeden z následujících kroků:

  - Kliknutím na **oddálit** se vrátíte k předchozí úrovni přiblížení.

  - Klikněte na tlačítko **obnovit nastavení** , aby se zobrazila veškerá časová osa v zobrazení.

#### <a name="to-view-the-call-stack-of-an-event"></a>Zobrazení zásobníku volání události

- V grafu časové osy klikněte na panel událostí.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Zobrazení nebo úpravy zdrojového kódu funkce v zásobníku volání

- V okně **zásobník volání** klikněte na název funkce.

  Zdrojový kód funkce musí být součástí aktuálního projektu.

#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Zobrazení stromu volání událostí sporu pro prostředek

- V grafu časové osy klikněte na **celkem**.

     Pro prostředek se zobrazí zobrazení sporů. Další informace najdete v tématu [zobrazení sporů prostředků](../profiling/resource-contentions-view-contention-data.md).

#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Zobrazení všech událostí sporu vlákna

- V grafu časové osy klikněte na název nebo ID vlákna.

     Zobrazí se zobrazení podrobností o vlákně pro vybrané vlákno. Další informace naleznete v tématu [zobrazení podrobností o vláknech](../profiling/thread-details-view-contention-data.md).
