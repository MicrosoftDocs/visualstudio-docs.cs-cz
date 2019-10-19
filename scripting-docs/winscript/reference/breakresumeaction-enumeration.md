---
title: Výčet BREAKRESUMEACTION – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572611"
---
# <a name="breakresumeaction-enumeration"></a>Výčet BREAKRESUMEACTION
Popisuje způsoby, jak pokračovat ze zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Ukončí aplikaci.|  
|BREAKRESUMEACTION_CONTINUE|Pokračuje v běhu.|  
|BREAKRESUMEACTION_STEP_INTO|Postup.|  
|BREAKRESUMEACTION_STEP_OVER|Postupuje postupem.|  
|BREAKRESUMEACTION_STEP_OUT|Kroky jsou mimo aktuální postup.|  
|BREAKRESUMEACTION_IGNORE|Pokračuje v běhu se stavem.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Kroky k dalšímu dokumentu.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)