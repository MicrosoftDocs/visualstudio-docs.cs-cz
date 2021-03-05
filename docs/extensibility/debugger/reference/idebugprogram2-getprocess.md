---
description: Získejte proces, ve kterém je tento program spuštěn.
title: 'IDebugProgram2:: getprocess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 233bd9bbb41f64b375e899dba9c0be9a9fba3d97
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168986"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Získejte proces, ve kterém je tento program spuštěn.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametry
`ppProcess`\
mimo Vrátí rozhraní [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , které představuje proces.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud modul ladění (DE) neimplementuje rozhraní [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , implementace de této metody by měla vždycky vracet, `E_NOTIMPL` protože de nemůže určit, který proces je spuštěný, a proto nemůže splnit implementaci této metody.

 Implementace `IDebugEngineLaunch2` rozhraní znamená, že de musí znát, jak vytvořit proces; proto implementace rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) je schopna zjistit, v jakém procesu běží.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
