---
description: Poskytuje mapu adres pro podporu překladů rozložení obrázků.
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9b00147f4ea8b2313e49e86795c36ec33aae9f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158306"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Poskytuje mapu adres pro podporu překladů rozložení obrázků.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

pro Počet prvků v `data` parametru.

 `data[]`

pro Pole struktur [struktury DiaAddressMapEntry –](../../debugger/debug-interface-access/diaaddressmapentry.md) , které definují mapu překladu.

 `imagetoSymbols`

[in] `TRUE` Pokud `data` parametr definuje mapování z nového rozložení obrázku do původního rozložení (jak je popsáno v tématu symboly ladění). `FALSE` Pokud `data` je mapa k novému rozložení obrázku z původního rozložení provedena.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Obvykle DIA načítá mapy překladu adres ze souboru databáze programu (PDB). Pokud tyto hodnoty chybí, metoda [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) je volána dvakrát, jednou s `imagetoSymbols` parametrem nastaveným na `TRUE` a jednou s `imagetoSymbols` parametrem nastaveným na `FALSE` . Překlady map adres nelze povolit pomocí metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , pokud nejsou k dispozici obě mapy překladu.

## <a name="see-also"></a>Viz také
- [DiaAddressMapEntry – struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
