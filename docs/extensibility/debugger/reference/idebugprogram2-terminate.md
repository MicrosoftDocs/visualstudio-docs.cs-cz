---
title: IDebugProgram2::Ukončit | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722744"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Ukončí program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud je to možné, program bude ukončen a uvolněn z procesu; v opačném případě ladicí modul (DE) provede všechny nezbytné vyčištění.

 Tato metoda nebo [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metoda je volána IDE, obvykle v reakci na uživatele zastavení všech ladění. Implementace této metody by měla v ideálním případě ukončit program v rámci procesu. Pokud to není možné, DE by měl zabránit spuštění programu nic víc v tomto procesu (a provést všechny nezbytné vyčištění). Pokud `IDebugProcess2::Terminate` byla metoda volána ide, celý proces bude ukončen `IDebugProgram2::Terminate` a někdy po volání metody.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
