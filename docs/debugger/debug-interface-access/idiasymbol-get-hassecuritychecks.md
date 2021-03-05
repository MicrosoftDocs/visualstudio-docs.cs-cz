---
description: Načte příznak, který určuje, zda byla kompilantu nebo funkce kompilována se kontrolami zabezpečení přetečení vyrovnávací paměti (například/GS (kontrola zabezpečení vyrovnávací paměti)) – přepínač kompilátoru).
title: 'IDiaSymbol:: get_hasSecurityChecks | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56f337a84081aa8c0282efcf07b70f30d98da15e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162066"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Načte příznak, který určuje, zda byla kompilantu nebo funkce kompilována se kontrolami zabezpečení přetečení vyrovnávací paměti (například přepínač kompilátoru [/GS (kontrola zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check) ).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Vrátí, `TRUE` zda má funkce nějaké kontroly zabezpečení; v opačném případě vrátí `FALSE` .

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
- [/GS (kontrolu zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check)
