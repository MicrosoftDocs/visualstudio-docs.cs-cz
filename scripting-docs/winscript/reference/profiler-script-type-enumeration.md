---
title: PROFILER_SCRIPT_TYPE – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796389"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE – výčet
Určuje typ skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Určuje kód uživatele zapsat skriptu.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Určuje kód skriptu, který je generován dynamicky během provádění.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Určuje typ skriptu pro nativní funkce a objekty, které jsou definovány skriptovacího stroje.|  
|PROFILER_SCRIPT_TYPE_DOM|Určuje volání do objektu modelu dokumentu (DOM) aplikace Internet Explorer, například volání `document.getElementById` metoda.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty profileru aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)