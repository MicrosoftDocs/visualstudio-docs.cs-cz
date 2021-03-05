---
description: Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor čísla řádku.
title: 'IDiaEnumLineNumbers:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af784c89e523f1747b665e46455d5d8b6b7e63b3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148981"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone ( 
   IDiaEnumLineNumbers** ppenum
);
```

#### <a name="parameters"></a>Parametry
 `ppenum`

mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje duplikát objektu Enumerator. Čísla řádků nejsou duplikována, pouze enumerátor..

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
