---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a9867c3997a73f349ba7a9989cb8450f9bd2d3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465676"
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