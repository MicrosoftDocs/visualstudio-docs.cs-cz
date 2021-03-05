---
description: Vytvoří objekt Array.
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aee0617364321e5a18f0ea83ef7f19f1388209df
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166486"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Vytvoří objekt Array. Toto pole může obsahovat hodnoty primitivního nebo instančního objektu.

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
pro Určuje hodnotu z výčtu [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) , která označuje typ nového objektu Array.

`pClassField`\
pro Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující třídu objektu, pokud se vytváří pole hodnot instance objektu. Pokud vytváříte pole primitivních objektů, tento parametr je hodnota null.

`dwRank`\
pro Rozměr nebo počet rozměrů pole.

`dwDims`\
pro Velikosti jednotlivých rozměrů pole.

`dwLowBounds`\
pro Původ každé dimenze (obvykle 0 nebo 1).

`ppObject`\
mimo Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující nově vytvořené pole. Toto je vlastně objekt [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zavolejte tuto metodu pro vytvoření objektu, který představuje parametr pole pro funkci, která je reprezentovaná [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraním.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
