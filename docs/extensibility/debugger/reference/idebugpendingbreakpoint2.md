---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5e84180747a3e6a3b9e5a34e7694f4cd07867c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121554"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Toto rozhraní představuje zarážek, který je připraven vytvořit vazbu na umístění kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní jako součást své podpory zarážky.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) vytvoří čekající zarážek z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) rozhraní. Volání [vazby](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) vytvoří `IDebugBreakpoint2` rozhraní, které představuje vázané Breakpoint – v programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugPendingBreakpoint2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda tento čekající zarážek můžete vázat na umístění kódu.|  
|[Vazby](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Jedno nebo více umístění kód vytvoří vazbu této čekající zarážky.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav tohoto čekající na vyřízení zarážek.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá zarážek požadavek, který byl použit k vytvoření této čekající zarážky.|  
|[Při virtualizaci](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Přepne stav virtualizované tohoto čekající na vyřízení zarážek.|  
|[Povolit](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepne to čekající na vyřízení zarážek povolený stav.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Nastaví nebo změny přidružený k tomuto čekající na vyřízení zarážek podmínku.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Nastaví nebo změny průchodu počet, přidružený k tomuto čekající na vyřízení zarážek.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Vytvoří výčet všech zarážky vázaný z této čekající zarážky.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Zobrazí všechny zarážky chyba, která byla vygenerována z této čekající zarážky.|  
|[Odstranit](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní tento čekající zarážek a všechny zarážky vázaný z něj.|  
  
## <a name="remarks"></a>Poznámky  
 `IDebugPendingBreakpoint2` můžete představit jako zprostředkovatel všechny potřebné informace potřebné k vytvoření vazby boru přerušení. kód, který lze použít pro jednu nebo více programů.  
  
 Čekající zarážek potenciálně může vytvářet více než jeden vázané breakpoint. Například zarážky v šabloně stylu C++ může vytvořit vázané Breakpoint – pro každou jedinečnou instanci dané šablony.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)