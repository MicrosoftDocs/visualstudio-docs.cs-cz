---
title: 'IDiaSymbol:: findChildrenEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdced012baada390cdd0a112856b592d3c923e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741273"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Načte podřízené položky symbolu. Místní symboly, které jsou vráceny, obsahují informace o živém rozsahu, pokud je program zkompilován s optimalizací na.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildrenEx ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `symtag`

pro Určuje značky symbolů podřízených objektů, které mají být načteny, jak je definováno ve [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md). Nastavte na `SymTagNull` pro všechny podřízené položky, které se mají načíst.

 `name`

pro Určuje název podřízených objektů, které mají být načteny. Nastavte na `NULL` pro všechny podřízené položky, které se mají načíst.

 `compareFlags`

pro Určuje možnosti porovnání, které se mají použít pro porovnávání názvů. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.

 `ppResult`

mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje seznam načtených podřízených symbolů.

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK`, pokud byl nalezen alespoň jeden podřízený symbol, nebo vrátí `S_FALSE`, pokud nebyly nalezeny žádné podřízené položky; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je rozšířená verze [IDiaSymbol:: findChildren –](../../debugger/debug-interface-access/idiasymbol-findchildren.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 Knihovna DLL: msdia100. dll

## <a name="see-also"></a>Viz také:
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)