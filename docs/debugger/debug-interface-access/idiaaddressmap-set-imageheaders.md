---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745017"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Nastaví záhlaví obrázků pro povolení relativního překladu virtuálních adres.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parametry
 cbData

pro Počet bajtů dat záhlaví. Musí být `n*sizeof(IMAGE_SECTION_HEADER)`, kde `n` je počet hlaviček oddílu ve spustitelném souboru.

 data []

pro Pole `IMAGE_SECTION_HEADER` struktury, které se mají použít jako hlavičky obrázků.

 originalHeaders

pro Nastavte na `FALSE`, pokud se hlavičky imagí nacházejí v nové imagi, `TRUE` Pokud odrážejí původní image před upgradem. Obvykle by to bylo nastaveno na `TRUE` pouze v kombinaci s voláním metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Struktura `IMAGE_SECTION_HEADER` je deklarována v souboru Winnt. h a představuje formát záhlaví oddílu image pro spustitelný soubor.

 Relativní výpočty virtuálních adres závisí na hodnotách `IMAGE_SECTION_HEADER`. DIA je obvykle načítá ze souboru databáze programu (PDB). Pokud tyto hodnoty chybí, DIA nedokáže vypočítat relativní virtuální adresy a metoda [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) vrátí `FALSE`. Klient pak musí zavolat metodu [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) a povolit tak relativní výpočty virtuálních adres po poskytnutí chybějících záhlaví obrázků z samotné image.

## <a name="see-also"></a>Viz také:
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)