---
title: Výčet SCRIPTTHREADSTATE – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575659"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE – výčet
Určuje stav vlákna ve skriptovacím stroji. Tento výčet používá metoda [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Zadané vlákno aktuálně neobsluhuje událost skriptu, zpracovává okamžitě text skriptu nebo spouští makro skriptu.|  
|SCRIPTTHREADSTATE_RUNNING|Zadané vlákno aktivně obsluhuje událost skriptu, zpracovává okamžitě text skriptu nebo spouští makro skriptu.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a kódy chyb aktivních skriptů](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)