---
title: 'IDiaSymbol:: get_unmodifiedTypeId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6205bf2a80f362d803b5f5e23397a5578ddc2b3
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461586"
---
# <a name="idiasymbolget_unmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
Načte ID původního (neupraveného) typu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_unmodifiedTypeId(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Ukazatel na `DWORD` , který obsahuje ID.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)