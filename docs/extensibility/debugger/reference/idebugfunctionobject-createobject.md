---
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6085e974f58346eba7b38e76e5588b34fc3ff2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929981"
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
pro Objekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) představující konstruktor objektu, který má být vytvořen.

`dwArgs`\
pro Počet parametrů v `pArg` poli. Představuje počet parametrů předaných konstruktoru.

`pArg`\
pro Pole objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představujících parametry předané konstruktoru.

`ppObject`\
mimo Vrátí `IDebugObject` reprezentaci nově vytvořeného objektu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zavolejte tuto metodu pro vytvoření objektu, který představuje instanci třídy (nebo jiného komplexního typu, který vyžaduje konstruktor), který je parametrem funkce, která je reprezentovaná [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraním.

 Pokud parametr objektu nevyžaduje konstruktor, zavolejte metodu [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
