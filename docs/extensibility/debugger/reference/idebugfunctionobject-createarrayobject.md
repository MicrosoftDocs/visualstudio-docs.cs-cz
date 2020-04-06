---
title: IDebugFunctionObject::CreateArrayObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728616"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Vytvoří objekt pole. Toto pole může obsahovat buď hodnoty primitivnínebo objektové instance.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ot`\
[v] Určuje hodnotu z [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) výčtu označující typ nového objektu pole.

`pClassField`\
[v] Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující třídu objektu, pokud vytvářípole hodnot instancí objektu. Pokud vytváříte pole primitivních objektů, je tento parametr nulovou hodnotou.

`dwRank`\
[v] Pořadí nebo počet dimenzí pole.

`dwDims`\
[v] Velikosti každé dimenze pole.

`dwLowBounds`\
[v] Počátek každé dimenze (obvykle 0 nebo 1).

`ppObject`\
[out] Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující nově vytvořené pole. Toto je ve skutečnosti objekt [IDebugArrayObject.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Volání této metody k vytvoření objektu, který představuje parametr pole pro funkci, která je reprezentována rozhraním [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
