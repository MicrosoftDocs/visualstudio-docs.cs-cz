---
title: 'IDiaEnumTables:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27daf70a3cc5f155bfbe6b2678cce42b50801153
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467461"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Přeskočí zadaný počet tabulek ve výčtové sekvenci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 `celt`

pro Počet tabulek v sekvenci výčtu k přeskočení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud neexistují žádné další tabulky, které by bylo možné přeskočit.

## <a name="see-also"></a>Viz také
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)