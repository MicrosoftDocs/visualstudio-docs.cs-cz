---
title: IEnumDebugCodeContexts2::Další | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6e54b44d9e0ece42b65bf12412d6906158bc7fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717284"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Vrátí další sadu prvků z výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[v] Počet prvků načíst. Také určuje maximální velikost `rgelt` pole.

`rgelt`\
[dovnitř, ven] Pole [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) prvky, které mají být vyplněny.

`pceltFetched`\
[out] Vrátí počet prvků skutečně `rgelt`vrácených v .

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud menší než požadovaný počet prvků mohou být vráceny; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
