---
description: Toto rozhraní je odesláno ladicím modulem (DE) do nástroje Session Debug Manager (SDM) při načtení programu, ale před spuštěním jakéhokoli kódu.
title: IDebugLoadCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugLoadCompleteEvent2
helpviewer_keywords:
- IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 53351ca836658d55cdef1b793e0162b8573f6c6e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076924"
---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
Toto rozhraní je odesláno ladicím modulem (DE) do nástroje Session Debug Manager (SDM) při načtení programu, ale před spuštěním jakéhokoli kódu.

## <a name="syntax"></a>Syntax

```
IDebugLoadCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že byl program úspěšně načten. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, aby nahlásila, že byl program úspěšně načten. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojen k laděnému programu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
