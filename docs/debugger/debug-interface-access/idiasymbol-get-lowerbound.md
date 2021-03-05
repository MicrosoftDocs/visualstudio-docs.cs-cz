---
description: Načte dolní mez dimenze pole FORTRAN.
title: 'IDiaSymbol:: get_lowerBound | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBound method
ms.assetid: e9a6440b-d068-4de4-a240-6723d20812b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b81c853c69aae755fa17c5d37f0e92c94d4871d2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147287"
---
# <a name="idiasymbolget_lowerbound"></a>IDiaSymbol::get_lowerBound
Načte dolní mez dimenze pole FORTRAN.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lowerBound ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje dolní mez dimenze pole FORTRAN.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
