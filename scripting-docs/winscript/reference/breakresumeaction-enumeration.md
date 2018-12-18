---
title: Výčet BREAKRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791877"
---
# <a name="breakresumeaction-enumeration"></a>Výčet BREAKRESUMEACTION
Popisuje, jak pokračovat od zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|BREAKRESUMEACTION_ABORT|Zruší aplikace.|  
|BREAKRESUMEACTION_CONTINUE|Běžet dál.|  
|BREAKRESUMEACTION_STEP_INTO|Kroky do procedury.|  
|BREAKRESUMEACTION_STEP_OVER|Kroky přes procedury.|  
|BREAKRESUMEACTION_STEP_OUT|Kroky mimo aktuální procedury.|  
|BREAKRESUMEACTION_IGNORE|Běh stavu pokračuje.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Postup další dokument.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)