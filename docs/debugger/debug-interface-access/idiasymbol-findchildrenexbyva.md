---
title: 'IDiaSymbol:: findChildrenExByVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ed1d2e2cfda5bf16117c2bc4fbd8c13384055a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854666"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Načte podřízené objekty symbolu, které jsou platné v zadané virtuální adrese.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildrenExByVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `symtag`

pro Určuje značky symbolů podřízených objektů, které mají být načteny, jak je definováno ve [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md). Nastavte na hodnotu `SymTagNull` pro všechny podřízené položky, které mají být načteny.

 `name`

pro Určuje název podřízených objektů, které mají být načteny. Nastavte na hodnotu `NULL` pro všechny podřízené položky, které mají být načteny.

 `compareFlags`

pro Určuje možnosti porovnání, které se mají použít pro porovnávání názvů. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.

 `address`

pro Určuje virtuální adresu.

 `ppResult`

mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje seznam načtených podřízených symbolů.

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK` , zda byl nalezen alespoň jeden podřízený symbol, nebo vrátí, `S_FALSE` Pokud nebyly nalezeny žádné podřízené položky. v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Mezi vracené místní symboly patří informace o živém rozsahu.

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia100.dll

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)