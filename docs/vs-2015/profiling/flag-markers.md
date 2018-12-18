---
title: Příznak značek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4d1e5c119c5402501efaafcdccd9c3d0885ce75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803198"
---
# <a name="flag-markers"></a>Značky příznaků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příznak značka představuje něco, ke které došlo v okamžiku v čase v aplikaci. Příznak, který může představovat různé druhy událostí aplikace. Příznak, který může například zobrazit naplánovaného konkrétní pracovní položce nebo když došlo k výjimce. Moduly runtime, jako je například Task Parallel Library můžete vygenerovat také příznaky.  
  
## <a name="flag-importance"></a>Důležitosti příznaku  
 Příznaky jsou zobrazeny v různě v závislosti na jejich význam. Stejně jako všechny značky může být význam nízká, Normální, vysoká nebo kritické.  Tento obrázek ukazuje vzhled značek podle úrovně závažnosti:  
  
 ![Nízká, Normální, vysokou a kritický význam značky](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Značky zobrazující důležitosti příznaku  
  
## <a name="flag-category"></a>Příznak kategorie  
 Příznak, který se zobrazí v jednom z pěti různých barev v závislosti na jeho kategorie. Barvy jsou znovu použít, pokud existuje více než pět kategorií. Nemůžete zvolit barvu. Stejně jako všechny značky kategorie může být libovolné celé číslo. Následující obrázek znázorňuje barvy pro prvních pět kategorií.  
  
 ![Pět barvy značky kategorie](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Zobrazení kategorií značky  
  
## <a name="alerts"></a>Upozornění  
 Výstraha je red barevné příznak, který představuje událost kritické aplikace, jako je například výjimku.  Tady je výstrahy:  
  
 ![Upozornění značek pro Concurrency Visualizer](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Upozornění značky  
  
## <a name="aggregation-flags"></a>Příznaky agregace  
 Někdy příznaky probíhá tak blízko sebe Vizualizátor souběžnosti, že se nedá vykreslit jednotlivě. Pokud k tomu dojde, šedé *agregace příznak* , že se zobrazí představuje základní příznaky. Když ukazatel myši na jednu z těchto ikon, zobrazí popisek počet základní příznaky, které jsou reprezentovány. Chcete-li zobrazit příznaků, Přiblížit. Pokud přiblížíte úplně a zachovat si agregaci příznak, můžete zobrazit základní příznaky v [sestava značek](../profiling/markers-report.md).  
  
 Příznaky agregace jsou vykreslovány v různých velikostech. Velikost závisí na úroveň důležitosti příznaku nejdůležitější v agregaci. Následující obrázek znázorňuje příznaky agregace ve vzestupném pořadí podle důležitosti.  
  
 ![Agregace příznaky znázorňující čtyři úrovně důležitosti](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Příznaky agregace podle úrovně závažnosti  
  
## <a name="see-also"></a>Viz také  
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)   
 [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)



