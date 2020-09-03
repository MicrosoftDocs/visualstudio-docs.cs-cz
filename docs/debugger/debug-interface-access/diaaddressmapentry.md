---
title: DiaAddressMapEntry – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 8cae8159c893229f02e9598e932d7bc19efc2f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468677"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Popisuje položku v mapě adres.

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementy
`rva` Relativní virtuální adresa (RVA) v imagi A.

`rvaTo` Relativní virtuální adresa `rva` je namapována na v imagi B.

## <a name="remarks"></a>Poznámky
Mapa adres poskytuje překlad z jednoho rozložení obrázku (A) na jiný (B). Pole `DiaAddressMapEntry` struktur seřazené podle `rva` definuje mapu adres.

K překladu adresy, `addrA` v imagi a na adresu, `addrB` v imagi B proveďte následující kroky:

1. Vyhledá v mapě položku, `e` která má největší velikost `rva` menší než nebo rovna `addrA` .

2. Nastavit `delta = addrA - e.rva` .

3. Nastavit `addrB = e.rvaTo + delta` .

    `DiaAddressMapEntry`Do metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) se předává pole struktur.

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

## <a name="see-also"></a>Viz také
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
