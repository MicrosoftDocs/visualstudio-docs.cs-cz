---
description: Přeskočí na zadaný počet DEBUG_PROPERTY_INFO prvků.
title: 'IEnumDebugPropertyInfo2:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Skip
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Skip
ms.assetid: 0366c778-18eb-4065-a452-64b70c751a58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f519d3a0163b7afdf15c254b450c24686d80b417
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082865"
---
# <a name="ienumdebugpropertyinfo2skip"></a>IEnumDebugPropertyInfo2::Skip
Přeskočí na zadaný počet prvků.

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
pro Počet prvků, které se mají přeskočit

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí, `S_FALSE` Pokud `celt` je větší než počet zbývajících prvků. v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud `celt` Určuje hodnotu větší než počet zbývajících prvků, je výčet nastaven na konec a `S_FALSE` je vrácen.

## <a name="see-also"></a>Viz také
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
