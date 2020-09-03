---
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931be468f6321250481aec79688f7f326abcfcac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725246"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Tato metoda odesílá události, které signalizují vytvoření a zničení procesů a programů na portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Event(
   IDebugCoreServer2* pServer,
   IDebugPort2*       pPort,
   IDebugProcess2*    pProcess,
   IDebugProgram2*    pProgram,
   IDebugEvent2*      pEvent,
   REFIID             riidEvent
);
```

```csharp
int Event(
   IDebugCoreServer2 pServer,
   IDebugPort2       pPort,
   IDebugProcess2    pProcess,
   IDebugProgram2    pProgram,
   IDebugEvent2      pEvent,
   ref Guid          riidEvent
);
```

## <a name="parameters"></a>Parametry
`pMachine`\
pro Objekt [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , který představuje ladicí Server (pro každou instanci [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ), ve kterém došlo k události, je jeden.

`pPort`\
pro Objekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , který představuje port, ve kterém došlo k události.

`pProcess`\
pro Objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , který představuje proces, ve kterém došlo k události.

`pProgram`\
pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, ve kterém došlo k události.

`pEvent`\
pro Objekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , který identifikuje událost. Možné události jsou následující:

- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)

- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)

- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

`riidEvent`\
pro Identifikátor GUID události Vzhledem k tomu, že je událost přetypování na [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) před voláním této metody, tento identifikátor usnadňuje určení, která událost se posílá.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
