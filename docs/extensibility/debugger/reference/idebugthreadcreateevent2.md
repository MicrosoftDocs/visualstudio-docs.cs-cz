---
title: IDebugThreadCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadCreateEvent2
helpviewer_keywords:
- IDebugThreadCreateEvent2
ms.assetid: aee34a14-4f9c-4ad3-845f-c96ee938cefd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1aaa25e719f17701344d821759a0dac06aa88698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718536"
---
# <a name="idebugthreadcreateevent2"></a>IDebugThreadCreateEvent2
Toto rozhraní se odesílá ladicím modulem (DE) do nástroje Session Debug Manager (SDM), když je v laděném programu vytvořen podproces.

## <a name="syntax"></a>Syntax

```
IDebugThreadCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že bylo vytvořeno vlákno. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [QueryInterface](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, aby nahlásila, že bylo vlákno vytvořeno. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
