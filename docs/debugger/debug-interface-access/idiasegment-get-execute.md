---
title: 'IDiaSegment:: get_execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 349b9b865223e2df0083e12d4c8bfd26ae2c2643
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466005"
---
# <a name="idiasegmentget_execute"></a>IDiaSegment::get_execute
Načte příznak, který označuje, zda je segment spustitelný.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_execute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda je segment označen jako spustitelný soubor. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)