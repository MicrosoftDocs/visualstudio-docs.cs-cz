---
title: 'IDebugProgram2:: terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722744"
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
