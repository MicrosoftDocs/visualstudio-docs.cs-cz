---
description: Načte identifikátor GUID pro tento program.
title: 'IDebugProgram2:: GetProgramId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45721d4214c396f3366bd23c2bc48e74a1427ec8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168960"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Načte identifikátor GUID pro tento program.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parametry
`pguidProgramId`\
mimo Vrátí `GUID` pro tento program.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Ladicí stroj (DE) musí vrátit identifikátor programu původně předaný metodě [Attach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) nebo [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . To umožňuje identifikaci programu napříč komponentami ladicího programu.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
