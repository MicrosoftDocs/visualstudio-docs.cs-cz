---
description: Načte aktuální zarovnání obrázku.
title: 'IDiaAddressMap:: get_imageAlign | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: daf52fa451c690445778258400f68ad95cc91f3c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151153"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Načte aktuální zarovnání obrázku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí hodnotu zarovnání obrázku ze spustitelného souboru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Obrázky jsou zarovnané na konkrétní hranice paměti v závislosti na tom, jak byl obrázek načten a vytvořen. Zarovnání je obvykle na 1, 2, 4, 8, 16, 32 nebo 64 bajtových hranic. Zarovnání obrázku lze nastavit voláním metody [IDiaAddressMap::p ut_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) .

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
