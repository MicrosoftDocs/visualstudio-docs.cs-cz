---
description: Načte počet položek v tabulce.
title: 'IDiaTable:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_Count method
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 410f8b6f029f26939582d64420db0351a71c0975
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155486"
---
# <a name="idiatableget_count"></a>IDiaTable::get_Count
Načte počet položek v tabulce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet položek v tabulce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)
