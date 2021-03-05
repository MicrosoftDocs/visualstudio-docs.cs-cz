---
description: Určuje, zda je tento symbol ukazatelem na členskou funkci.
title: 'IDiaSymbol:: get_isPointerToMemberFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92bcde9b53cc03326aac1c122e1d2b2e20f08e67
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156074"
---
# <a name="idiasymbolget_ispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
Určuje, zda je tento symbol ukazatelem na členskou funkci.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isPointerToMemberFunction(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na `BOOL` , který určuje, zda je tento symbol ukazatel na členskou funkci.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
