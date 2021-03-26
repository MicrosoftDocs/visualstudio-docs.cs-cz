---
description: Nastaví nebo změní podmínku přidruženou k této vázané zarážce.
title: 'IDebugBoundBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 792c0464b6c1beced9903e3dc21783d1841ab455
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088871"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Nastaví nebo změní podmínku přidruženou k této vázané zarážce.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametry
`bpCondition`\
pro Hodnota z výčtu [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) , která popisuje podmínku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí, `E_BP_DELETED` zda je stav objektu vázaného bodu přerušení nastaven na hodnotu `BPS_DELETED` (součást výčtu [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Poznámky
 Veškerá podmínka, která byla dříve přidružena k této zarážce, bude ztracena.

## <a name="see-also"></a>Viz také
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
