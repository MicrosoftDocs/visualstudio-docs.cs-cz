---
description: 'IDiaSymbol:: findInlineFramesByRVA načte výčet, který umožňuje klientovi iterovat všemi vloženými snímky na zadané relativní virtuální adrese (RVA).'
title: 'IDiaSymbol:: findInlineFramesByRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22ecafb604f31c23f503bbfcbedcd13ee2a42e95
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156662"
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
Načte výčet, který umožňuje klientovi iterovat všemi vloženými snímky na zadané relativní virtuální adrese (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInlineFramesByRVA (    DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `rva`

pro Určuje adresu jako RVA.

 `ppResult`

mimo Obsahuje `IDiaEnumSymbols` objekt, který obsahuje seznam rámců, které byly načteny.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
