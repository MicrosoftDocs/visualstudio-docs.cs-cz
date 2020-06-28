---
title: 'IDiaSymbol:: get_types | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d947eed08ba28cfdd68e2cd7d34998412fc8bc3a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461683"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Načte pole typů určených pro kompilátor pro tento symbol.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parametry
 `cTypes`

pro Velikost vyrovnávací paměti pro uchovávání dat.

 `pcTypes`

mimo Vrátí počet zapsaných typů, nebo, pokud `types` je parametr `NULL` , a celkový počet dostupných typů.

 `types[]`

mimo Pole, které se má vyplnit objekty [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , které reprezentují všechny typy pro tento symbol.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)