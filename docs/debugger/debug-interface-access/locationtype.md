---
title: LocationType – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738639"
---
# <a name="locationtype"></a>LocationType
Určuje druh informací o poloze obsažených v symbolu.

## <a name="syntax"></a>Syntaxe

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elementy
informace o umístění `LocIsNull` nejsou k dispozici.

Umístění `LocIsStatic` je statické.

Umístění `LocIsTLS` se nachází v thread localm úložišti.

Umístění `LocIsRegRel` je relativní k registraci.

Umístění `LocIsThisRel` je `this` relativní.

Umístění `LocIsEnregistered` se nachází v registru.

Umístění `LocIsBitField` se nachází v bitovém poli.

Umístění `LocIsSlot` je slot jazyka MSIL (Microsoft Intermediate Language).

Umístění `LocIsIlRel` je relativní vzhledem k jazyku MSIL.

Umístění `LocInMetaData` se nachází v metadatech.

Umístění `LocIsConstant` se nachází v konstantní hodnotě.

`LocTypeMax` počet typů umístění v tomto výčtu.

## <a name="remarks"></a>Poznámky
Vlastnosti, které jsou k dispozici pro rozhraní [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , závisí na umístění symbolu v rámci souboru obrázku. Další informace naleznete v tématu [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md).

Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)
