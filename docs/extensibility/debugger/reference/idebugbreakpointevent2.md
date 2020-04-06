---
title: IDebugBreakpointEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f59bdef49f5c7b9c4dc345ba1862f3f08042428e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735024"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
Ladicí modul (DE) odešle toto rozhraní správci ladění relace (SDM), když se program zastaví na zarážky.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní jako součást jeho podporu pro zarážky. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, pokud je v programu zjištěna alespoň jedna zarážka. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBreakpointEvent2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Vytvoří čítač výčtu pro všechny zarážky, které jsou aktivovány v aktuálním umístění kódu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
