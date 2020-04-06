---
title: IDebugEventCallback2::Událost | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b60c09b21d531326e343dddd2f1cc69cfb0e5d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729904"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Odešle oznámení o událostech ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>Parametry
`pEngine`\
[v] [Objekt IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) který představuje ladicí modul (DE), který odesílá tuto událost. K vyplnění tohoto parametru je nutné DE.

`pProcess`\
[v] [Objekt IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) který představuje proces, ve kterém dojde k události. Tento parametr je vyplněn správcem ladění relace (SDM). De de vždy předá hodnotu null pro tento parametr.

`pProgram`\
[v] [Objekt IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který představuje program, ve kterém dojde k této události. Pro většinu událostí tento parametr není nulovou hodnotou.

`pThread`\
[v] [Objekt IDebugThread2,](../../../extensibility/debugger/reference/idebugthread2.md) který představuje vlákno, ve kterém dojde k této události. Pro zastavení události tento parametr nemůže být nulovou hodnotu jako rámec zásobníku je získán z tohoto parametru.

`pEvent`\
[v] Objekt [IDebugEvent2,](../../../extensibility/debugger/reference/idebugevent2.md) který představuje událost ladění.

`riidEvent`\
[v] GUID, který určuje, které rozhraní `pEvent` události získat z parametru.

`dwAttrib`\
[v] Kombinace příznaků z výčtu [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Při volání této `dwAttrib` metody musí parametr odpovídat hodnotě vrácené z metody [GetAttributes,](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) jak je volána na objekt události předaný v parametru. `pEvent`

 Všechny ladicí události jsou zaúčtovány asynchronně, bez ohledu na to, zda je samotná událost asynchronní nebo ne. Při volání DE tuto metodu, vrácená hodnota neoznačuje, zda byla událost zpracována, pouze zda byla událost přijata. Ve skutečnosti ve většině případů událost nebyla zpracována při této metodě vrátí.

## <a name="see-also"></a>Viz také
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
