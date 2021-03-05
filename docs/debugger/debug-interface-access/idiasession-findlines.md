---
description: Načte čísla řádků v rámci zadaných identifikátorů kompilantu a zdrojových souborů.
title: 'IDiaSession:: findLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a887436555f1ac3d4880c53f1a9103d0fa285df0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147714"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Načte čísla řádků v rámci zadaných identifikátorů kompilantu a zdrojových souborů.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `compiland`

pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující kompilantu. Toto rozhraní použijte jako kontext, ve kterém chcete vyhledat čísla řádků.

 `file`

pro Objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) představující zdrojový soubor, ve kterém chcete vyhledat čísla řádků.

 `ppResult`

mimo Vrátí objekt [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , který obsahuje seznam čísel řádků, které se načetly.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
