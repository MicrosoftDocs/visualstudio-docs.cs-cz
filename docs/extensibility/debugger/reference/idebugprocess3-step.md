---
title: IDebugProcess3::Krok | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5c4927f3f997b7fdbdca2b32977f2aa31a51219
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723549"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Způsobí, že proces krok jeden instrukce nebo příkaz.

> [!NOTE]
> Tato metoda by měla být použita namísto [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parametry
`pThread`\
[v] [Objekt IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) představující krokování vlákna.

`sk`\
[v] Jedna z hodnot [STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[v] Jedna z hodnot [STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V případě, že existuje synchronizace vláken nebo komunikace mezi vlákny, ostatní vlákna v procesu by měla být spuštěna, když je určité vlákno krokování.

 **Upozornění** Neodesílejte událost zastavení nebo okamžitou (synchronní) událost na [událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) při zpracování tohoto hovoru; jinak může zavěsit ladicí program.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
