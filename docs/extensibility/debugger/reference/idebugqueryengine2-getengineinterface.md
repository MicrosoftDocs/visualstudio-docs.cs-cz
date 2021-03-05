---
description: Získá vlastní rozhraní ladicího stroje (DE).
title: 'IDebugQueryEngine2:: GetEngineInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbf727de01c8cbf34d645aff4e0a64aeb476ebbd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167838"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Získá vlastní rozhraní ladicího stroje (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parametry
`ppUnk`\
mimo Vrátí `IUnknown` objekt, který představuje ladicí modul (de) a který se může dotazovat na jakékoli jiné platné rozhraní přidružené k de (například [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) nebo [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Výsledné rozhraní by se mělo používat opatrně, protože volání rozhraní načtených z této metody obchází zpracování správce ladění relace a může způsobit, že se SDM načítá do špatného stavu nebo generuje chyby při ladění.

## <a name="see-also"></a>Viz také
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
