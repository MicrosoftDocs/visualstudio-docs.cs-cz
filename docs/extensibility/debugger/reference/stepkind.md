---
title: STEPKIND | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b69f90633c08eda3b27c0292be44743b2cd38509
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948366"
---
# <a name="stepkind"></a>STEPKIND
Určuje typ kroku pro procházení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Členové  
 STEP_INTO  
 Kroky na funkci.  
  
 STEP_OVER  
 Jednotlivé kroky k funkci.  
  
 STEP_OUT  
 Vystoupí z funkce.  
  
 STEP_BACKWARDS  
 Jednotlivé kroky zpět na funkci.  
  
## <a name="remarks"></a>Poznámky  
 Předán jako argument [krok](../../../extensibility/debugger/reference/idebugprocess3-step.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)