---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745031"
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

pro Počet prvků v parametru `data`.

 `data[]`

pro Pole struktur [struktury DiaAddressMapEntry –](../../debugger/debug-interface-access/diaaddressmapentry.md) , které definují mapu překladu.

 `imagetoSymbols`

[in] `TRUE`, pokud parametr `data` definuje mapu z nového rozložení obrázku do původního rozložení (jak je popsáno v tématu symboly ladění). `FALSE`, pokud `data` je mapa k novému rozložení obrázku vytvořenému z původního rozložení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Obvykle DIA načítá mapy překladu adres ze souboru databáze programu (PDB). Pokud tyto hodnoty chybí, metoda [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se volá dvakrát, jednou s parametrem `imagetoSymbols` nastaveným na `TRUE` a jednou s parametrem `imagetoSymbols` nastaveným na `FALSE`. Překlady map adres nelze povolit pomocí metody [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , pokud nejsou k dispozici obě mapy překladu.

## <a name="see-also"></a>Viz také:
- [DiaAddressMapEntry – struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)