---
title: IDebugFunctionObject::CreateObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728594"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Vytvoří objekt pomocí konstruktoru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parametry
`pConstructor`\
[v] [Objekt IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) představující konstruktor objektu, který má být vytvořen.

`dwArgs`\
[v] Počet parametrů v `pArg` poli. Představuje počet parametrů předaných konstruktoru.

`pArg`\
[v] Pole [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty představující parametry předané konstruktoru.

`ppObject`\
[out] Vrátí `IDebugObject` reprezentující nově vytvořený objekt.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Volání této metody k vytvoření objektu, který představuje instanci třídy (nebo jiného komplexního typu, který vyžaduje konstruktor), který je parametrem funkce, která je reprezentována rozhraním [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Pokud parametr objektu nevyžaduje konstruktor, zavolejte metodu [CreateObjectNoConstructor.](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
