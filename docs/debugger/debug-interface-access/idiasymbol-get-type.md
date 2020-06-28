---
title: 'IDiaSymbol:: get_type | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 738d3045c524700e803fe82c8902d4f1b77948b5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461744"
---
# <a name="idiasymbolget_type"></a>IDiaSymbol::get_type
Načte symbol, který představuje typ pro tento symbol.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
`pRetVal`

mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje typ tohoto symbolu.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
Chcete-li určit typ symbolu, je nutné zavolat tuto metodu a prozkoumávat výsledný objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Všimněte si, že je možné, že symbol nemá typ. Například název struktury nemá žádný typ, ale může mít podřízené symboly (k prohlédnutí těchto podřízených metod použijte metodu [IDiaSymbol:: findChildren –](../../debugger/debug-interface-access/idiasymbol-findchildren.md) ).

## <a name="example"></a>Příklad

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
