---
description: Vytvoří enumerátor pro typ každého argumentu, který je vyžadován pro volání metody.
title: 'IDebugMethodField:: EnumArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04815bb1fc148893c5b594223f6b92bfb7e0d97f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172122"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Vytvoří enumerátor pro typ každého argumentu, který je vyžadován pro volání metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam typů argumentů. Vrátí hodnotu null, pokud nejsou žádné argumenty.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou k dispozici žádné argumenty. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek je objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje typy jednotlivých parametrů. Zavolejte metodu [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pro načtení informací o typu každého parametru.

 Pokud je název parametru vyžadován společně s typem, zavolejte metodu [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
