---
description: Načte příznak, který určuje, zda uživatelsky definovaný datový typ obsahuje definice vnořeného typu.
title: 'IDiaSymbol:: get_hasNestedTypes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasNestedTypes method
ms.assetid: 1a8306bd-10dd-40a9-81fc-01f71c348484
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52efb012ef713c2308e3fc7b6b28367327e8311
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156284"
---
# <a name="idiasymbolget_hasnestedtypes"></a>IDiaSymbol::get_hasNestedTypes
Načte příznak, který určuje, zda uživatelsky definovaný datový typ obsahuje definice vnořeného typu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasNestedTypes ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda uživatelsky definovaný datový typ obsahuje definice vnořeného typu; v opačném případě vrátí `FALSE` .

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
