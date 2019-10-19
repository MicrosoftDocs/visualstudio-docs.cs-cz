---
title: Výčet PROFILER_SCRIPT_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574575"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE – výčet
Určuje typ skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
|PROFILER_SCRIPT_TYPE_USER|Určuje uživatelsky psaný kód skriptu.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Určuje kód skriptu, který je generován dynamicky během provádění.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Určuje typ skriptu pro nativní funkce a objekty, které jsou definovány skriptovacím modulem.|  
|PROFILER_SCRIPT_TYPE_DOM|Určuje volání do model DOM (Document Object Model) (DOM) aplikace Internet Explorer, například volání metody `document.getElementById`.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury profileru aktivních skriptů](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [Iactivescriptprofilercallback –:: ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [Iactivescriptprofilercallback2 –:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)