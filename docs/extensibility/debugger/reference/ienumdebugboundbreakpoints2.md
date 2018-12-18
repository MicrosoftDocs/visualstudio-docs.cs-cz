---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5faeb96f32170fefa1f93a69ca08228ceaec11f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121050"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Toto rozhraní zobrazí vázané zarážky přidružené čekající zarážek nebo zarážek vázaný událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní jako součást své podpory zarážky. Toto rozhraní musí být implementována, pokud jsou podporovány zarážky.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Visual Studio volání:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) k získání tohoto rozhraní představující seznam všech zarážky, které se spustila.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) k získání tohoto rozhraní představující seznam všech zarážky, které se váží.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) k získání tohoto rozhraní představující seznam všech zarážky vázána na tento čekající zarážek.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IEnumDebugBoundBreakpoints2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Načte zadaný počet vázané zarážky v posloupnosti výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Přeskočí zadaný počet vázané zarážky v posloupnosti výčtu.|  
|[Resetování](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Návrat na začátek v sekvenci výčtu.|  
|[klonování](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Vytvoří enumerátor, který obsahuje stav výčtu jako aktuální enumerátor.|  
|[GetCount –](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Získá počet vázané zarážky v enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio použije vázané zarážky reprezentovaný tímto rozhraním aktualizovat zobrazení zarážky v prostředí IDE.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)