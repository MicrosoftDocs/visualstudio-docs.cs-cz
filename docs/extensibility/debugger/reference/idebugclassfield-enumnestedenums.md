---
title: 'IDebugClassField:: EnumNestedEnums | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734407"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Vytvoří enumerátor pro vnořené enumerátory této třídy.

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
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam vnořených výčtů. Vrací hodnotu null, pokud nejsou žádné vnořené výčty.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádné vnořené enumerátory. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Každý prvek výčtu je objekt [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) popisující vnořený výčet.

Výčet deklarovaný uvnitř třídy je považován za vnořený výčet. Například předané:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`Metoda vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) , který obsahuje jeden objekt [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) , který představuje `NestedEnum` výčet.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
