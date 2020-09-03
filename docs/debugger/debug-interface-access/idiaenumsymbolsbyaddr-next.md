---
title: 'IDiaEnumSymbolsByAddr:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2a4be91f2439c198ca7424ba13542c68d41c6b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467664"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Načte další symboly v pořadí podle adresy.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet symbolů v enumerátoru, které mají být načteny.

 rgelt

mimo Pole, které se má vyplnit objektem [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje požadované symboly.

 pceltFetched

mimo Vrátí počet symbolů v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další symboly. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda aktualizuje pozici čítače výčtu počtem načtených prvků.

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)