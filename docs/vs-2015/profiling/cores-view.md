---
title: Zobrazení jader | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 869980fe7bbb773d566dffd38088b003e3a97a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145640"
---
# <a name="cores-view"></a>Zobrazení jader
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení jádra ukazuje, jak bylo spuštění vlákna namapováno na jádra logického procesoru. Pokud píšete serverové aplikace, toto zobrazení vám může pomoci optimalizovat výkon mezipaměti pomocí spřažení vlákna nebo správy fondu vláken. Může vám taky posuzovat případy, kdy použití spřažení vlákna mohlo zhoršit problémy s migrací mezi jádry. Zobrazení jádra má dvě části, graf a legendu.  
  
 Graf znázorňuje logické jádra na ose y a čas na ose x. Každé vlákno v grafu má jedinečnou barvu, abyste mohli sledovat jeho pohyb napříč jádry v průběhu času. Vlákna v tomto grafu můžete filtrovat tak, že je vyberete v oblasti legenda.  
  
 Oblast legendy obsahuje záznam pro každou barvu v grafu. Každá položka zobrazuje barvu a název vlákna, počet přepínačů kontextu mezi jádry, celkový počet přepínačů kontextu a procento přepínačů kontextu, které kříží jádro. Legenda je seřazena podle počtu přepínačů kontextu křížového jádra v klesajícím pořadí. Obsahuje pouze vlákna, která byla provedena během zobrazeného časového rozsahu.  Seznam se aktualizuje, když přiblížíte nebo posunete.  
  
## <a name="see-also"></a>Viz také  
 [Vizualizátor souběžnosti](../profiling/concurrency-visualizer.md)   
 [Zobrazení využití](../profiling/utilization-view.md)   
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
