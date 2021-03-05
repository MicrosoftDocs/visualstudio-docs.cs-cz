---
description: Určuje, zda tento ukazatel ukazuje na datový člen s vícenásobnou dědičností.
title: 'IDiaSymbol:: get_isMultipleInheritance | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d197810c61ca50a98cc47c5c3e2ecaca5be548d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156172"
---
# <a name="idiasymbolget_ismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Určuje, zda `this` ukazatel ukazuje na datový člen s vícenásobnou dědičností.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na `BOOL` , který určuje, zda `this` ukazatel ukazuje na datový člen s vícenásobnou dědičností.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
