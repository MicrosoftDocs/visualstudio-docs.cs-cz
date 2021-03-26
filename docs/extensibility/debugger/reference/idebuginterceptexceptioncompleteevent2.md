---
description: Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když DE dokončí zpracování zachycené události.
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6902382a94beaa983ee97ebb63223e5bdfa1645f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091809"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když DE dokončí zpracování zachycené události.

## <a name="syntax"></a>Syntax

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo, že zpracování zachycené výjimky bylo dokončeno. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, aby nahlásil dokončení zachycené výjimky. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojen k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 `IDebugInterceptExceptionCompleteEvent2`Rozhraní implementuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Vrací jedinečnou hodnotu přidruženou k ošetřené výjimce.|

## <a name="remarks"></a>Poznámky
 Tato událost bude odeslána serverem [InterceptCurrentException –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) , pokud tato metoda úspěšně dokončila zpracování zachycené výjimky.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
