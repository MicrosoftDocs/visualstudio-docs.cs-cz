---
title: Značky span | Microsoft Docs
description: Přečtěte si, jak Značka rozsahu představuje smysluplnou fázi aplikace a jak vidět příklad, který ukazuje rozpětí v Vizualizátor souběžnosti.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 526d82194a4ed1463c802296cb97c95e0eb41d33
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960140"
---
# <a name="span-markers"></a>Značky span
Značka rozsahu představuje smysluplnou fázi aplikace. Například můžete použít rozsah, který představuje časový interval, během kterého se zpracovává konkrétní pracovní položka. Jeho délka představuje dobu trvání odpovídající fáze aplikace. Tento obrázek ukazuje rozpětí v Vizualizátor souběžnosti:

 ![Značka span v Vizualizér souběžnosti](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Značka span v Vizualizér souběžnosti

## <a name="span-category"></a>Span – kategorie
 Značka rozpětí se zobrazí v jedné z pěti různých barev v závislosti na její kategorii. Pokud existuje více než pět kategorií, budou barvy opakovány. Kategorie může být libovolné celé číslo. Na tomto obrázku vidíte pět možných barev:

 ![Pět rozsahů v různých kategoriích](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") Barvy prvních pěti kategorií span

## <a name="span-aggregation-markers"></a>Span – značky agregace
 Někdy se značky přestanou provádět tak, aby se v Vizualizátor souběžnosti vzájemně nemohly kreslit samostatně. V takovém případě je zobrazena šedá *značka agregace rozsahu* , která představuje základní rozsahy. Když umístíte ukazatel myši na jednu z těchto ikon, zobrazí se popis, který znázorňuje počet základních rozsahů, které jsou reprezentovány. Chcete-li zobrazit rozsahy, přiblížte se. Pokud se přiblížíte ke všemu způsobem a stále získáte značku agregace rozsahu, můžete zobrazit základní značky span v [sestavě značek](../profiling/markers-report.md). Tento obrázek ukazuje značku agregace rozsahu:

 ![Agregovaná Značka rozsahu v Vizualizér souběžnosti](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Značka agregace rozsahu

## <a name="see-also"></a>Viz také
- [Značky Vizualizátor souběžnosti](../profiling/concurrency-visualizer-markers.md)
- [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)