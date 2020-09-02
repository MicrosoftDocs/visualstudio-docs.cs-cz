---
title: Zobrazení řádků | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccdb211312a6f53e7f519b7fac0e3ac28aab2429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145636"
---
# <a name="lines-view"></a>Zobrazení řádků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení řádků je k dispozici pouze pro data profileru, která byla shromážděna pomocí metody vzorkování. Zobrazení není k dispozici pro data shromážděná pomocí instrumentace.  
  
 V případě vzorkování dat profilu se v zobrazení řádky identifikuje příkaz ve funkci, která byla přímo spuštěna při shromáždění ukázky. V případě dat paměti .NET identifikuje zobrazení řádky příkazy, které přidělují paměť.  
  
 Ve zdrojovém souboru může příkaz pokrývat více než jeden řádek ve zdrojovém souboru a jeden řádek může obsahovat více než jeden výraz.  
  
 Příkaz je identifikován následujícím způsobem:  
  
- Zdrojový soubor, který obsahuje příkaz Function.  
  
- Funkce, která obsahuje příkaz.  
  
- Zdrojový řádek, ve kterém se příkaz spustí.  
  
- Znak ve zdrojovém řádku, ve kterém se příkaz spustí.  
  
- Zdrojový řádek, na kterém končí příkaz.  
  
- Znak ve zdrojovém řádku, na kterém končí příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení řádků](../profiling/lines-view-sampling-data.md)   
 [Zobrazení řádků – vzorkování](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zobrazení řádků](../profiling/lines-view-contention-data.md)
