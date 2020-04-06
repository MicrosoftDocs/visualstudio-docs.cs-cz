---
title: IDebugFunctionObject2::CreateObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728475"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Vytvoří objekt, který používá konstruktor dané nastavení hodnocení příznak a hodnotu časového času.

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
[v] [Objekt IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) který představuje konstruktor objektu, který má být vytvořen.

`dwArgs`\
[v] Počet parametrů v `pArg` poli. Představuje počet parametrů předaných konstruktoru.

`pArgs`\
[v] Pole [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty, které představuje parametry předané konstruktoru.

`dwEvalFlags`\
[v] Kombinace příznaků z výčtu [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) které určují, jak má být hodnocení provedeno.

`dwTimeout`\
[v] Maximální doba v milisekundách čekání před návratem z této metody. Použití **INFINITE** čekat neomezeně dlouho.

`ppObject`\
[out] Vrátí **objekt IDebugObject** představující nově vytvořený objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Volání této metody k vytvoření objektu, který představuje instanci třídy nebo jiného komplexního typu, který vyžaduje konstruktor, který je parametrem.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
