---
description: Načte příznak, který určuje, zda funkce obsahuje použití příkazu longjmp) (spárováno s příkazem setjmp (/CPP/c-Runtime-Library/Reference/setjmp), tyto formuláře označují metodu zpracování výjimek ve stylu C.
title: 'IDiaSymbol:: get_hasLongJump | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c211e52e1a8e13a88b6c2a2f9404f5d8a67386f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156298"
---
# <a name="idiasymbolget_haslongjump"></a>IDiaSymbol::get_hasLongJump
Načte příznak, který určuje, zda funkce obsahuje použití příkazu [longjmp](/cpp/c-runtime-library/reference/longjmp) (spárovaného s příkazem [setjmp](/cpp/c-runtime-library/reference/setjmp) , tato forma metody zpracování výjimek ve stylu C).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, `TRUE` zda funkce obsahuje `longjmp` příkaz. v opačném případě vrátí hodnotu `FALSE` .

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
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)
