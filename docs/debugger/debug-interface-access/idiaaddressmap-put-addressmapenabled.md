---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b671150463060f11dc62ea49d3a21cd388c6000
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468572"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Určuje, zda se má mapa adres použít k překladu adres symbolů.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

pro Nastavte na `TRUE` , chcete-li povolit překlad symbolů nebo `FALSE` zakázat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Spustitelné procesory někdy aktualizují spustitelný soubor. DIA obsahuje mechanismus pro podporu překladu symbolů na nové rozložení.

 Po načtení souboru PDB je povolena mapa adres uložená v souboru. Existují však situace, kdy může klientská aplikace potřebovat dodat vlastní mapu adresy voláním metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Pokud `set_addressMap` je metoda úspěšná, klientská aplikace musí zavolat `put_addressMapEnabled` metodu s `NewVal` parametrem `TRUE` pro povolení použití této mapy adres.

 Aktuální stav povoleného mapování adres lze načíst voláním metody [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Viz také
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)