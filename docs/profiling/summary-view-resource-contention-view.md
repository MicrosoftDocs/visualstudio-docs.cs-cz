---
title: Souhrnné zobrazení – zobrazení kolizí prostředků | Microsoft Docs
description: V souhrnném zobrazení se zobrazí informace o událostech aplikace, ve kterých bylo během čekání na přístup k prostředku pozastaveno vlákno nebo proces.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3e6f0b629aa14cf465dcaa8abec48e3eea110c4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959997"
---
# <a name="summary-view---resource-contention-view"></a>Souhrnné zobrazení – zobrazení kolize prostředků
V souhrnném zobrazení se zobrazí informace o událostech aplikace, ve kterých bylo během čekání na přístup k prostředku pozastaveno vlákno nebo proces.

 Další informace, včetně popisu odkazů na oznámení a seznamů sestav, najdete v tématu [souhrnné zobrazení](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Graf časové osy
 Graf časové osy v zobrazení Souhrn znázorňuje počet událostí kolizí profilované aplikace v době, kdy k profilaci došlo. Graf časové osy můžete použít k filtrování zobrazení do vybraného časového rozsahu. Další informace najdete v tématu [Postup: filtrování zobrazení sestav na časové ose souhrnu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>Největší prostředky, které jsou v úmyslu
 **Většina** vyvolaných prostředků vypisuje prostředky v aplikaci, které způsobily největší události sporů. Kliknutím na název prostředku můžete zobrazit zobrazení sporů. Zobrazení sporů poskytuje podrobnou časovou osu sporů prostředků podle vlákna.

 **Většina** vydaných prostředků zahrnuje pro každý prostředek následující data.

|Sloupec|Popis|
|------------|-----------------|
|**Název**|Název prostředku.|
|**Sporů**|Procento všech událostí sporů v datech profilace, které byly v tomto prostředku vyhodnoceny jako spory.|

## <a name="most-contended-thread"></a>Nejvíce v úmyslu
 **Většina** vydaných vláken zobrazuje vlákna v aplikaci, která měla nejvyšší počet událostí sporů. Kliknutím na název vlákna můžete zobrazit zobrazení sporů, které poskytuje detailní časovou osu sporů prostředků vláknem.

 **Většina nejnáročnějších vláken** obsahuje pro každé vlákno následující data.

|Sloupec|Popis|
|------------|-----------------|
|**ID**|Identifikátor vlákna.|
|**Název**|Název procesu, který vlastní vlákno.|
|**Sporů**|Procento všech událostí sporů v datech profilace, které byly v tomto prostředku vyhodnoceny jako spory.|
