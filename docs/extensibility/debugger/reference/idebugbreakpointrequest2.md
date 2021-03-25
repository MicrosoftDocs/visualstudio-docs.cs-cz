---
description: Rozhraní IDebugBreakPointRequest2 představuje informace potřebné k vytvoření a svázání libovolného typu zarážky.
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8788e7a78bcd4c03567e5d07c96a310fa6970fb1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054449"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Toto rozhraní představuje informace potřebné k vytvoření a svázání libovolného typu zarážky.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní obvykle implementuje správce ladění relace (SDM).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí stroj (DE) obdrží toto rozhraní prostřednictvím volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , aby bylo možné vytvořit nevyřízenou zarážku. Volání [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) může získat toto rozhraní z de.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugBreakpointRequest2` .

|Metoda|Popis|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Získá typ umístění zarážky této žádosti o zarážku.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Získá informace o požadavku zarážky, které popisují tuto žádost o zarážku.|

## <a name="remarks"></a>Poznámky
 Po načtení programu, který se právě ladí, se volání metody [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) váže na nevyřízenou zarážku na požadované místo v programu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Zapisovat](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
