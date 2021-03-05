---
description: Určuje typy převodů.
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8d9fe78eedd0166594daf43093aa525e3d8d3e88
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161590"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Určuje typy převodů.

## <a name="syntax"></a>Syntax

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Elementy
THUNK_ORDINAL_NOTYPE standardní převolání.

THUNK_ORDINAL_ADJUSTOR pomocí `this` kódu pro úpravy.

THUNK_ORDINAL_VCALL virtuální volání.

THUNK_ORDINAL_PCODE P-code převod.

THUNK_ORDINAL_LOAD opožděné načtení.

THUNK_ORDINAL_TRAMP_INCREMENTAL přírůstkové Trampoline převodu (Trampoline převodu se používá pro odskok volání z jednoho paměťového prostoru na jiný).

THUNK_ORDINAL_TRAMP_BRANCHISLAND trampoliney bodu větve.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny ze volání metody [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
