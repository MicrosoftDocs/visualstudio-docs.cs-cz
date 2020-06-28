---
title: 'IDiaSymbol:: get_value | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_value method
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9a36da3feecfe1af664e35fa50d616d2a94fb0a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461509"
---
# <a name="idiasymbolget_value"></a>IDiaSymbol::get_value
Načte hodnotu konstanty.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_value (
    VARIANT* pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

[in, out] `VARIANT`Objekt, který je vyplněn hodnotou konstanty.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
Zadaný typ VARIANT musí být inicializován před předáním této metodě. Další informace najdete v příkladu.

## <a name="example"></a>Příklad

```C++
void ProcessValue(IDiaSymbol *pSymbol)
{
    VARIANT value;
    value.vt = VT_EMPTY;    // Initialize variant for use.
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value.
    }
}

//----------------------------------------------------
// Alternate approach
void ProcessValue2(IDiaSymbol *pSymbol)
{
    CComVariant value;
    if (pSymbol->get_value(&value) == S_OK)
    {
        // Do something with value
    }
}
```

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
