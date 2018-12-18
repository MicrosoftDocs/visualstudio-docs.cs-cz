---
title: Značky rozpětí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37f2dd735b7deb2d4fed1232c2ba690b26a9fde0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676456"
---
# <a name="span-markers"></a>Značky rozpětí
Značka span představuje smysluplné fáze aplikace. Například můžete použít rozpětí k reprezentaci interval doby, během kterého se zpracovává konkrétní pracovní položce. Jeho délka představuje dobu trvání odpovídající fáze aplikace. Tento obrázek ukazuje rozpětí ve Vizualizátor souběžnosti:  
  
 ![Značku span v Concurrency Visualizer](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Značka span ve vizualizátoru souběžnosti  
  
## <a name="span-category"></a>Kategorie značky span  
 V jednom z pěti různých barev, v závislosti na jeho kategorie se zobrazí značku span. Barvy se opakují, pokud existuje více než pět kategorií. Kategorie může být libovolné celé číslo. Tento obrázek ukazuje pět možných barev:  
  
 ![Pět rozsahy v různých kategoriích](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Barvy prvních pět kategorií rozpětí  
  
## <a name="span-aggregation-markers"></a>Agregace značky rozpětí  
 Někdy span značky tak dojít blízko sebe ve vizualizátoru souběžnosti, že se nedá vykreslit jednotlivě. Pokud k tomu dojde, šedé *značky span agregace* , že se zobrazí představuje základní rozpětí. Když ukazatel myši na jednu z těchto ikon, zobrazí popisek počet základní rozsahy, které jsou reprezentovány. Chcete-li zobrazit rozsahy, Přiblížit. Pokud přiblížíte úplně a zachovat si značka span agregace, můžete zobrazit základní značky span v [sestava značek](../profiling/markers-report.md). Tento obrázek ukazuje značku span agregace:  
  
 ![Agregace span značky v Concurrency Visualizer](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Značka span agregace  
  
## <a name="see-also"></a>Viz také:  
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)   
 [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)