---
title: Příznak značek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f924089ef31e2b452419b107788357060a4c6bb6
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237988"
---
# <a name="flag-markers"></a>Značky příznaků
Příznak značku představuje něco, co došlo k chybě v okamžiku v čase v aplikaci. Příznak může představovat různé druhy událostí aplikace. Příznak může například zobrazovat naplánovaného konkrétní pracovní položky nebo pokud došlo k výjimce. Moduly runtime například Task Parallel Library můžete také vygenerovat příznaky.  
  
## <a name="flag-importance"></a>Příznak důležitostí  
 Příznaky jsou zobrazeny v různě v závislosti na jejich důležitosti. Podobně jako všechny značky může být význam nízkou, Normální, vysoká nebo kritické.  Tento obrázek ukazuje vzhled značek podle úrovně důležitosti:  
  
 ![Nízká, Normální, vysoká a kritický význam značek](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Značky zobrazující příznaku důležitosti  
  
## <a name="flag-category"></a>Příznak kategorie  
 Příznak se zobrazí v jedné z pěti různých barev v závislosti na jeho kategorii. Barvy jsou opakovaně, pokud existuje více než pět kategorií. Nemůžete vybrat barvu. Podobně jako všechny značky může být kategorii jakékoliv celé číslo. Následující obrázek znázorňuje, barvy pro první pěti kategorií.  
  
 ![Pět barvy kategorie značek](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Značky zobrazující kategorií  
  
## <a name="alerts"></a>Upozornění  
 Výstraha je red barevných příznak, který představuje událost kritické aplikace, jako je například výjimku.  Tady je výstrahu:  
  
 ![Výstrahy značky Vizualizéru souběžnosti](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Výstrahy značky  
  
## <a name="aggregation-flags"></a>Příznaky agregace  
 Někdy příznaky dojít tak blízko sebe navzájem v Concurrency Visualizer, že se nemůže být vykreslován jednotlivě. Pokud k tomu dojde, šedá *agregace příznak* , se zobrazí představuje základní příznaků. Pokud se ukazatel myši na jednu z těchto ikon, zobrazí popisek počet základní příznaky, které představuje. Chcete-li zobrazit příznaků, přiblížení. Pokud přiblížit úplně a stále získat příznak agregaci, můžete zobrazit základní příznaky ve [sestava značek](../profiling/markers-report.md).  
  
 Příznaky agregace jsou vykreslovány v různých velikostech. Velikost závisí na úroveň důležitosti příznak nejdůležitější v agregace. Následující obrázek znázorňuje agregace příznaky ve vzestupném pořadí význam.  
  
 ![Agregace flags čtyři úrovně zobrazuje důležité](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Agregace příznaky podle úrovně důležitosti  
  
## <a name="see-also"></a>Viz také:  
 [Značky Vizualizéru souběžnosti](../profiling/concurrency-visualizer-markers.md)   
 [SDK Vizualizéru souběžnosti](../profiling/concurrency-visualizer-sdk.md)