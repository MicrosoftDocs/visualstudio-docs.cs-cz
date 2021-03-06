---
description: Toto rozhraní slouží ke komunikaci s kritickými ladicími informacemi, jako je například zastavení na zarážce, a nekritické informace, jako je například zpráva ladění.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5406c70703b594236dba47539e5cc76bbe67a73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065759"
---
# <a name="idebugevent2"></a>IDebugEvent2
Toto rozhraní slouží ke komunikaci s kritickými ladicími informacemi, jako je například zastavení na zarážce, a nekritické informace, jako je například zpráva ladění.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Modul ladění (DE) a vlastní dodavatel portu implementují toto rozhraní na stejném objektu jako všechna ostatní rozhraní událostí.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí argumentu ID rozhraní (IID) daného pro [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) nebo [událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)zavolá Správce ladění relace (SDM) na rozhraní metodu [QueryInterface](/cpp/atl/queryinterface) , `IDebugEvent2` aby získala příslušné rozhraní události.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Získá atributy pro tuto událost ladění.|

## <a name="remarks"></a>Poznámky
 Konkrétnější rozhraní události, jako je [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), se neodvozují z rozhraní IDebugEvent2, ale místo toho se implementují jako samostatné rozhraní stejného objektu jako `IDebugEvent2` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
