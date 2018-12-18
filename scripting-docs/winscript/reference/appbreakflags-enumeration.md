---
title: APPBREAKFLAGS – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792027"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Jazyk modul by měl okamžitě rozdělit na všechna vlákna s BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Jazyk modul by měl s BREAKREASON_DEBUGGER_HALT rozdělit okamžitě.|  
|APPBREAKFLAG_STEP|0x00010000|Jazyk modul by měl proniknout okamžitě taktování vlákno s BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|Aplikace je v vnořené provádění na zarážky.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|Ladicí program je krokování na úrovni zdroje.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|Ladicí program je krokování na úrovni kódu bajtů.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|Ladicí program je krokování na úrovni počítače.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Maska řešení si krok typu.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Probíhá zarážky.|  
  
## <a name="remarks"></a>Poznámky  
 Některé příznaky zadejte, že jazyk moduly by mělo dojít při nejbližší příležitosti, při nastavení další příznaky zadejte taktování režimu ladicího programu.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON – výčet](../../winscript/reference/breakreason-enumeration.md)