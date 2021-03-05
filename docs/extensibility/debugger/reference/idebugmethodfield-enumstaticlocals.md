---
description: Vytvoří enumerátor pro statické lokální proměnné metody.
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c31d8644bf918b57c1d97b2ee2ddbc840a33ff1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164978"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Vytvoří enumerátor pro statické lokální proměnné metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parametry
`ppLocals`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam statických národních prostředí. Vrátí hodnotu null, pokud nejsou žádné statické lokální hodnoty.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádná statická národní prostředí. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek je objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje různé typy statických národních prostředí. Voláním metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) pro každý objekt určíte přesně to, jaký typ statické lokální proměnné objekt představuje.

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
