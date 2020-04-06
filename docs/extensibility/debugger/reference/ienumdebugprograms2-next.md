---
title: IEnumDebugPrograms2::Další | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 035af638b9504318a39e01f34ed32719d957896e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715625"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[v] Počet prvků načíst. Také určuje maximální velikost `rgelt` pole.

`rgelt`\
[dovnitř, ven] Pole [iDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) prvky, které mají být vyplněny.

`pceltFetched`\
[out] Vrátí počet prvků skutečně `rgelt`vrácených v .

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud menší než požadovaný počet prvků mohou být vráceny; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
