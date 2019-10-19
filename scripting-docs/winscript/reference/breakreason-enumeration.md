---
title: Výčet BREAKREASON – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572623"
---
# <a name="breakreason-enumeration"></a>Výčet BREAKREASON
Označuje, co způsobilo přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|BREAKREASON_STEP|Jazykový modul se nachází v režimu krokování.|  
|BREAKREASON_BREAKPOINT|Jazykový modul narazil na explicitní zarážku.|  
|BREAKREASON_DEBUGGER_BLOCK|Jazykový modul nalezl blok ladicího programu v jiném vlákně.|  
|BREAKREASON_HOST_INITIATED|Hostitel požadoval přerušení.|  
|BREAKREASON_LANGUAGE_INITIATED|Jazykový modul požadoval přerušení.|  
|BREAKREASON_DEBUGGER_HALT|Rozhraní IDE ladicího programu vyžadovalo přerušení.|  
|BREAKREASON_ERROR|Chyba provádění způsobila přerušení.|  
|BREAKREASON_JIT|Příčinou je spuštění ladění JIT.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)