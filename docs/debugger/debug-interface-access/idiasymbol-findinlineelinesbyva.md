---
title: 'IDiaSymbol:: findInlineeLinesByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb8f86b7bdeb7e6d3eb95f9540ce8c0a5c1eb241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464490"
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo, v tomto symbolu v rámci zadané virtuální adresy (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByVA ( 
   ULONGLONG             va,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `va`

pro Určuje adresu jako VA.

 `length`

pro Určuje rozsah adres, který má být pokrytý pomocí tohoto dotazu, v počtu bajtů.

 `ppResult`

mimo Obsahuje `IDiaEnumLineNumbers` objekt obsahující seznam čísel řádků, které jsou načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)