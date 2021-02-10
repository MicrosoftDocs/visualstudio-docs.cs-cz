---
title: 'IDebugEventCallback2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54f53132f0a1f4769386874118d24f7e77a95f71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933307"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Odesílá oznámení o událostech ladění.

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
pro Objekt [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , který představuje ladicí stroj (de), který odesílá tuto událost. K vyplnění tohoto parametru je vyžadován DE.

`pProcess`\
pro Objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , který představuje proces, ve kterém dojde k události. Tento parametr vyplní Správce ladění relace (SDM). Hodnota DE vždy předá hodnotu null pro tento parametr.

`pProgram`\
pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, ve kterém k této události dojde. U většiny událostí tento parametr není hodnotou null.

`pThread`\
pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje vlákno, ve kterém k této události dochází. Pro zastavování událostí nemůže tento parametr hodnotu null, protože rámec zásobníku je získán z tohoto parametru.

`pEvent`\
pro Objekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , který představuje událost ladění.

`riidEvent`\
pro Identifikátor GUID, který určuje rozhraní události, které se má získat z `pEvent` parametru.

`dwAttrib`\
pro Kombinace příznaků z výčtu [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Při volání této metody `dwAttrib` musí parametr odpovídat hodnotě vrácené z metody [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) , jak je volána u objektu události předaného v `pEvent` parametru.

 Všechny události ladění jsou odesílány asynchronně bez ohledu na to, zda je událost sama o sobě nebo není asynchronní. Když metoda DE volá tuto metodu, návratová hodnota neurčuje, zda byla událost zpracována, a to pouze bez ohledu na to, zda byla událost přijata. Ve většině případů není událost zpracována při návratu této metody.

## <a name="see-also"></a>Viz také
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
