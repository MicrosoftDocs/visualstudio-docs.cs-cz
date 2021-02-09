---
title: LocationType – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5aafc62f5920db70bd881bd3a541cfcfabfac360
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862344"
---
# <a name="locationtype"></a>LocationType
Určuje druh informací o poloze obsažených v symbolu.

## <a name="syntax"></a>Syntax

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
`LocIsNull` Informace o poloze nejsou k dispozici.

`LocIsStatic` Umístění je statické.

`LocIsTLS` Umístění je v thread local Storage.

`LocIsRegRel` Umístění je relativní k registraci.

`LocIsThisRel` Umístění je `this` relativní.

`LocIsEnregistered` Umístění se nachází v registru.

`LocIsBitField` Umístění je bitové pole.

`LocIsSlot` Umístění je slot jazyka MSIL (Microsoft Intermediate Language).

`LocIsIlRel` Umístění je relativní vzhledem k jazyku MSIL.

`LocInMetaData` Umístění je v metadatech.

`LocIsConstant` Umístění je konstantní hodnota.

`LocTypeMax` Počet typů umístění v tomto výčtu.

## <a name="remarks"></a>Poznámky
Vlastnosti, které jsou k dispozici pro rozhraní [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , závisí na umístění symbolu v rámci souboru obrázku. Další informace naleznete v tématu [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md).

Hodnoty v tomto výčtu jsou vráceny voláním metody [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Požadavky
Záhlaví: cvconst. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)
