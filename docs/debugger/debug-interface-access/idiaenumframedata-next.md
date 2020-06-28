---
title: 'IDiaEnumFrameData:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2755ce3f48e22d239622dd49800e98ce49c496c7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468320"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Načte zadaný počet prvků dat rámce v sekvenci výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet datových elementů rámce ve výčtu, který má být načten.

 rgelt

mimo Pole objektů [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , které se mají vyplnit požadovanými datovými prvky rámce.

 pceltFetched

mimo Vrátí počet datových elementů rámce v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další záznamy. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)