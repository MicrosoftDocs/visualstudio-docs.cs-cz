---
title: THREADSTATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e2f6e8011b001c88743871a137ebc0b8cd7c26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204786"
---
# <a name="threadstate"></a>THREADSTATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje stav vlákna.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Členové  
 THREADSTATE_RUNNING  
 Indikuje, že vlákno běží.  
  
 THREADSTATE_STOPPED  
 Označuje, že vlákno je zastaveno z důvodu zarážky.  
  
 THREADSTATE_FRESH  
 Indikuje, že vlákno bylo vytvořeno, ale ještě neběží s kódem.  
  
 THREADSTATE_DEAD  
 Indikuje, že vlákno je neaktivní.  
  
 THREADSTATE_FROZEN  
 Indikuje, že je vlákno zmrazeno (nelze provést žádné spuštění).  
  
## <a name="remarks"></a>Poznámky  
 Používá se pro `dwThreadState` pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
