---
description: Načte příznak, který určuje, zda není funkce nebo popisek nikdy dosažen.
title: 'IDiaSymbol:: get_notReached | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_notReached method
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63acaae080dee21516729764906e959c8dca9930
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147166"
---
# <a name="idiasymbolget_notreached"></a>IDiaSymbol::get_notReached
Načte příznak, který určuje, zda není funkce nebo popisek nikdy dosažen.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_notReached(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 pFlag

mimo Vrátí hodnotu `TRUE` , pokud není nikdy dosaženo funkce nebo popisku; v opačném případě vrátí `FALSE` .

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
