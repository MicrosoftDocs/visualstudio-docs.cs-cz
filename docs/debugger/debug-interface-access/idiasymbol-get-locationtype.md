---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 244f9c1b696b03a085e665c5e45abf200c5774cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462971"
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