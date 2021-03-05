---
description: Načte příznak, který určuje, zda je funkce Představujeme virtuální funkci.
title: 'IDiaSymbol:: get_intro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad2e791995f4edc1b09655640bc339d577f7f37d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160874"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Načte příznak, který určuje, zda je funkce Představujeme virtuální funkci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

mimo Vrátí, `TRUE` zda je funkce vydaná jako virtuální; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="example"></a>Příklad

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

`A::f1`A `B::f1` jsou virtuální funkce, ale `A::f1` je to virtuální.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
