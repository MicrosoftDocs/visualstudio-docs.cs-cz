---
title: Basictype – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745481"
---
# <a name="basictype"></a>BasicType
Určuje základní typ symbolu.

## <a name="syntax"></a>Syntaxe

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementy
btNoType není zadán žádný základní typ.

btVoid Basic Type je `void`.

btChar Basic Type je `char` (C/C++ typ).

btWChar Basic Type je roztažitelné znak (Unicode) (`WCHAR`).

btInt Basic Type je `signed int` (C/C++ typ).

btUInt Basic Type je `unsigned int` (C/C++ typ).

btFloat Basic Type je číslo s plovoucí desetinnou čárkou (`FLOAT`).

btBCD Basic Type je binární kódované číslo (`BCD`).

btBool Basic Type je logická hodnota (`BOOL`).

btLong Basic Type je `long int` (C/C++ typ).

btULong Basic Type je `unsigned long int` (C/C++ typ).

btCurrency je základní typ Měna.

btDate je základní typ datum a čas (`DATE`).

btVariant Basic Type je struktura typu proměnné (`VARIANT`).

Základní typ btComplex je komplexní číslo.

btBit základní typ je bit.

btBSTR Basic Type je základní nebo binární řetězec (`BSTR`).

btHresult Basic Type je `HRESULT`.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
