---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae9e10da02ab0bbef6be0fed5b9d505bf1b3e268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892668"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Povolí (nebo zakáže) vyhodnocení výrazu v daném vlákně, i když se program zastavil.

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
pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) představující program, který vyhodnocuje výraz.

`dwTid`\
pro Určuje identifikátor vlákna.

`dwEvalFlags`\
pro Kombinace příznaků z výčtu [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , která určuje, jak má být provedeno vyhodnocení.

`pExprCallback`\
pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který se má použít k odeslání událostí ladění, ke kterým dojde při vyhodnocování výrazu.

`fWatch`\
pro Pokud je nenulová ( `TRUE` ), umožňuje vyhodnocení výrazu na vlákně identifikovaném `dwTid` . v opačném případě nula ( `FALSE` ) zakáže vyhodnocení výrazu v tomto vlákně.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když správce ladění relace (SDM) požádá o program označený `pOriginatingProgram` parametrem, aby vyhodnotil výraz, upozorní všechny ostatní připojené programy voláním této metody.

 Vyhodnocení výrazu v jednom programu může způsobit, že se kód spustí v jiném z důvodu vyhodnocení funkce nebo vyhodnocení jakýchkoli `IDispatch` vlastností. Z tohoto důvodu umožňuje tato metoda vyhodnocení výrazu spustit a dokončit, i když je vlákno v tomto programu možné zastavit.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
