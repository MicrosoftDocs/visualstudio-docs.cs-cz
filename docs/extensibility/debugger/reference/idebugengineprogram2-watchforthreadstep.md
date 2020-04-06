---
title: IDebugEngineProgram2::WatchForThreadStep | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730351"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Hodinky pro provádění (nebo přestane sledovat pro spuštění) dojít v daném vlákně.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parametry
`pOriginatingProgram`\
[v] [Objekt IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) představující krokování programu.

`dwTid`\
[v] Určuje identifikátor vlákna, které chcete sledovat.

`fWatch`\
[v] Nenulová`TRUE`( ) znamená začít sledovat provádění `dwTid`na vlákno označené ; jinak nula`FALSE`( ) znamená `dwTid`zastavit sledování pro spuštění na .

`dwFrame`\
[v] Určuje index rámce, který řídí typ kroku. Pokud je tato hodnota nula (0), typ kroku je "krok do" `dwTid` a program by měl zastavit vždy, když vlákno identifikované spuštěním. Pokud `dwFrame` je nenulová, typ kroku je "krok přes" a program `dwTid` by měl zastavit pouze v případě, že vlákno `dwFrame`identifikované podle je spuštěn v rámci, jehož index je rovna nebo vyšší v zásobníku než .

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když správce ladění relace (SDM) provede kroky `pOriginatingProgram` programu, identifikovaného parametrem, upozorní všechny ostatní připojené programy voláním této metody.

 Tato metoda je použitelná pouze pro krokování stejného vlákna.

## <a name="see-also"></a>Viz také
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
