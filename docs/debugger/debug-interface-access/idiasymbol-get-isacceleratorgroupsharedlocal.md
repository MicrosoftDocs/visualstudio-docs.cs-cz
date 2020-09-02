---
title: 'IDiaSymbol:: get_isAcceleratorGroupSharedLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1110f0882e8281955fa4efdf41a1355405bdd557
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463503"
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