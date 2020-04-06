---
title: IDebugEngineLaunch2::CanTerminateProcess | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730557"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Určuje, zda lze proces ukončit.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametry
`pProcess`\
[v] [Objekt IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) který představuje proces, který má být ukončen.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `S_FALSE` pokud modul nemůže ukončit proces, například protože přístup je odepřen.

## <a name="remarks"></a>Poznámky
 Pokud tato `S_OK`metoda vrátí , pak to [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) metoda může být volána skutečně ukončit proces.

## <a name="see-also"></a>Viz také
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
