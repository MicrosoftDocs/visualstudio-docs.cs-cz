---
description: Nastaví zarovnání obrázku.
title: IDiaAddressMap::p ut_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c3027332018441efd132cc941d16aab3bcab594
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158366"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Nastaví zarovnání obrázku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

pro Nová hodnota zarovnání obrázku pro spustitelný soubor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Image (načtené spustitelné soubory) jsou zarovnané na zadané hranice paměti. Toto zarovnání může být ovlivněno aktuální architekturou systému a možnostmi kompilovat a propojit čas. Zarovnání obrázku je vždy na hranicích bajtů. Následující hodnoty zarovnání obrázku jsou platné: 1, 2, 4, 8, 16, 16, 32 a 64 bajtových hranic.

 Aktuální zarovnání obrázku lze načíst voláním metody [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> Bitová kopie je již načtena v době, kdy lze tuto metodu volat. `put_imageAlign`Metoda se obvykle používá, když se obrázek přesunul nebo změnil a vyžaduje se nové zarovnání.

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
