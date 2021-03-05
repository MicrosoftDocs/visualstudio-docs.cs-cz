---
description: Načte datové bajty pro symbol OEM.
title: 'IDiaSymbol:: get_dataBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09156b8d99daa5cbfd065110073c3c185c3ac0a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161014"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
Načte datové bajty pro symbol OEM.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

pro Velikost vyrovnávací paměti pro uchovávání dat.

 `pcbData`

mimo Vrátí počet zapsaných bajtů nebo, pokud `data` je parametr `NULL` , vrátí počet dostupných bajtů.

 `data[]`
- [out,] Vyrovnávací paměť, která je vyplněna datovými bajty.

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
