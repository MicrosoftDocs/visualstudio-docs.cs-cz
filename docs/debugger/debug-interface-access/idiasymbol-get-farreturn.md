---
description: Načte příznak, který určuje, zda funkce obsahuje zcela návrat.
title: 'IDiaSymbol:: get_farReturn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_farReturn method
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bebf0d1f61c6cf1dc21528e44703de049d247c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156340"
---
# <a name="idiasymbolget_farreturn"></a>IDiaSymbol::get_farReturn
Načte příznak, který určuje, zda funkce obsahuje zcela návrat.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_farReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

pro Vrátí `TRUE` , zda funkce používá zcela vrácenou hodnotu, jinak vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
