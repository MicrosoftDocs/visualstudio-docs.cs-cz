---
title: 'IDiaSymbol:: get_hasSEH | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0689490e855508314835a21e44e6cb9a02736ef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863303"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Načte příznak, který určuje, zda funkce obsahuje jakékoli [strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (například bloky __try/ \_ _except).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí `TRUE` , zda má funkce jakékoli strukturované bloky zpracování výjimek; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 8.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Strukturované zpracování výjimek (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)