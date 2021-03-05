---
description: Vytvoří objekt bez konstruktoru.
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0f5ddd90f979c3646014bc82aa55402386a5f36
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151828"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Vytvoří objekt bez konstruktoru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pClassObject`\
pro Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující typ objektu, který má být vytvořen.

`ppObject`\
mimo Vrátí [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující nově vytvořený objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zavolejte tuto metodu pro vytvoření objektu, který představuje instanci struktury nebo komplexního typu (který nevyžaduje konstruktor), který je parametrem funkce, která je reprezentovaná [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraním.

 Pokud parametr objektu vyžaduje konstruktor, zavolejte metodu [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
