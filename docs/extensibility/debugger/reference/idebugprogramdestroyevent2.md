---
title: IDebugProgramDestroyEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2
helpviewer_keywords:
- IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc83e15372a15cefccc47ea60db5ba451546ecba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722588"
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
Toto rozhraní je odesláno ladicí modul (DE) do správce ladění relace (SDM) při spuštění programu do dokončení.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De nebo dodavatel vlastního portu implementuje toto rozhraní, aby oznámil, že program byl ukončen a již není k dispozici pro ladění. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 De nebo dodavatel vlastního portu vytvoří a odešle tento objekt události k nahlášení ukončení programu. DE odešle tuto událost pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm při připojení k programu, který je odladěn. Dodavatel vlastního portu odešle tuto událost pomocí rozhraní [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce je `IDebugProgramDestroyEvent2`uvedena metoda .

|Metoda|Popis|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Získá ukončovací kód programu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
