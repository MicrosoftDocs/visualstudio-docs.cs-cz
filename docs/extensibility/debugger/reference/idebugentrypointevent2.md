---
description: Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), když se program chystá spustit první instrukci uživatelského kódu.
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da733292407c93327374a4c6fa54c558d3202caa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153388"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), když se program chystá spustit první instrukci uživatelského kódu.

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní jako součást běžných operací. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, když se ladicí program načetl a je připravený spustit první instrukci uživatelského kódu. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojen k laděnému programu.

## <a name="remarks"></a>Poznámky
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) se pošle, když se program chystá spustit velmi první pokyn. Například `IDebugEntryPoint2` se pošle, když se program chystá spustit `main` funkci uživatele.

 Když DE pošle `IDebugEntryPointEvent2` , aktuální pozice kódu by měla být první instrukcí uživatelského kódu, třeba `main` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
