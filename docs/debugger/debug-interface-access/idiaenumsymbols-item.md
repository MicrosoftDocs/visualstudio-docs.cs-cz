---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58e00d55a26f3aaf771eed01135c62b607794876
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467755"
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