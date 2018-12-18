---
title: Scriptthreadid – konstanty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc692716115ea0c205b1cfd982b189fffd54a9ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796410"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID – konstanty
Slouží k zadání typu přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Aktuálně prováděné vlákno.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Základní podprocesu. To znamená, že byla vytvořena instance vláken, ve kterém skriptování modul.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Všechna vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 `SCRIPTTHREADID` Typ se používá v `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, a `IActiveScript::InterruptScriptThread`, ale konstanty lze použít pouze `IActiveScript::GetScriptThreadState` a `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)