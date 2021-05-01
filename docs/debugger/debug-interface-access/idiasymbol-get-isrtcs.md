---
description: Načte hodnotu, která určuje, zda byla funkce kompilována s kontrolou chyb za běhu rámce zásobníku. Toto je příznak/RTCs.
title: 'IDiaSymbol:: get_isRTCs | Microsoft Docs'
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a297abe6326af6f04058e6095f59f880f526adb
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217225"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol:: get_isRTCs

Vrátí hodnotu, která určuje, zda byla funkce kompilována s kontrolou chyb za běhu rámce zásobníku. Toto je příznak/RTCs.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry

 `pRetVal`

mimo Ukazatel na LOGICKou hodnotu, která určuje, zda byla funkce kompilována s kontrolou chyb za běhu rámce zásobníku.

## <a name="return-value"></a>Návratová hodnota

 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky

Tato metoda je podporována počínaje verzí Visual Studio 2019 verze 16,10 Preview 2.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
