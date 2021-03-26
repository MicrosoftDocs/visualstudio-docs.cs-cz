---
description: Toto rozhraní oznamuje správci ladění relace (SDM), že asynchronní přerušení bylo úspěšně dokončeno.
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d2369b2219d155b2210fb2860cc868ec3813bad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088793"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Toto rozhraní oznamuje správci ladění relace (SDM), že asynchronní přerušení bylo úspěšně dokončeno.

## <a name="syntax"></a>Syntax

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní pro podporu přerušení uživatele v programu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se musí implementovat na stejný objekt jako toto rozhraní (SDM používá pro přístup k rozhraní [QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` .).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání SDM zavolá [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) , když si uživatel vyžádá, aby byl program laděn. Po úspěšném pozastavení programu zruší událost DE zprávu `IDebugBreakEvent2` . Tato událost se posílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , kterou poskytuje služba SDM, když je připojená k laděnému programu.

## <a name="remarks"></a>Poznámky
 Uživatel může například vybrat příkaz **Break All** v nabídce **ladění** pro přerušení programu, na kterém běží nekonečné smyčky. Model SDM oznamuje programu zastavení voláním [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). DE pošle, `IDebugBreakEvent2` když se program nakonec zastaví.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
