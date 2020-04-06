---
title: IDebugClassField::EnumNestedEnums | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38ee3ccd1ffd3130bc918da18c631cf08683f064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734407"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Vytvoří čítač výčtu pro vnořené čítače výčtu této třídy.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam vnořených výčtů. Vrátí hodnotu null, pokud neexistují žádné vnořené výčty.

## <a name="return-value"></a>Návratová hodnota
Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné vnořené čítače výčtu. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Každý prvek výčtu je [Objekt IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) popisující vnořený výčet.

Výčet deklarovaný uvnitř třídy je považován za vnořený výčet. Například vzhledem k tomu, že:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Metoda `EnumNestedEnums` by vrátit [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objekt, který obsahuje jeden [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objekt, který představuje `NestedEnum` výčet.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
