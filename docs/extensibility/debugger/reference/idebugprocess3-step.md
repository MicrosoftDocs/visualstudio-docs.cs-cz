---
description: Způsobí, že proces krokuje jednu instrukci nebo příkaz.
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85df970c073fa2203873733073c5b6b85cabe06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150130"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Způsobí, že proces krokuje jednu instrukci nebo příkaz.

> [!NOTE]
> Tato metoda by se měla použít místo [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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
pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , který představuje povýšení vlákna.

`sk`\
pro Jedna z hodnot [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)

`step`\
pro Jedna z hodnot [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V případě, že dojde ke synchronizaci vlákna nebo komunikaci mezi vlákny, by se měly spouštět další vlákna v procesu, když konkrétní vlákno krokuje.

 **Upozornění** Neodesílat událost zastavení nebo okamžitou (synchronní) událost k [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) během zpracování tohoto volání; v opačném případě může ladicí program přestat reagovat.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
