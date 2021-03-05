---
description: Načte název souboru, ze kterého byly symboly načteny.
title: 'IDiaSymbol:: get_symbolsFileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symbolsFileName method
ms.assetid: c1aa39ee-d645-431e-bf5f-0640c0998934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe20bacc1100fc28258422626e44274813ce7253
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155759"
---
# <a name="idiasymbolget_symbolsfilename"></a>IDiaSymbol::get_symbolsFileName
Načte název souboru, ze kterého byly symboly načteny.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_symbolsFileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí název souboru, ze kterého byly symboly načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je platná pouze pro symboly s hodnotou [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) `SymTagExe` , která má také globální rozsah.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
