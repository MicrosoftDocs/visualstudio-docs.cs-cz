---
title: Výčet APPBREAKFLAGS – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572658"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS – výčet
Udávají aktuální stav ladění pro aplikace a vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Jazykový modul by měl být okamžitě přerušen na všech vláknech s BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Jazykový modul by měl být hned přerušený pomocí BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Jazykový modul by měl být okamžitě přerušen ve vlákně Stepping pomocí BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Aplikace je ve vnořeném provádění na zarážce.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Ladicí program provádí krokování na zdrojové úrovni.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Ladicí program je krokování na úrovni bajtového kódu.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Ladicí program se rozkrokuje na úrovni počítače.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maska pro vynásobení typů kroků|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Probíhá zarážka.|  
  
## <a name="remarks"></a>Poznámky  
 Některé příznaky určují, že by se měly jazykové moduly narušovat při další příležitosti, zatímco jiné příznaky určují režim krokování ladicího programu.  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [BREAKREASON – výčet](../../winscript/reference/breakreason-enumeration.md)