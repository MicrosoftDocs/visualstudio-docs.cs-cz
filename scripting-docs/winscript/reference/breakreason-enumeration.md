---
title: Výčet BREAKREASON | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791817"
---
# <a name="breakreason-enumeration"></a>Výčet BREAKREASON
Označuje, co způsobilo přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|BREAKREASON_STEP|Modul jazyk je v taktování režimu.|  
|BREAKREASON_BREAKPOINT|Modul jazyka došlo explicitní zarážek.|  
|BREAKREASON_DEBUGGER_BLOCK|Modul jazyka došlo blok ladicí program na jiné vlákno.|  
|BREAKREASON_HOST_INITIATED|Hostitel požadovaná zalomení.|  
|BREAKREASON_LANGUAGE_INITIATED|Modul jazyk požadovaný zalomení.|  
|BREAKREASON_DEBUGGER_HALT|Ladicí program IDE požadovaný zalomení.|  
|BREAKREASON_ERROR|Chyba spuštění způsobila rozdělení.|  
|BREAKREASON_JIT|Spuštění ladění JIT způsobené.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)