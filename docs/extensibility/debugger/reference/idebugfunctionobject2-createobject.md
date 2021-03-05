---
description: Vytvoří objekt, který používá konstruktor se zadaným nastavením příznaku vyhodnocení a hodnotou časového limitu.
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143139"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Vytvoří objekt, který používá konstruktor se zadaným nastavením příznaku vyhodnocení a hodnotou časového limitu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parametry
`pConstructor`\
pro Objekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , který představuje konstruktor objektu, který má být vytvořen.

`dwArgs`\
pro Počet parametrů v `pArg` poli. Představuje počet parametrů předaných konstruktoru.

`pArgs`\
pro Pole objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , které představují parametry předané konstruktoru.

`dwEvalFlags`\
pro Kombinace příznaků z výčtu [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) , která určuje, jak má být provedeno vyhodnocení.

`dwTimeout`\
pro Maximální doba (v milisekundách), po kterou se má čekat, než se vrátí z této metody. Nepoužívejte **nekonečné** čekání na neomezenou dobu.

`ppObject`\
mimo Vrátí **IDebugObject** představující nově vytvořený objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Zavolejte tuto metodu pro vytvoření objektu, který představuje instanci třídy, nebo jiného komplexního typu, který vyžaduje konstruktor, který je parametrem.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
