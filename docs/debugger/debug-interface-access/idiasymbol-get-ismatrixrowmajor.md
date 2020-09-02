---
title: 'IDiaSymbol:: get_isMatrixRowMajor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eca3d36c0b0cf82ae3fe67ac527e292b401187c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85463370"
---
# <a name="idiasymbolget_ismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Určuje, zda je matice hlavní řádek.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMatrixRowMajor(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na `BOOL` , který určuje, zda je matice hlavní řádek.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)