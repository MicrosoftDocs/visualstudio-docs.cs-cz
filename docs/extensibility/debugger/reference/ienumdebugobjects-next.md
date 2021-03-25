---
description: Tato metoda vrací další sadu IDebugObject prvků z výčtu.
title: 'IEnumDebugObjects:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 661d95f2196787502ab0ce144f6a7490c9911eca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064566"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Tato metoda vrací další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.

`rgelt`\
[in, out] Pole [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) prvků, které se mají vyplnit

`pceltFetched`\
mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
