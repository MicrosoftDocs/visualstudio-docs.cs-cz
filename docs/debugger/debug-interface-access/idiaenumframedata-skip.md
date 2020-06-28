---
title: 'IDiaEnumFrameData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02c56c0b49844b72384d641a53eb513c2a504acb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468306"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Přeskočí zadaný počet prvků dat rámce v sekvenci výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet elementů dat rámce ve výčtové sekvenci, které se mají přeskočit.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud neexistují žádné další záznamy, které by bylo možné přeskočit.

## <a name="see-also"></a>Viz také
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)