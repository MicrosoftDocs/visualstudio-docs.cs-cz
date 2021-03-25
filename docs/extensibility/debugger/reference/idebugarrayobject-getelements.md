---
description: Získá enumerátor všech prvků pole.
title: 'IDebugArrayObject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42ecdcedef00ee9d9ca56a365689ff819375fb82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094351"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Získá enumerátor všech prvků pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí objekt [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) , který umožňuje výčet všech prvků.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Jako alternativu použijte metody [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) a [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) k iterování skrze prvky.

## <a name="see-also"></a>Viz také
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
