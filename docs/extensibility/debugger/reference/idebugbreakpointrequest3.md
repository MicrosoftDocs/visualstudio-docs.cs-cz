---
title: IDebugBreakpointRequest3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734831"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Toto rozhraní představuje informace potřebné k vytvoření a svázání jakéhokoli typu zarážky. Jedná se o rozšíření [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Správce ladění relace (SDM) obvykle implementuje toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Ladicí modul (DE) přistupuje k tomuto rozhraní voláním [queryinterface](/cpp/atl/queryinterface) v rozhraní IDebugBreakpointRequest2 přijatém ve volání [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)rozhraní `IDebugBreakpointRequest3` zpřístupňuje následující metodu.

|Metoda|Popis|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Získá informace o požadavku na zarážky, který popisuje tento požadavek na zarážky.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní slouží k poskytování dalšíinformace DE prostřednictvím [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury. Tyto další informace zahrnují ID dodavatele DE (ve formě identifikátoru GUID), název trasovacího bodu a název omezení zarážky.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
