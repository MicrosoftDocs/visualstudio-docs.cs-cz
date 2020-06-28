---
title: 'IDiaEnumSectionContribs:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e13f9290c76eb558bea397f7921f7cfd765613f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468091"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Přeskočí zadaný počet příspěvků oddílu do sekvence výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 `celt`

pro Počet příspěvků oddílu v sekvenci výčtu, které se mají přeskočit.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud neexistují žádné další příspěvky k oddílu, který by bylo možné přeskočit.

## <a name="see-also"></a>Viz také
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)