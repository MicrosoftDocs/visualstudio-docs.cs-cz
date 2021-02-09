---
title: 'IDiaEnumSectionContribs:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55c4dcef489c56688321497c93448d83ce342b1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856458"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Načte zadaný počet příspěvků oddílu do sekvence výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet příspěvků oddílu ve výčtu, který má být načten.

 rgelt

mimo Pole, které má být vyplněno objekty [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) , které reprezentují požadovaný oddíl.

 pceltFetched

mimo Vrátí počet příspěvků v sekci v načteném výčtu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda neexistují žádné další příspěvky k sekci. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)