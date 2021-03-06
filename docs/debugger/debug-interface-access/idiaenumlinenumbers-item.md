---
description: Načte číslo řádku prostřednictvím indexu.
title: 'IDiaEnumLineNumbers:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eeea52f2152d1674710d7c5ee2b5970a8cd91cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157978"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Načte číslo řádku prostřednictvím indexu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Parametry
 index

pro Index objektu [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) , který se má načíst Index je v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumLineNumbers:: get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) .

 Číslo řádku

mimo Vrátí objekt [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) představující požadované číslo řádku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
