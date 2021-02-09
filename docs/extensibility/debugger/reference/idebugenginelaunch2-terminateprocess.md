---
title: 'IDebugEngineLaunch2:: TerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::TerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::TerminateProcess
ms.assetid: f7039e7f-5f57-4222-9ad2-11a66b2da6e0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19222c3cc6ec7e3b09cfa16bdb82820ecc702451
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892798"
---
# <a name="idebugenginelaunch2terminateprocess"></a>IDebugEngineLaunch2::TerminateProcess
Ukončí proces.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT TerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int TerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametry
`pProcess`\
pro Objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , který představuje proces, který má být ukončen.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Před voláním této metody zavolejte metodu [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md) .

## <a name="see-also"></a>Viz také
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)
