---
title: 'IDiaEnumSourceFiles:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6dd38782a7618259d802ae898c643d2a504c3fc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467874"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
Přeskočí zadaný počet zdrojových souborů v sekvenci výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet zdrojových souborů v sekvenci výčtu, které se mají přeskočit.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud neexistují žádné další zdrojové soubory, které by bylo možné přeskočit.

## <a name="see-also"></a>Viz také
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)