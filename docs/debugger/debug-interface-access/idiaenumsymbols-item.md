---
description: Načte symbol prostřednictvím indexu.
title: 'IDiaEnumSymbols:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7d7223c19df1df3c73d976ede97a2fab98b7da91
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148701"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Načte symbol prostřednictvím indexu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD        index,
   IDiaSymbol** symbol
);
```

#### <a name="parameters"></a>Parametry
 index

pro Index objektu [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který se má načíst Index je v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumSymbols:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .

  – symbol

mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující požadovaný symbol.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
