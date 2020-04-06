---
title: IDebugClassField::EnumNestedClasses | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e6ef918b55d8b311380264d688085b0d2803601
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734430"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Vytvoří čítač výčtu pro třídy vnořené v této třídě.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam vnořených tříd. Vrátí hodnotu null, pokud neexistují žádné vnořené třídy.

## <a name="return-value"></a>Návratová hodnota
Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné vnořené třídy. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Každý prvek výčtu je objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) popisující vnořenou třídu.

Vnořená třída je třída definovaná uvnitř jiné třídy. Například:

```
class RootClass {
   class NestedClass { }
};
```

[Výčet IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) by obsahovat jeden `NestedClass` objekt představující třídu.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
