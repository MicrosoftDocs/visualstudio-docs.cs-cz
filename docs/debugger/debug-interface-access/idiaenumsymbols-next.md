---
description: Načte zadaný počet symbolů v sekvenci výčtu.
title: 'IDiaEnumSymbols:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Next method
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1effa2d3b861be076a18adaaeafa10549ec7478
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148708"
---
# <a name="idiaenumsymbolsnext"></a>IDiaEnumSymbols::Next
Načte zadaný počet symbolů v sekvenci výčtu.

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

mimo Pole, které se má vyplnit objekty [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , které reprezentují požadované symboly.

 pceltFetched

mimo Vrátí počet symbolů v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další symboly. V opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad

```C++
IDiaEnumSymbols* pEnum
CComPtr< IDiaSymbol> pSym;
DWORD celt;
pEnum->Next( 1, &pSym, &celt );
```

## <a name="see-also"></a>Viz také
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
