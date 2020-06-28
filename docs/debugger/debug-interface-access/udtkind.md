---
title: Udtkind – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 746ff69de6f58f85d16982522c6ac13dcbf4ce6a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460970"
---
# <a name="udtkind"></a>UdtKind
Popisuje nejrůznější uživatelsky definované typy (UDT).

## <a name="syntax"></a>Syntax

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elementy
UdtStruct UDT je struktura.

UdtClass UDT je třída.

UdtUnion UDT je sjednocení.

UdtInterface UDT je rozhraní.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
