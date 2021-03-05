---
description: Načte příznak, který označuje, zda symbol odpovídá skupině sdílené místní proměnné v kódu kompilovaném pro C++ AMP akcelerátor.
title: 'IDiaSymbol:: get_isAcceleratorGroupSharedLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8da1e0e8672fb0c10769ca448556f0007fe44014
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147301"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Načte příznak, který označuje, zda symbol odpovídá skupině sdílené místní proměnné v kódu kompilovaném pro C++ AMP akcelerátor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Ukazatel na `BOOL` , který označuje, zda symbol odpovídá skupině sdílené místní proměnné v kódu kompilovaném pro C++ amp akcelerátor. `TRUE`V případě, `get_baseDataSlot` `get_baseDataOffset` metody a lze použít k získání informací o umístění úložiště pro proměnnou.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)
