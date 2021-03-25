---
description: Vrátí další sadu prvků z výčtu vláken.
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 373cccd0b03efe1e4d65d1910b5b06f60ecb4ea1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082670"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugThread2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugThread2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.

`rgelt`\
[in, out] Pole [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) prvků, které se mají vyplnit

`pceltFetched`\
mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
