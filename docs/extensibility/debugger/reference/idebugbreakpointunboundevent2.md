---
title: IDebugBreakpointUnboundEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e1d15936316d08a712e3d6f3fdc7a3a73be613d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734636"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Toto rozhraní informuje správce ladění relace (SDM), že vázaná zarážka byla nevázaná z načteného programu.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointUnboundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní jako součást jeho podporu pro zarážky. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, pokud vázaná zarážka byla nevázaná. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBreakpointUnboundEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Získá zarážku, která se stala nevázaný.|
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Získá důvod, proč zarážka byla nevázaná.|

## <a name="remarks"></a>Poznámky
 Při ladění modulu DLL nebo třídy uvolní, všechny zarážky, které byly vázány na kód v tomto modulu musí být bez závazků z programu, který je laděn. Je `IDebugBreakpointUnboundEvent2` odeslána pro každou nevázanou zarážku.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
