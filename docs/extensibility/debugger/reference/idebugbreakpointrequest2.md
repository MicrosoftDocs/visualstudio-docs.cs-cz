---
title: IDebugBreakpointRequest2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734912"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Toto rozhraní představuje informace potřebné k vytvoření a svázání jakéhokoli typu zarážky.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Správce ladění relace (SDM) obvykle implementuje toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí modul (DE) obdrží toto rozhraní prostřednictvím volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) za účelem vytvoření čekající zarážky. Volání [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) můžete načíst toto rozhraní z DE.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugBreakpointRequest2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Získá typ umístění zarážky tohoto požadavku na zarážku.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Získá informace o požadavku na zarážky, který popisuje tento požadavek na zarážky.|

## <a name="remarks"></a>Poznámky
 Po načtení programu, který je laděn, volání [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) váže čekající zarážku na požadované umístění v programu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Vytvořit vazbu](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
