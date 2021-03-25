---
description: Vytvoří enumerátor pro konstruktory pro tuto třídu.
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efba9ecb25259b6aa4998a1f22fedf443c1281a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084971"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Vytvoří enumerátor pro konstruktory pro tuto třídu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`cMatch`\
pro Hodnota z výčtu [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) , která určuje typ konstruktorů, které se mají vyčíslit.

`ppEnum`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam konstruktorů. Vrací hodnotu null, pokud nejsou žádné konstruktory.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádné konstruktory. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek výčtu je objekt [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) popisující metodu konstruktoru.

 Seznam konstruktorů obvykle neobsahuje výchozí konstruktory dodávané kompilátorem.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
