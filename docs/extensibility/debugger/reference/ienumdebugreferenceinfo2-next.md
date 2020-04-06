---
title: IEnumDebugReferenceInfo2::Další | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Next
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Next
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb10504b2dbe02856364baa0670a7c825ef80cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715329"
---
# <a name="ienumdebugreferenceinfo2next"></a>IEnumDebugReferenceInfo2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                   celt,
   DEBUG_REFERENCE_INFO ** rgelt,
   ULONG*                  pceltFetched
);
```

```csharp
int Next(
   uint                   celt,
   DEBUG_REFERENCE_INFO[] rgelt,
   ref uint               pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[v] Počet prvků načíst. Také určuje maximální velikost `rgelt` pole.

`rgelt`\
[dovnitř, ven] Pole [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) prvků, které mají být vyplněny.

`pceltFetched`\
[out] Vrátí počet prvků skutečně `rgelt`vrácených v .

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud menší než požadovaný počet prvků mohou být vráceny; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
