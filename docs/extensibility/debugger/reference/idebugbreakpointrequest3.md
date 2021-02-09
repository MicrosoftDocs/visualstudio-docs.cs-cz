---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6e42111ca0c8b357a7f8841511cf935694a30b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893058"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Toto rozhraní představuje informace potřebné k vytvoření a svázání libovolného typu zarážky. Jedná se o rozšíření [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní obvykle implementuje správce ladění relace (SDM).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí stroj (DE) přistupuje k tomuto rozhraní voláním [QueryInterface](/cpp/atl/queryinterface) na rozhraní IDebugBreakpointRequest2 přijatém voláním [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) `IDebugBreakpointRequest3` rozhraní zpřístupňuje následující metodu.

|Metoda|Popis|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Získá informace o požadavku zarážky, které popisují tuto žádost o zarážku.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní se používá k poskytnutí dalších informací do DE prostřednictvím [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury. Tyto další informace zahrnují ID dodavatele DE (ve formě identifikátoru GUID), název zarážka s trasováním a název omezení zarážky.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
