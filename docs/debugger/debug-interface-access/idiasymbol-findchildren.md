---
title: 'IDiaSymbol:: findChildren – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a61a85e36159c361f01dd4048a06c040415860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854701"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Načte podřízené položky symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `symtag`

pro Určuje značky symbolů podřízených objektů, které mají být načteny, jak je definováno ve [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md). Nastavte na hodnotu `SymTagNull` pro všechny podřízené položky, které mají být načteny.

 `name`

pro Určuje název podřízených objektů, které mají být načteny. Nastavte na hodnotu `NULL` pro všechny podřízené položky, které mají být načteny.

 `compareFlags`

pro Určuje možnosti porovnání použité pro porovnávání názvů. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.

 `ppResult`

mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje seznam načtených podřízených symbolů.

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK` , zda byl nalezen alespoň jeden podřízený symbol, nebo vrátí, `S_FALSE` Pokud nebyly nalezeny žádné podřízené položky. v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je shodná s voláním metody [IDiaSession:: findChildren –](../../debugger/debug-interface-access/idiasession-findchildren.md) s tímto symbolem jako s prvním parametrem.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)