---
description: Označuje, zda bylo pro určitou relaci vytvořeno mapování adres.
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a55ff89e97d1898ec2ced2b62f7cdfa5a0df817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149107"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Označuje, zda bylo pro určitou relaci vytvořeno mapování adres.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

mimo Vrátí `TRUE` , zda je povoleno mapování adres.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Spustitelné procesory někdy aktualizují spustitelný soubor. DIA obsahuje mechanismus pro podporu překladu symbolů na nové rozložení.

 Klientské aplikace mohou nastavit mapu adres pro konkrétní relaci získáním rozhraní [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) z rozhraní [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a voláním metody [IDiaAddressMap:: Set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) následované voláním metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . `get_addressMapEnabled`Metoda vrátí výsledky volání `put_addressMapEnabled` metody.

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
