---
title: Porozumění hodnotám dat kolizí prostředků | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5983396924f38c31b6dafcd42b762042e1880e8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145438"
---
# <a name="understanding-resource-contention-data-values"></a>Porozumění hodnotám dat kolizí prostředku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilace kolizí prostředků shromažďuje podrobné informace o zásobníku volání pokaždé, když jsou konkurenční vlákna v aplikaci vynuceně čekat na přístup ke sdílenému prostředku.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Sestavy kolize prostředků zobrazují celkový počet kolizí a celkový čas, který byl vynaložen na čekání na prostředek pro moduly, funkce, řádky zdrojového kódu a instrukce, ve kterých došlo k čekání.  
  
- Hodnoty včetně hodnot zobrazují celkový počet sporů, které vynutily funkci pro čekání na spory prostředků a celkovou dobu, po kterou funkce čekala.  Spory, které byly způsobeny podřízenými funkcemi, které byly volány funkcí, jsou zahrnuty v hodnotách, které jsou k dispozici.  
  
- Exkluzivní hodnoty zobrazují pouze počet sporů, které vynutily funkci čekání a které byly způsobeny kódem v těle funkce. Spory způsobené podřízenými funkcemi nejsou zahrnuty. Výhradní čas pro funkci obsahuje také pouze časy čekání, které byly způsobeny příkazy v těle funkce.  
  
  Zobrazení sestav kolizí prostředků zahrnuje také grafy časové osy, které v průběhu času znázorňují jednotlivé události kolizí a zobrazují zásobníky volání, které vytvořily konkrétní událost. Další informace naleznete v jednom z následujících témat:  
  
- [Zobrazení podrobností o vláknu](../profiling/thread-details-view-contention-data.md)  
  
- [Zobrazení podrobností o prostředku](../profiling/resource-details-view-contention-data.md)  
  
  Další informace o druhém režimu profilace souběžnosti najdete v tématu [Vizualizátor souběžnosti](../profiling/concurrency-visualizer.md).
