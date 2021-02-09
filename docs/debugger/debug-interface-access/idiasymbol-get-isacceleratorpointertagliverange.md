---
title: 'IDiaSymbol:: get_isAcceleratorPointerTagLiveRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a0e2d22da73402c7eb68e2a84cfe98e59fc0832
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863254"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Načte příznak, který označuje, zda symbol odpovídá *symbolu rozsahu definice* pro komponentu značky v kódu kompilovaném pro C++ amp akcelerátor. Symbol rozsahu definice je umístění proměnné pro rozsah adres.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Ukazatel na `BOOL` , který označuje, zda symbol odpovídá symbolu rozsahu definice.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)