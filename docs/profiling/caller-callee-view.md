---
title: Volající volaný – zobrazení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 973c65927e3732cff44ab8eecb684f3c75af8614
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264291"
---
# <a name="callercallee-view"></a>Volající/Volaný – zobrazení
Zobrazení volající/volaný zobrazí profilování informace o vybrané funkce a její nadřazené a podřízené funkce. Zobrazení volající/volaný obsahuje tři mřížky:  
  
 **Funkci Current** se zobrazí v prostředním mřížky a ukazuje profilace informace o vybrané funkce. Hodnoty zahrnují všechna volání funkce, které byly shromážděny v profilaci spustit.  
  
 **Funkce, které volá funkci current** se zobrazí v horní mřížky, a zobrazuje počet hodnot vybrané (aktuální) funkce, které byly vygenerovány volání z funkce volající (nadřazené).  
  
 **Funkce, které byly volá funkci current** se zobrazí v mřížce dole ale zobrazí při volání funkce podřízené aktuální funkcí profilace informace pro funkce volaný (podřízená) vybrané funkce.  
  
 Sloupce, které jsou k dispozici v zobrazení volající/volaný závisí na profilování metody (vzorkování nebo instrumentace), která se používá ke shromažďování dat a jestli dat paměti .NET nebyla shromážděna v profilaci spustit.  
  
 Můžete vybrat jiné funkce na funkci aktuální v střední část zobrazení sestavy, a dvakrát klikněte na některou z funkcí, které jsou uvedeny v další dvě části tohoto zobrazení. Zobrazení sestavy se automaticky aktualizuje, aby se projevily změny.  
  
 Data můžete seřadit kliknutím na názvy sloupců. Zobrazení volající/volaný lze přidat další sloupce. Další informace najdete v tématu [postupy: přizpůsobení sloupců zobrazení sestavy](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení volající/volaný – vzorkování dat](../profiling/caller-callee-view-sampling-data.md)   
 [Zobrazení volající/volaný – data instrumentace](../profiling/caller-callee-view-instrumentation-data.md)   
 [Zobrazení volající/volaný – data instrumentace paměti .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Zobrazení volající/volaný – data vzorkování paměti .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Zobrazení volající/volaný – data kolizí](../profiling/caller-callee-view-contention-data.md)