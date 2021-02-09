---
title: 'IDiaSession:: findAcceleratorInlineesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 196eafaee2b18c4dd08b81d6670b79cf62b8f41f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864283"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Vrátí výčet symbolů pro vložené rámce, které odpovídají zadanému zdrojovému umístění.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro `IDiaSymbol` Který odpovídá funkci pro zástupnou proceduru akcelerátoru, která musí být prohledána.

 `file`

pro `IDiaSourceFile` Zdrojového umístění.

 `linenum`

pro Číslo řádku zdrojového umístění.

 `colnum`

pro Číslo sloupce zdrojového umístění

 `ppResult`

mimo Ukazatel na `IDiaEnumLineNumbers` ukazatel rozhraní, který je inicializován s výsledkem.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)