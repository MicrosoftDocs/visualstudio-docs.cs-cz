---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735402"
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
