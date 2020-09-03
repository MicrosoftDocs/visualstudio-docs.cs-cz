---
title: Datakind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2423646976744da17d3e904246ac74f8b2e75f41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468705"
---
# <a name="datakind"></a>DataKind
Označuje konkrétní rozsah hodnoty dat.

## <a name="syntax"></a>Syntax

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementy
Nelze určit DataIsUnknown datový symbol.

Datová položka DataIsLocal je místní proměnná.

Datová položka DataIsStaticLocal je statická lokální proměnná.

Položka DataIsParam data je formální parametr.

Položka dat DataIsObjectPtr je ukazatel objektu ( `this` ).

Datová položka DataIsFileStatic je proměnná s rozsahem souboru.

Datová položka DataIsGlobal je globální proměnná.

Položka dat DataIsMember je proměnná člen objektu.

Datová položka DataIsStaticMember je statická proměnná třídy.

Datová položka DataIsConstant je konstantní hodnota.

## <a name="remarks"></a>Poznámky
Hodnoty v tomto výčtu jsou vráceny metodou [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
