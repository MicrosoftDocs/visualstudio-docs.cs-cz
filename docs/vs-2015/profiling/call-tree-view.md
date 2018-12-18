---
title: Zobrazení stromu volání | Dokumentace Microsoftu
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
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f09b85c20d84cb25d6a1fdbbd8493c47056318a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738753"
---
# <a name="call-tree-view"></a>Zobrazení stromu volání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení stromu volání zobrazí cesty spuštění funkce, které byly Procházet v profilované aplikaci. Kořen stromu je vstupním bodem do aplikace nebo komponenty. Každý uzel funkce obsahuje všechny funkce, které se nazývá a údaje o výkonu o volání těchto funkcí.  
  
 Zobrazení stromu volání můžete také rozšířit a zvýrazňovat cesta provedení funkce, která nejvíce času spotřebovaného nebo vzorkováno nejčastěji. Zobrazení výkonu nejdražší cesty, klikněte pravým tlačítkem na funkci a pak klikněte na **rozbalit kritickou cestu**.  
  
 Každý proces při spuštění profilování se zobrazí jako kořenový uzel. Počáteční uzel zobrazení stromu volání můžete nastavit tak, že kliknete pravým tlačítkem uzel, který chcete nastavit jako počáteční uzel a pak vyberete **nastavit kořenový**.  
  
 Když nastavíte kořenový uzel, odstraníte všechny položky ze zobrazení s výjimkou podstrom vybraný uzel. Kořenový uzel můžete resetovat zpět do uzlu, který byl zobrazený. V okně zobrazení stromu volání, klikněte pravým tlačítkem myši a potom vyberte **resetování kořenového**.  
  
 Přidejte nebo odeberte sloupce je možné přizpůsobit zobrazení stromu volání. Klikněte pravým tlačítkem myši **sloupec Název záhlaví**a pak vyberte **Přidat/odebrat sloupce**.  
  
 Zobrazení stromu volání lze nakonfigurovat pro snížení šumu tím, že omezíte množství dat, která se zobrazí. Pomocí snížení šumu jsou problémy s výkonem nejvážnějších v zobrazení. Když je snadné je rozlišit problémy s výkonem, analýzy je jednodušší. Další informace najdete v tématu [postupy: Konfigurace snížení šumu v zobrazeních sestav](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Pokud je nakonfigurováno snížení šumu zobrazovat upozornění, když je povoleno, informační panel, zobrazí se v sestavě.  
  
 Další informace o definicích sloupců v zobrazení stromu volání naleznete v následujících tématech:  
  
 [Zobrazení stromu volání](../profiling/call-tree-view-sampling-data.md)  
  
 [Zobrazení stromu volání](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Zobrazení stromu volání – Vzorkování](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Zobrazení stromu volání](../profiling/call-tree-view-contention-data.md)  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení sestav výkonu](../profiling/performance-report-views.md)   
 [Porozumění hodnotám dat instrumentace](../profiling/understanding-instrumentation-data-values.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)



