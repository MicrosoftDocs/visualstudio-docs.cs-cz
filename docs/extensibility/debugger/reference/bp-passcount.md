---
title: BP_PASSCOUNT | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 105c6668c50d690bcc0016f888ce1f241130d1eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883112"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
Popisuje počet a podmínky, při které se aktivuje podmíněné zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Členové  
 `dwPassCount`  
 Počet pokusů, než se ohlásí ji procházel přes zarážku.  
  
 `stylePassCount`  
 Hodnota z [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) počet průchodů výčet, který určuje typ zarážky.  
  
## <a name="remarks"></a>Poznámky  
 Tato struktura je členem skupiny [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury.  
  
 Tato struktura je také předat jako parametr[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) a[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)