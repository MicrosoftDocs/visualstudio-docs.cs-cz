---
title: Souhrnné zobrazení – zobrazení konfliktů prostředků | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 185345c13134f4d2ec6086e6a66183e044c577ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771445"
---
# <a name="summary-view---resource-contention-view"></a>Souhrnné zobrazení – zobrazení kolize prostředků
Souhrnné zobrazení zobrazuje informace o událostech v aplikaci, ve kterých bylo vlákno nebo proces pozastaven, zatímco čekal na přístup k prostředku.

 Další informace, včetně popisu odkazů na oznámení a seznamů sestav, naleznete v [tématu Souhrnné zobrazení](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v souhrnném zobrazení zobrazuje počet konfliktních událostí profilované aplikace v době, kdy došlo k profilování. Graf časové osy můžete použít k filtrování zobrazení na vybrané časové rozpětí. Další informace naleznete v [tématu How to: Filter Report Views from the Summary Timeline](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>Nejspornější zdroje
 **Většina tvrdí prostředky** uvádí prostředky v aplikaci, která způsobila nejvíce konfliktudálostí. Kliknutím na název prostředku zobrazíte zobrazení Konflikty. Zobrazení Konflikty poskytuje podrobnou časovou osu konflikty prostředků podle vlákna.

 **Většina tvrdil prostředky** obsahuje následující data pro každý prostředek.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název prostředku.|
|**Tvrzení %**|Procento všech konfliktních událostí v datech profilování, které byly konflikty nad tímto prostředkem.|

## <a name="most-contended-thread"></a>Nejspornější vlákno
 **Většina tvrdí vlákna** uvádí podprocesy v aplikaci, která měla největší počet konfliktních událostí. Kliknutím na název vlákna zobrazíte zobrazení Konflikty, které poskytuje podrobnou časovou osu tvrzení o prostředku podprocesem.

 **Většina tvrdí vlákna** obsahuje následující data pro každé vlákno.

|Sloupec|Popis|
|------------|-----------------|
|**Id**|Identifikátor vlákna.|
|**Název**|Název procesu, který vlastní vlákno.|
|**Tvrzení %**|Procento všech konfliktních událostí v datech profilování, které byly konflikty nad tímto prostředkem.|
