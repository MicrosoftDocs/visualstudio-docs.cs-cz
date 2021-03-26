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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d87d863b954a9865ff3960f2f2cdd45ac40ce58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065395"
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
