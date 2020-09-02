---
title: 'IDebugClassField:: EnumNestedClasses | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734430"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Vytvoří enumerátor pro třídy vnořené v této třídě.

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
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam vnořených tříd. Vrací hodnotu null, pokud nejsou žádné vnořené třídy.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou žádné vnořené třídy. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Každý prvek výčtu je objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) popisující vnořenou třídu.

Vnořená třída je třída definovaná uvnitř jiné třídy. Příklad:

```
class RootClass {
   class NestedClass { }
};
```

Výčet [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) by obsahoval jeden objekt reprezentující `NestedClass` třídu.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
