---
title: IEnumDebugFields::Přeskočit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4c08e9291d6aad2801ada8d427adc198d6bc5e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716812"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
Tato metoda přeskočí zadaný počet prvků.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametry
`celt`\
[v] Počet prvků přeskočit.

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . `S_FALSE` Vrátí, `celt` pokud je větší než počet zbývajících prvků; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud `celt` určuje hodnotu větší než počet zbývajících prvků, výčet je `S_FALSE` nastavena na konec a je vrácena.

## <a name="see-also"></a>Viz také
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
