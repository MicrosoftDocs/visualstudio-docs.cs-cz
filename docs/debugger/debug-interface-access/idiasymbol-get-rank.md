---
title: 'IDiaSymbol:: get_rank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da00422a5a12a12f99cf706b0bf7bb2ce623d76f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853679"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Načte pořadí (počet rozměrů) multidimenzionálního pole FORTRAN.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet dimenzí v multidimenzionálním poli FORTRAN.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Rank odkazuje na počet dimenzí v poli, kde je pole deklarováno jako `myarray[1,2,3]` . Tento příklad má pořadí 3 a 3 rozměry. Rozsah se nevztahuje na jazyk C++, který používá koncept pole polí pro každou dimenzi (tj `myarray[1][2][3]` .).

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)