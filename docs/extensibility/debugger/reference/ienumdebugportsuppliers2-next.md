---
title: 'IEnumDebugPortSuppliers2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04f1b428f76198c0bb06ae6d12c58d5f779a0e79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846735"
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                 celt,
   IDebugPortSupplier2** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   IDebugPortSupplier2[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.

`rgelt`\
[in, out] Pole [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) prvků, které se mají vyplnit

`pceltFetched`\
mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
