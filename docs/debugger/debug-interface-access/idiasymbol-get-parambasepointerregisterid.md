---
description: Načte identifikátor registru, který uchovává základní ukazatel na parametry.
title: 'IDiaSymbol:: get_paramBasePointerRegisterId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 25430f835ffedce3fa890c189cabc358f160a4ba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155857"
---
# <a name="idiasymbolget_parambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
Načte identifikátor registru, který uchovává základní ukazatel na parametry. Použijte v případě, že je [výčet SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) nastaven na hodnotu `SymTagFunction` .

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_paramBasePointerRegisterId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí ID registru, který uchovává základní ukazatel na parametry.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia100.dll

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
