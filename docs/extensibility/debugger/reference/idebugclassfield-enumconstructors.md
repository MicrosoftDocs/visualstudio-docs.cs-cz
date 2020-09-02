---
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734467"
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
