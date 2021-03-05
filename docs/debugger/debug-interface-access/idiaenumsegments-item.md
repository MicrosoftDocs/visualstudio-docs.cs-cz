---
description: Načte segment prostřednictvím indexu.
title: 'IDiaEnumSegments:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8714964bdf2e267e9f9c047fb1878655e58f489
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148848"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Načte segment prostřednictvím indexu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parametry
 index

pro Index objektu [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , který se má načíst Index je v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumSegments:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .

 segment

mimo Vrátí objekt [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) představující požadovaný segment.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
