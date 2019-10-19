---
title: Konstanty SCRIPTTHREADID – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575667"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID – konstanty
Slouží k určení typu vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Aktuálně prováděné vlákno.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Základní vlákno; To znamená vlákno, ve kterém se vytvořila instance skriptovacího stroje.|  
|SCRIPTTHREADID_ALL|Hodnotu|Všechna vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 @No__t_0 typ používá `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` a `IActiveScript::InterruptScriptThread`, ale konstanty lze použít pouze `IActiveScript::GetScriptThreadState` a `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)    
 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)