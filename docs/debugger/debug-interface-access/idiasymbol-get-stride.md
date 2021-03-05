---
description: Načte rozteč matice nebo pole s roztečí.
title: 'IDiaSymbol:: get_stride | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 331949c4b37c6e4f472bc2d1f5d805d7a9f7426a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147147"
---
# <a name="idiasymbolget_stride"></a>IDiaSymbol::get_stride
Načte rozteč matice nebo pole s roztečí.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_stride(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na `DWORD` , který má rozteč.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
