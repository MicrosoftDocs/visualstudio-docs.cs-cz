---
title: 'IDiaSymbol:: get_typeIds | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739076"
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

mimo Vrátí počet zapsaných `typeIds`, nebo pokud `typeIds` `NULL`, pak celkový počet dostupných identifikátorů typů.

 `typeIds[]`

mimo Pole, které se má vyplnit identifikátory typu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také:
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)