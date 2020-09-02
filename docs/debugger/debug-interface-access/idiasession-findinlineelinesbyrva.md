---
title: 'IDiaSession:: findInlineeLinesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9469415682d7347aa3d51ee09878e31e28e85f62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465718"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo zadaným nadřazeným symbolem a jsou obsaženy v rámci zadané relativní virtuální adresy (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro `IDiaSymbol` Objekt představující nadřazený prvek.

 `rva`

pro Určuje adresu jako RVA.

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