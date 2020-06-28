---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e23f5752229ece7ecac02362c294bc661d109039
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468593"
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