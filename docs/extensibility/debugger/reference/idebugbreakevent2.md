---
title: IDebugBreakEvent2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735402"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Toto rozhraní informuje správce ladění relace (SDM), že asynchronní přerušení bylo úspěšně dokončeno.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní pro podporu přerušení uživatele v programu. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 SDM volá [CauseBreak,](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) když uživatel požádal program, který je laděn, aby byl pozastaven. Po úspěšném pozastavení programu de odešle `IDebugBreakEvent2` událost. Tato událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="remarks"></a>Poznámky
 Uživatel může například vybrat příkaz **Přerušit vše** v nabídce **Ladění** a vymanit se z programu, který je spuštěn nekonečnou smyčkou. SDM říká program zastavit voláním [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). De odešle, `IDebugBreakEvent2` když program nakonec zastaví.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
