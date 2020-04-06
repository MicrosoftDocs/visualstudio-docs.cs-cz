---
title: IDebugMethodField::EnumAllLocals | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50da5af616c56276a0299a0d08e6eeb0b88181cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727340"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Vytvoří čítač výčtu pro všechny místní proměnné metody, včetně těch, které jsou generovány interně kompilátorem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`pAddress`\
[v] Objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) představující ladicí adresu v rámci metody, odkazující na určitý obor nebo kontext.

`ppLocals`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam všech místních obyvatel v zadaném oboru. v opačném případě vrátí hodnotu null označující žádné místní.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné místní. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Jsou uvedeny pouze proměnné definované v rámci bloku, který obsahuje danou adresu ladění. Tato metoda zahrnuje všechny místní hodnoty generované kompilátorem. Pokud vše, co je potřeba, jsou locals explicitně definované ve zdroji, volání [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) metoda.

 Metoda může obsahovat více kontextů oboru nebo bloků.

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
