---
title: IDebugFunctionObject::CreatePrimitiveObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728530"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Vytvoří primitivní datový objekt, například jednoduché celé číslo.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ot`\
[v] Hodnota z [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) výčtu představující typ primitivní vytvořit.

`ppObject`\
[out] Vrátí [objekt IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující nově vytvořený objekt.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Volání této metody k vytvoření objektu, který představuje primitivní objekt, který je parametrem funkce, která je reprezentována rozhraním [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Například pokud je řetězec výrazu "myString(5)", tato metoda by se použít k vytvoření objektu představující celé číslo 5.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
