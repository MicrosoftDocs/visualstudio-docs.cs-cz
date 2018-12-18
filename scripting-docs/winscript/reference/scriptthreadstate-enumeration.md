---
title: SCRIPTTHREADSTATE – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e18cc6f5f2afb1dcea6835983f69f6a6f7b9280
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796329"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE – výčet
Určuje stav vlákna v skriptovacího stroje. Tento výčet je používán [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Zadaný vlákno je aktuálně obsluhy skriptované událostí, zpracování okamžitě spustit skript text, nebo spuštění skriptu makra.|  
|SCRIPTTHREADSTATE_RUNNING|Zadaný vlákno je aktivně obsluhy skriptované událostí, zpracování okamžitě spustit skript text, nebo spuštění skriptu makra.|  
  
## <a name="see-also"></a>Viz také  
 [Aktivních skriptů konstanty, výčty a kódy chyb](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)