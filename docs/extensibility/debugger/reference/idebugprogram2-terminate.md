---
description: Ukončí program.
title: 'IDebugProgram2:: terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 404df2be6718ab691ec47081b6fd400a1ddc8891
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084464"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Ukončí program.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud je to možné, program se ukončí a uvolní z tohoto procesu. v opačném případě modul ladění (DE) provede veškeré nezbytné vyčištění.

 Tato metoda nebo metoda [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) je volána rozhraním IDE, obvykle v reakci na uživatele, který zastavuje ladění. Implementace této metody by v ideálním případě ukončila program v rámci procesu. Pokud to není možné, by příkaz DE měl zabránit programu v běhu žádné další v tomto procesu (a provést potřebné vyčištění). Pokud `IDebugProcess2::Terminate` byla metoda volána rozhraním IDE, celý proces bude ukončen po `IDebugProgram2::Terminate` volání metody.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) (Ukončení)
