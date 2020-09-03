---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 877ac3b0a73dc13600c9d6847dfc505caaa05821
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464042"
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