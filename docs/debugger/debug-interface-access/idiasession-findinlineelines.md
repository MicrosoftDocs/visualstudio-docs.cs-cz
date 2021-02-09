---
title: 'IDiaSession:: findInlineeLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f13e9c92657072b09fb11dd5f632a9df64040d94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864248"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
Načte výčet, který umožňuje klientovi iterovat informace o číslech řádků všech funkcí, které jsou vloženy přímo nebo nepřímo zadaným nadřazeným symbolem.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineeLines ( 
   IDiaSymbol*       parent,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro `IDiaSymbol` Objekt představující nadřazený prvek.

 `ppResult`

mimo Obsahuje `IDiaEnumLineNumbers` objekt obsahující seznam čísel řádků, které jsou načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)