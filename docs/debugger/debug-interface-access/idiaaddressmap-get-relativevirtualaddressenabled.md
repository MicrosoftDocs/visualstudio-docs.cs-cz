---
description: Označuje, zda je povolen výpočet a použití relativních virtuálních adres (RVA).
title: 'IDiaAddressMap:: get_relativeVirtualAddressEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5383772ca95d3dada7218643b483d2ca5d056613
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158425"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Označuje, zda je povolen výpočet a použití relativních virtuálních adres (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

mimo Vrátí, `TRUE` zda je povolen výpočet RVA.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 RVA jsou povoleny, pokud byly segmenty původně načteny ze souboru PDB. Použití RVA lze dočasně zakázat voláním metody [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) .

 Také je možné vytvořit nová záhlaví obrázků voláním metody [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) následované voláním `put_relativeVirtualAddressEnabled` metody pro povolení použití RVA pomocí nových hlaviček obrázků.

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
