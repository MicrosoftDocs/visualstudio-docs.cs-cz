---
description: Načte příznak, který určuje, zda byla Kompilantu) propojena s přepínačem linkeru/LTCG (generování kódu při propojování) (/CPP/Build/reference/LTCG-Link-Time-Code-Generation), které pomáhá v optimalizaci celého programu.
title: 'IDiaSymbol:: get_isLTCG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b8306dabe6533287d7d28841ea76f2d6478e4a3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160811"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
Načte příznak, který určuje, zda byl [kompilantu](../../debugger/debug-interface-access/compiland.md) propojen s přepínačem linkeru [/LTCG (generování kódu při propojování)](/cpp/build/reference/ltcg-link-time-code-generation), které pomáhá v optimalizaci celého programu. Tento přepínač platí pouze pro spravovaný kód.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 pFlag

mimo Vrátí, `TRUE` zda `compiland` byla propojena s přepínačem linkeru/LTCG. v opačném případě vrátí `FALSE` .

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
