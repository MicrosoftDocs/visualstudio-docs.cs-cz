---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730372"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Umožňuje (nebo zakáže) vyhodnocení výrazu dojít v daném vlákně, i v případě, že program byl zastaven.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parametry
`pOriginatingProgram`\
[v] [Objekt IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) představující program, který vyhodnocuje výraz.

`dwTid`\
[v] Určuje identifikátor vlákna.

`dwEvalFlags`\
[v] Kombinace příznaků z výčtu [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) které určují, jak má být hodnocení provedeno.

`pExprCallback`\
[v] [Objekt IDebugCallBackback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) který má být použit k odeslání ladicí události, ke kterým dochází během vyhodnocení výrazu.

`fWatch`\
[v] Pokud nenulová`TRUE`( ), umožňuje vyhodnocení `dwTid`výrazu na vlákno označené ; jinak nula`FALSE`( ) zakazuje vyhodnocení výrazu v tomto vlákně.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když správce ladění relace (SDM) požádá program, `pOriginatingProgram` identifikovaný parametrem, vyhodnotit výraz, upozorní všechny ostatní připojené programy voláním této metody.

 Vyhodnocení výrazu v jednom programu může způsobit spuštění kódu v `IDispatch` jiném programu z důvodu vyhodnocení funkce nebo vyhodnocení všech vlastností. Z tohoto důvodu tato metoda umožňuje vyhodnocení výrazu spustit a dokončit i v případě, že vlákno může být zastavenv tomto programu.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
