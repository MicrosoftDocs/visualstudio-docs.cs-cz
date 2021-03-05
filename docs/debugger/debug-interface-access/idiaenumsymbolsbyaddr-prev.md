---
description: Načte předchozí symboly v pořadí podle adresy.
title: IDiaEnumSymbolsByAddr::P rev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 721eaf80e0bd7121d9e8286315b63422edbb745d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148638"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Načte předchozí symboly v pořadí podle adresy.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet symbolů v enumerátoru, které mají být načteny.

 rgelt

mimo Pole, které se má vyplnit objekty [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , které reprezentují požadované symboly.

 pceltFetched

mimo Vrátí počet symbolů v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné předchozí symboly. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda aktualizuje pozici čítače výčtu počtem načtených prvků.

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
