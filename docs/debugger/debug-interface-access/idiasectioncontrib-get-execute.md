---
title: 'IDiaSectionContrib:: get_execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_execute method
ms.assetid: 66eb38ce-a5e1-467e-b845-b3dc433eda91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f163c2a6a37dd1e379557047f70966932ef45c64
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742659"
---
# <a name="idiasectioncontribget_execute"></a>IDiaSectionContrib::get_execute
Načte příznak, který označuje, zda je oddíl spustitelný jako kód.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_excute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí `TRUE`, zda lze oddíl provést jako kód; v opačném případě vrátí `FALSE`.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`. Vrátí `S_FALSE`, pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)