---
description: Označuje, zda symbol odpovídá symbolu funkce nejvyšší úrovně pro shader kompilovaný pro akcelerátor, který odpovídá parallel_for_each volání.
title: 'IDiaSymbol:: get_isAcceleratorStubFunction | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 710622fdb8fb10d0357c060097f13bab3be7d05f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156214"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Označuje, zda symbol odpovídá symbolu funkce nejvyšší úrovně pro shader kompilovaný pro akcelerátor, který odpovídá `parallel_for_each` volání.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

mimo Ukazatel na `BOOL` , který označuje, zda symbol odpovídá symbolu funkce nejvyšší úrovně pro shader kompilovaný pro akcelerátor, který odpovídá `parallel_for_each` volání.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
