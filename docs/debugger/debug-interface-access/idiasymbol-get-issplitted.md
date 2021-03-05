---
description: Načte příznak, který určuje, zda byl datový symbol rozdělen do agregace nebo kolekce jiných symbolů; kompilátor zpracovává symboly jako samostatné entity, a to i v případě, že jsou ve skutečnosti součástí většího symbolu.
title: 'IDiaSymbol:: get_isSplitted | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5dd9807928ca5f1b8d2e3b20c5de3ec30adc70db
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162052"
---
# <a name="idiasymbolget_issplitted"></a>IDiaSymbol::get_isSplitted
Načte příznak, který určuje, zda byl datový symbol rozdělen do agregace nebo kolekce jiných symbolů; kompilátor zpracovává symboly jako samostatné entity, a to i v případě, že jsou ve skutečnosti součástí většího symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isSplitted(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, `TRUE` zda byl symbol rozdělen na agregaci symbolů; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Metoda [IDiaSymbol:: get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) vrátí `TRUE` pro všechny symboly, které jsou součástí rozděleného symbolu.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)
