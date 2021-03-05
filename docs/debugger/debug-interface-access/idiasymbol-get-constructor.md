---
description: Načte příznak, který určuje, zda uživatelem definovaný datový typ má konstruktor nebo destruktor.
title: 'IDiaSymbol:: get_constructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_constructor method
ms.assetid: 2f2cf1e0-f817-4ca0-b782-3341362c46a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca2162f9da71d42308feb44b15edcca77ad269df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156417"
---
# <a name="idiasymbolget_constructor"></a>IDiaSymbol::get_constructor
Načte příznak, který určuje, zda uživatelem definovaný datový typ má konstruktor nebo destruktor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_constructor ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda uživatelem definovaný datový typ má konstruktor nebo destruktor; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
