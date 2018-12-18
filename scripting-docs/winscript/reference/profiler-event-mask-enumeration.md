---
title: PROFILER_EVENT_MASK – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796428"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK – výčet
Určuje typy událostí, které by měl být profilovaným.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funkce profily, které jsou definovány v uživatele zapsat skript a dynamický kód.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Nativní funkce profily, které jsou definovány skriptovacího stroje.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Profily všechny funkce uživatelsky definovaná a skriptovací stroje, s výjimkou volání do objektu modelu dokumentu (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funkce profily, které volání do modelu DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Profily všechny funkce, včetně volání do modelu DOM.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty profileru aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)