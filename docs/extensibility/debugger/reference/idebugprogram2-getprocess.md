---
title: IDebugProgram2::GetProcess | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722793"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Získejte proces, ve které je tento program spuštěn.

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
[out] Vrátí rozhraní [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) které představuje proces.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud ladicí modul (DE) implementuje rozhraní [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) de implementace `E_NOTIMPL` této metody by měla vždy vrátit, protože DE nelze určit, který proces je spuštěn v a proto nemůže uspokojit implementaci této metody.

 Implementace `IDebugEngineLaunch2` rozhraní znamená, že DE musí vědět, jak vytvořit proces; proto de implementace rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) je schopen vědět, jaký proces je spuštěn v.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
