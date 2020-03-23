---
title: Značky příznaku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccc0c7aa3386e906ad13331a596953db70240701
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969940"
---
# <a name="flag-markers"></a>Značky příznaku
Značka příznaku představuje něco, co se stalo v okamžiku v čase v aplikaci. Příznak může představovat mnoho druhů událostí aplikace. Příznak může například zobrazit, kdy byla naplánována určitá pracovní položka nebo kdy byla vyvolána výjimka. Runtimes, jako je například paralelní knihovna úloh y můžete také generovat příznaky.

## <a name="flag-importance"></a>Důležitost příznaku
 Příznaky jsou zobrazeny v různých velikostech v závislosti na jejich důležitosti. Jako každá značka, význam může být nízká, normální, vysoká nebo kritická.  Tento obrázek znázorňuje vzhled značek podle úrovně důležitosti:

 ![Značky nízké, normální, vysoké a kritické důležitosti](../profiling/media/cvmarkerimportance.png "CVMarkerVýznam") Značky zobrazující důležitost příznaku

## <a name="flag-category"></a>Kategorie příznaku
 Příznak je zobrazen v jedné z pěti různých barev v závislosti na jeho kategorii. Barvy jsou znovu použity, pokud existuje více než pět kategorií. Barvu nelze vybrat. Jako každá značka může být kategorie libovolné celé číslo. Následující obrázek znázorňuje barvy prvních pěti kategorií.

 ![Pět barev značek kategorií](../profiling/media/cvmarkercategory.png "Kategorie CVMarker") Značky zobrazující kategorie

## <a name="alerts"></a>Výstrahy
 Výstraha je červený barevný příznak, který představuje událost kritické aplikace, například výjimku.  Tady je upozornění:

 ![Značka výstrahy vizualizéru souběžnosti](../profiling/media/cvmarkeralert.png "Upozornění na cvmarker") Značka výstrahy

## <a name="aggregation-flags"></a>Příznaky agregace
 Někdy příznaky dojít tak blízko u sebe v souběžnosti Vizualizátor, že nemohou být vypracovány jednotlivě. V takovém případě je zobrazen šedý *příznak agregace,* který představuje základní příznaky. Když položíte ukazatel myši na jednu z těchto ikon, zobrazí popisek počet zobrazených základních příznaků. Chcete-li zobrazit příznaky, přibližte zobrazení. Pokud přiblížíte celou cestu a stále získáte příznak agregace, můžete zobrazit základní příznaky v [sestavě značek](../profiling/markers-report.md).

 Agregační příznaky jsou kresleny v různých velikostech. Velikost závisí na úrovni důležitosti nejdůležitější příznak v agregaci. Následující obrázek znázorňuje příznaky agregace v rostoucím pořadí důležitosti.

 ![Agregační příznaky zobrazující čtyři úrovně důležitosti](../profiling/media/cvmarkeraggregate.png "Agregace CVMarker") Příznaky agregace podle úrovně důležitosti

## <a name="see-also"></a>Viz také
- [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)