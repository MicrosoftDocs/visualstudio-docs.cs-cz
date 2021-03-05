---
description: Načte příznak, který určuje, zda symbol odkazuje na kód jazyka MSIL (Microsoft Intermediate Language).
title: 'IDiaSymbol:: get_msil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_msil method
ms.assetid: 43a8e003-6856-4726-aa16-c0d4dae7299b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 322b01e97507da4940aea02fe461da0b19b7995c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155948"
---
# <a name="idiasymbolget_msil"></a>IDiaSymbol::get_msil
Načte příznak, který určuje, zda symbol odkazuje na kód jazyka MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_msil ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda symbol odkazuje na kód jazyka MSIL; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
