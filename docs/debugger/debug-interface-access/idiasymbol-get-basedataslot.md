---
description: Načte základní datovou oblast.
title: 'IDiaSymbol:: get_baseDataSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 941633f50e7d8e44e591b82211b00de931d45919
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156466"
---
# <a name="idiasymbolget_basedataslot"></a>IDiaSymbol::get_baseDataSlot
Načte základní datovou oblast.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_baseDataSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na objekt `DWORD` , který obsahuje základní datovou oblast.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
