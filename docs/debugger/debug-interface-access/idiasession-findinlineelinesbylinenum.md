---
description: Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo v zadaném zdrojovém souboru a čísle řádku.
title: 'IDiaSession:: findInlineeLinesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 130c270e0be0e38768018467e117361c9befd796
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147763"
---
# <a name="idiasessionfindinlineelinesbylinenum"></a>IDiaSession::findInlineeLinesByLinenum
Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo v zadaném zdrojovém souboru a čísle řádku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 column,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `compiland`

pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje kompilantu, ve kterém chcete vyhledat čísla řádků. Tento parametr nemůže být `NULL` .

 `file`

pro Objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , který představuje zdrojový soubor, ve kterém se má hledat. Tento parametr nemůže být `NULL` .

 `linenum`

pro Určuje číslo řádku založené na jednom čísle.

> [!NOTE]
> Hodnotu nula nelze použít k určení všech řádků (k vyhledání všech řádků použijte metodu [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) ).

 `column`

pro Určuje číslo sloupce. K určení všech sloupců použijte nulu. Sloupec je posun bajtů na řádek.

 `ppResult`

mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje seznam čísel řádků, které byly načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
