---
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e6311c0db3329852fe8061c8da9f0355d6b2565
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865283"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Umožňuje klientovi povolit nebo zakázat výpočet a použití relativních virtuálních adres (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

pro Nastavte na `TRUE` Povolit nebo `FALSE` zakázat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Adresy pro objekty ladění, které jsou popsány rozhraními DIA a relativní vzhledem k základu obrázku spustitelného souboru, lze načíst jako relativní virtuální adresy.

 Použití RVA je povoleno, když jsou segmenty zpočátku načteny ze souboru PDB. Chcete-li získat aktuální stav použití RVA, zavolejte metodu [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .

 `put_relativeVirtualAddress`Metoda musí být volána, aby bylo možné povolit RVA po úspěšném volání metody [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se vytvořila nová záhlaví obrázků.

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)