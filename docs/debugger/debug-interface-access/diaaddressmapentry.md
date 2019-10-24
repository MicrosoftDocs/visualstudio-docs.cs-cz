---
title: DiaAddressMapEntry – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745254"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Popisuje položku v mapě adres.

## <a name="syntax"></a>Syntaxe

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementy
`rva` relativní virtuální adresu (RVA) v imagi A.

`rvaTo` relativní virtuální adresa `rva` je namapovaná na Image B.

## <a name="remarks"></a>Poznámky
Mapa adres poskytuje překlad z jednoho rozložení obrázku (A) na jiný (B). Pole `DiaAddressMapEntry` struktury seřazené podle `rva` definuje mapu adres.

Chcete-li přeložit adresu, `addrA` v imagi A na adresu `addrB` v imagi B proveďte následující kroky:

1. Vyhledejte v mapě položku `e` s největším `rva`ou menší nebo rovnou `addrA`.

2. Nastavte `delta = addrA - e.rva`.

3. Nastavte `addrB = e.rvaTo + delta`.

    Do metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) se předává pole struktur `DiaAddressMapEntry`.

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

## <a name="see-also"></a>Viz také:
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
