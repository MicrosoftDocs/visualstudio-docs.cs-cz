---
description: Načte symbol podle jeho jedinečného identifikátoru.
title: 'IDiaSession:: symbolById | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 979825cd3e62c97334d55676b3bf32bf874f8445
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147602"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Načte symbol podle jeho jedinečného identifikátoru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametry
`id`

pro Jedinečný identifikátor.

`ppSymbol`

mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje načtený symbol.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Zadaný identifikátor je jedinečnou hodnotou, kterou používá interně DIA SDK k nastavení všech symbolů jako jedinečných.

Tuto metodu lze použít například k načtení symbolu reprezentujícího typ jiného symbolu (viz příklad).

## <a name="example"></a>Příklad
Tento příklad načte [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující typ jiného symbolu. Tento příklad ukazuje, jak použít `symbolById` metodu v relaci. Jednodušším přístupem je volání metody [IDiaSymbol:: get_Type](../../debugger/debug-interface-access/idiasymbol-get-type.md) pro načtení symbolu typu přímo.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
