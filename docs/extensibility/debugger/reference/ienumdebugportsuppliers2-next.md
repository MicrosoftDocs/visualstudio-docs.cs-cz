---
title: IEnumDebugPortSuppliers2::Další | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78fa25ee4155d646d1be2cd73fa86773e767c649
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716019"
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
[v] Počet prvků načíst. Také určuje maximální velikost `rgelt` pole.

`rgelt`\
[dovnitř, ven] Pole [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) prvky, které mají být vyplněny.

`pceltFetched`\
[out] Vrátí počet prvků skutečně `rgelt`vrácených v .

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud menší než požadovaný počet prvků mohou být vráceny; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
