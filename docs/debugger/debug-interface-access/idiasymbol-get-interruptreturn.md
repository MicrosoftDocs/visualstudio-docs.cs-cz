---
description: Načte příznak, který určuje, zda funkce obsahuje návrat z instrukce pro přerušení (například IRET sestavení x86).
title: 'IDiaSymbol:: get_interruptReturn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_interruptReturn method
ms.assetid: 9665da6c-4cc0-41d7-b2e2-0d9e50174cf8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 91e88b4348e5bc778b71c0737a57effcf70ecac6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147322"
---
# <a name="idiasymbolget_interruptreturn"></a>IDiaSymbol::get_interruptReturn
Načte příznak, který určuje, zda funkce obsahuje návrat z instrukce pro přerušení (například kód sestavení x86 `iret` ).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_interruptReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, `TRUE` zda funkce vrátí z instrukce pro přerušení. v opačném případě vrátí hodnotu `FALSE` .

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
