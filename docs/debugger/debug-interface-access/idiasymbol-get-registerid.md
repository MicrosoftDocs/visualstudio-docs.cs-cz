---
title: 'IDiaSymbol:: get_registerId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f252d02a137ada627c0c546e1f1ac79118f76de9
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462474"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Načte specifikátor registrace umístění, pokud je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) nastaven na hodnotu `LocIsEnregistered` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí specifikátor registrace umístění.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Pokud je symbol relativní vzhledem k registru, to znamená, že pokud je [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) symbolu nastaven na `LocIsRegRel` , použijte `get_registerId` metodu následovanou voláním metody [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) pro získání posunu od registru, kde je symbol umístěn.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)