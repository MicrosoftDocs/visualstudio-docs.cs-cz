---
description: Načte příznak, který označuje, jestli se oddíl nedá stránkovat z paměti.
title: 'IDiaSectionContrib:: get_notPaged | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcb59824f3be2e6f04e1fd49dcdc4a9ef08b8af1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147987"
---
# <a name="idiasectioncontribget_notpaged"></a>IDiaSectionContrib::get_notPaged
Načte příznak, který označuje, jestli se oddíl nedá stránkovat z paměti.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_notPaged ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`
- [out, retval] Vrátí `TRUE` , zda oddíl nelze stránkovat. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
