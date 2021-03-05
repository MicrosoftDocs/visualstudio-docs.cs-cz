---
description: Získá pole, ke kterému je přiřazen vlastní atribut.
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4af4569b64a41fc84a09c7e8f2ce0a8f6b42e86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154506"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Získá pole, ke kterému je přiřazen vlastní atribut.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametry
`ppField`\
mimo Vrátí objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje pole, ke kterému je přiřazen vlastní atribut.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Voláním metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) u vráceného objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) určete, jaký druh pole je nadřazený.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
