---
title: MACHINE_INFO | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7cc6bd2e55542c25df41f19dda87ff08dd095517
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729895"
---
# <a name="machineinfo"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Popisuje konkrétní počítač.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Členové  
 `Fields`  
 Kombinace příznaků z [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) výčet určující, která pole struktury jsou inicializovány.  
  
 `bstrName`  
 Název počítače. Ekvivalentní volání [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Kombinace příznaků z [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) výčet popisující atributy počítače.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je vrácený voláním [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

