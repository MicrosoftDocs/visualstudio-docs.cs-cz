---
title: IDebugMethodField::EnumLocals | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08872160860d0d442f9807705dea70190dff9b28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727203"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Vytvoří čítač výčtu pro vybrané místní proměnné metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[v] [Objekt IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) představující ladicí adresu, která vybere kontext nebo obor, ze kterého chcete získat místní.

`ppLocals`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam místních obyvatel. v opačném případě vrátí hodnotu null, pokud neexistují žádné místní.

## <a name="return-value"></a>Návratová hodnota
Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné místní. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Jsou uvedeny pouze proměnné definované v rámci bloku, který obsahuje danou adresu ladění. Pokud jsou potřeba všechny místní, včetně místních obyvatel generované kompilátorem, zavolejte metodu [EnumAllLocals.](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)

Metoda může obsahovat více kontextů oboru nebo bloků. Například následující vykonstruovaná metoda obsahuje tři obory, dva vnitřní bloky a samotné tělo metody.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

Objekt [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) představuje `func` samotnou metodu. Volání `EnumLocals` metody s [iDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nastavenou `Inner Scope 1` na adresu vrátí výčet obsahující například proměnnou. `temp1`

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
