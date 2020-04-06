---
title: IDebugPendingBreakpoint2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725652"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Toto rozhraní představuje zarážku, která je připravena k vytvoření vazby na umístění kódu.

## <a name="syntax"></a>Syntaxe

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní jako součást jeho podporu pro zarážky.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) vytvoří čekající zarážku z rozhraní [IDebugBreakpointRequest2.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Volání [bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) vytvoří `IDebugBreakpoint2` rozhraní, které představuje vázanou zarážku v programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugPendingBreakpoint2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Určuje, zda tato čekající zarážka může vázat na umístění kódu.|
|[Vytvořit vazbu](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Váže tuto čekající zarážku na jedno nebo více umístění kódu.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Získá stav této čekající zarážky.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Získá požadavek na zarážku, který byl použit k vytvoření této čekající zarážky.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Přepíná virtualizovaný stav této čekající zarážky.|
|[Povolení](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Přepíná povolený stav této čekající zarážky.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Nastaví nebo změní podmínku přidruženou k této čekající zarážky.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Nastaví nebo změní počet průchodů přidružených k této čekající zarážky.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Vyjmenovává všechny zarážky vázané z této čekající zarážky.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Vyjmenovává všechny chybové zarážky, které vyplynuly z této čekající zarážky.|
|[Odstranit](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Odstraní tuto čekající zarážku a všechny zarážky z ní vázané.|

## <a name="remarks"></a>Poznámky
 `IDebugPendingBreakpoint2`lze považovat za zprostředkovatele všech potřebných informací potřebných k vytvoření zarážky ke kódu, který lze použít pro jeden nebo více programů.

 Čekající zarážka může potenciálně vytvořit více než jednu vázanou zarážku. Například zarážka v šabloně stylu C++může vytvořit vázanou zarážku pro každou jedinečnou instanci této šablony.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
