---
title: Značky příznaků | Microsoft Docs
description: Další informace o značkách příznaků najdete v Vizualizér souběžnosti sady Visual Studio. Značka praporku představuje něco, co v aplikaci nastalo v čase.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc7e8d9a7c39a0bb7953c309adb9f2abb1c0dc43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916711"
---
# <a name="flag-markers"></a>Značky příznaků
Značka praporku představuje něco, co v aplikaci nastalo v čase. Příznak může představovat mnoho typů událostí aplikace. Příznak může například zobrazit, kdy byla určitá pracovní položka naplánována nebo byla vyvolána výjimka. Moduly runtime, jako je například Task Parallel Library, mohou také generovat příznaky.

## <a name="flag-importance"></a>Důležitost označení
 Příznaky se zobrazují v různých velikostech v závislosti na jejich důležitosti. Podobně jako u libovolné značky může být důležitost nízká, normální, vysoká nebo kritická.  Tento obrázek znázorňuje vzhled značek podle úrovně důležitosti:

 ![Značky nízké, normální, vysoké a kritické důležitosti](../profiling/media/cvmarkerimportance.png "CVMarkerImportance") Značky ukazující důležitost příznaku

## <a name="flag-category"></a>Kategorie příznaků
 Příznak se zobrazí v jedné z pěti různých barev v závislosti na jeho kategorii. Barvy se znovu použijí, pokud existuje více než pět kategorií. Barvu nelze vybrat. Stejně jako u libovolné značky může být kategorie libovolné celé číslo. Následující obrázek znázorňuje barvy pro prvních pět kategorií.

 ![Pět barev značek kategorií](../profiling/media/cvmarkercategory.png "CVMarkerCategory") Značky zobrazující kategorie

## <a name="alerts"></a>Výstrahy
 Výstraha je červený barevný příznak, který představuje kritickou událost aplikace, jako je například výjimka.  Tady je upozornění:

 ![Značka výstrahy Vizualizátor souběžnosti](../profiling/media/cvmarkeralert.png "CVMarkerAlert") Značka výstrahy

## <a name="aggregation-flags"></a>Agregované příznaky
 Někdy se příznaky vyskytují, takže se v Vizualizátor souběžnosti nedají kreslit samostatně. V takovém případě se zobrazí šedý *příznak agregace* , který představuje základní příznaky. Když umístíte ukazatel myši na jednu z těchto ikon, zobrazí se popis, který znázorňuje počet základních příznaků, které jsou zastoupeny. Chcete-li zobrazit příznaky, přiblížit. Pokud přiblížíte všechny způsoby a stále získáte příznak agregace, můžete zobrazit základní příznaky v [sestavě značek](../profiling/markers-report.md).

 Příznaky agregace jsou vykreslovány v různých velikostech. Velikost závisí na úrovni důležitosti nejdůležitějšího příznaku v agregaci. Následující ilustrace znázorňuje agregované příznaky ve vzestupném pořadí podle důležitosti.

 ![Agregované příznaky zobrazující čtyři úrovně důležitosti](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate") Agregované příznaky podle úrovně důležitosti

## <a name="see-also"></a>Viz také
- [Značky Vizualizátor souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)