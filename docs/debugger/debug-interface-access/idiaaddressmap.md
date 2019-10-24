---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744982"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Poskytuje kontrolu nad tím, jak DIA SDK počítá virtuální a relativní virtuální adresy pro objekty ladění.

## <a name="syntax"></a>Syntaxe

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Následující tabulka ukazuje metody `IDiaAddressMap`.

|Metoda|Popis|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Označuje, zda bylo pro určitou relaci vytvořeno mapování adres.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Určuje, zda se má mapa adres použít k překladu adres symbolů.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Určuje, zda je povolen výpočet a použití relativních virtuálních adres.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Umožňuje klientovi povolit nebo zakázat výpočet relativních virtuálních adres.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Načte aktuální zarovnání obrázku.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Nastaví zarovnání obrázku.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Nastaví záhlaví imagí pro povolení překladu relativních virtuálních adres.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Poskytuje mapu adres pro podporu překladů rozložení obrázků.|

## <a name="remarks"></a>Poznámky
 Ovládací prvek poskytnutý tímto rozhraním je zapouzdřen ve dvou sadách dat, která zadáte: hlavičky obrázků a mapy adres. Většina klientů používá metodu [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) k vyhledání správných informací o ladění pro obrázek a metoda může obvykle zjistit všechny nezbytné hlavičky a data Maps. Někteří klienti však implementují specializované zpracování a hledání dat. Tito klienti používají metody rozhraní `IDiaAddressMap` k tomu, aby DIA SDK výsledky hledání.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je dostupné z objektu relace DIA. Klient volá metodu `QueryInterface` v rozhraní objektu relace DIA, obvykle [IDiaSession](../../debugger/debug-interface-access/idiasession.md), pro načtení rozhraní `IDiaAddressMap`.

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 Knihovna DLL: Msdia80. dll

## <a name="see-also"></a>Viz také:
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)