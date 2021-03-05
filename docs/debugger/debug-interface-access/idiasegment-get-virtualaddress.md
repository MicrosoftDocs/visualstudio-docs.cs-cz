---
description: Načte virtuální adresu (VA) začátku oddílu.
title: 'IDiaSegment:: get_virtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_virtualAddress method
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f1410a34bce0e9ca7705e61af98f71a154988ff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147889"
---
# <a name="idiasegmentget_virtualaddress"></a>IDiaSegment::get_virtualAddress
Načte virtuální adresu (VA) začátku oddílu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí hodnotu VA začátku oddílu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
