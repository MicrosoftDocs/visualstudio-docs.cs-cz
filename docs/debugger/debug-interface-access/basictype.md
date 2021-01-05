---
title: Basictype – | Microsoft Docs
description: Vyhledejte referenční informace o výčtu Basictype –, který určuje základní typ symbolu v sadě Visual Studio Debug Interface Access SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 27fd166b094f74cfbf9b6a37a87804031dedcbc7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728874"
---
# <a name="basictype"></a>BasicType
Určuje základní typ symbolu.

## <a name="syntax"></a>Syntax

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

btVoid je základní typ `void` .

btChar Basic je typ `char` (C/C++).

btWChar Basic Type je roztažitelné znak (Unicode) ( `WCHAR` ).

btInt Basic Type `signed int` (typ C/C++).

btUInt Basic Type `unsigned int` (typ C/C++).

btFloat Basic Type je číslo s plovoucí desetinnou čárkou ( `FLOAT` ).

btBCD Basic Type je binární kódované číslo ( `BCD` ).

btBool základní typ je logická hodnota ( `BOOL` ).

btLong Basic je typ `long int` (C/C++).

btULong Basic Type je typ `unsigned long int` (C/C++).

btCurrency je základní typ Měna.

btDate je základní typ datum a čas ( `DATE` ).

btVariant Basic Type je struktura typu proměnné ( `VARIANT` ).

Základní typ btComplex je komplexní číslo.

btBit základní typ je bit.

btBSTR Basic Type je základní nebo binární řetězec ( `BSTR` ).

btHresult je základní typ `HRESULT` .

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
