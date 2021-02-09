---
title: 'IDiaSymbol:: get_thunkOrdinal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 276cb0ed42f884f2be3b10d82fd8561c6b9aa20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853504"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Načte typ převráceného kódu funkce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrací hodnotu z výčtu [výčtu THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) , který určuje typ převráceného kódu funkce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je platná pouze v případě, že symbol jako hodnota [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) `SymTagThunk` .

 "Převádějící" je část kódu, která se převádí mezi 32 adresního prostoru (označovaného také jako plochý adresní prostor) a 16bitového adresního prostoru (označovaného jako segmentované adresní místo).

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [THUNK_ORDINAL – výčet](../../debugger/debug-interface-access/thunk-ordinal.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)