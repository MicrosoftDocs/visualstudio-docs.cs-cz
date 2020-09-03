---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4af506da822a7f8e38a8952d7c1d0d15fc1995d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468551"
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