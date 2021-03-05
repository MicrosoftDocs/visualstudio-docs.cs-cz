---
description: Získá třídu, která uzavře tuto třídu.
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c08550204c8a2860d8fd7870e4ac949e9e9319c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164198"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Získá třídu, která uzavře tuto třídu.

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
mimo Vrátí objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představující ohraničující třídu. Vrací hodnotu null, pokud neexistuje žádná ohraničující třída.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Pokud je třída reprezentovaná tímto objektem [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) vnořenou třídou, pak `ppClassField` parametr vrátí `IDebugClassField` objekt představující ohraničující třídu. Například s ohledem na tuto definici třídy:

```
class RootClass {
    class NestedClass { }
};
```

Volání `GetEnclosingClass` metody na `IDebugClassField` objektu představující `NestedClass` třídu vrátí `IDebugClassField` objekt představující třídu `RootClass` .

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
