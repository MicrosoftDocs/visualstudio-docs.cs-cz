---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734749"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Toto rozhraní představuje informace, které popisují vázanou zarážku.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory zarážek. Toto rozhraní poskytuje popis vázané zarážky, kterou správce ladění relace používá, když uživatel zobrazí vlastnosti zarážky.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní vrátí volání [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugBreakpointResolution2` .

|Metoda|Popis|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Získá typ zarážky reprezentované tímto řešením.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Získá informace o rozlišení zarážky, které popisují tuto zarážku.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
