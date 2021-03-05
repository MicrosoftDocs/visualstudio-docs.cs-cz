---
description: Načte typ umístění datového symbolu.
title: 'IDiaSymbol:: get_locationType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_locationType method
ms.assetid: fbb09c43-ebb7-4b4f-be53-ccff86eb183a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a4ef7d60db3eacc7f87699e8c6e20b93e56bcd4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156018"
---
# <a name="idiasymbolget_locationtype"></a>IDiaSymbol::get_locationType
Načte typ umístění datového symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_locationType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrací hodnotu z výčtu [výčtu LocationType –](../../debugger/debug-interface-access/locationtype.md) , který určuje typ umístění symbolu dat, například `static` nebo `local` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
