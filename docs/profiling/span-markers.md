---
title: Značky rozpětí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69b48a5b1b551e2e29b9aa10e7f68ff0df0e379
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62980957"
---
# <a name="span-markers"></a>Značky rozpětí
Značka rozpětí představuje smysluplnou fázi aplikace. Můžete například použít rozpětí představují časový interval, během kterého je zpracovávána určitá pracovní položka. Jeho délka představuje dobu trvání odpovídající fáze aplikace. Tento obrázek znázorňuje rozpětí v vizualizéru souběžnosti:

 ![Značka rozpětí ve vizualizéru souběžnosti](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Značka rozpětí ve vizualizéru souběžnosti

## <a name="span-category"></a>Kategorie rozpětí
 Značka rozpětí je zobrazena v jedné z pěti různých barev v závislosti na jeho kategorii. Barvy se opakují, pokud existuje více než pět kategorií. Kategorie může být libovolné celé číslo. Tento obrázek znázorňuje pět možných barev:

 ![Pět rozpětí v různých kategoriích](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanKategorie") Barvy prvních pěti kategorií rozpětí

## <a name="span-aggregation-markers"></a>Značky agregace rozsahu
 Někdy span značky dojít tak blízko u sebe v souběžnosti Vizualizátor, že nemohou být vypracovány jednotlivě. V takovém případě je *zobrazena značka šedé agregace rozpětí,* která představuje základní rozsahy. Když položíte ukazatel myši na jednu z těchto ikon, zobrazí popisek počet zobrazených podkladových rozsahů. Chcete-li zobrazit rozpětí, přibližte zobrazení. Pokud přiblížíte celou cestu a stále získáte značku agregace rozpětí, můžete zobrazit základní značky rozsahu v [sestavě značek](../profiling/markers-report.md). Tento obrázek znázorňuje značku agregace rozpětí:

 ![Agregační značka rozsahu v vizualizéru souběžnosti](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAgregace") Agregační značka rozpětí

## <a name="see-also"></a>Viz také
- [Značky vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)