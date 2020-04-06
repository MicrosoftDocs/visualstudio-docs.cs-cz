---
title: IDebugClassField::GetEnclosingClass | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734394"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Získá třídu, která obklopuje tuto třídu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parametry
`ppClassField`\
[out] Vrátí objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představující ohraničující třídu. Vrátí hodnotu null, pokud neexistuje žádná ohraničující třída.

## <a name="return-value"></a>Návratová hodnota
Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Pokud je třída reprezentovaná tímto objektem [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) vnořenou třídou, `ppClassField` pak parametr vrátí `IDebugClassField` objekt představující ohraničující třídu. Například vzhledem k této definici třídy:

```
class RootClass {
    class NestedClass { }
};
```

Volání `GetEnclosingClass` metody na `IDebugClassField` objekt představující `NestedClass` třídu `IDebugClassField` vrátí objekt `RootClass`představující třídu .

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
