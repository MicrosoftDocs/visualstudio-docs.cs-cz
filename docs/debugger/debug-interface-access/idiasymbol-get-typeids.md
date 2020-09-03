---
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36bf189b8137c5a1a632dffd0b5a5d1641a9c24c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461690"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Načte pole hodnot identifikátoru specifického pro kompilátor pro tento symbol.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametry
 `cTypeIds`

pro Velikost vyrovnávací paměti pro uchovávání dat.

 `pcTypeIds`

mimo Vrátí počet `typeIds` napsaných čísel, nebo pokud `typeIds` je `NULL` , a celkový počet dostupných identifikátorů typů.

 `typeIds[]`

mimo Pole, které se má vyplnit identifikátory typu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)