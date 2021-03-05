---
description: Načte zadaný počet zdrojových souborů v sekvenci výčtu.
title: 'IDiaEnumSourceFiles:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdac59ba0998528cde8412a9fff9062edb56044
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148778"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Načte zadaný počet zdrojových souborů v sekvenci výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet zdrojových souborů v enumerátoru, které mají být načteny.

 rgelt

mimo Pole, které se má vyplnit objekty [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , které reprezentují požadované zdrojové soubory.

 pceltFetched

mimo Vrátí počet zdrojových souborů v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další zdrojové soubory. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
