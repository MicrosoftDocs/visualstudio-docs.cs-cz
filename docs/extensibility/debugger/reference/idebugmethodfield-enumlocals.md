---
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727203"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Vytvoří enumerátor pro vybrané místní proměnné metody.

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
pro Objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) představující adresu ladění, která vybere kontext nebo obor, ze kterého se mají získat místní hodnoty.

`ppLocals`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam místních hodnot; v opačném případě vrátí hodnotu null, pokud nejsou k dispozici žádná národní prostředí.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádné místní hodnoty. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Jsou vyhodnoceny pouze proměnné definované v rámci bloku, který obsahuje danou adresu pro ladění. Pokud jsou vyžadovány všechny místní proměnné včetně všech místních hodnot generovaných kompilátorem, zavolejte metodu [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .

Metoda může obsahovat více kontextů nebo bloků oborů. Například následující metoda contrived obsahuje tři obory, dva vnitřní bloky a tělo metody samotné.

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

Objekt [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) představuje metodu, která je `func` sama. Volání `EnumLocals` metody s [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nastavenou na `Inner Scope 1` adresu vrátí výčet obsahující `temp1` proměnnou, například.

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
