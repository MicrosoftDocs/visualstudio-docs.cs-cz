---
title: 'IDiaSymbol:: get_subType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0b3cbf77-8f11-434a-ad60-ea9829fec6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57a7756d7764cbd4799bfe49eec7f06732bd0bee
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461947"
---
# <a name="idiasymbolget_subtype"></a>IDiaSymbol::get_subType
Načte dílčí typ.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_subType(
   IDiaSymbol** pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na podtyp.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)