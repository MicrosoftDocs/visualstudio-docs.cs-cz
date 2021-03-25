---
description: Připojí se k přidruženému programu nebo odloží proces připojení k metodě Attach.
title: 'IDebugProgramNodeAttach2:: Attach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 334a8e4bdf559e2d39d52a03dcf1a849f73af3e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087259"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Připojí se k přidruženému programu nebo odloží proces připojení k metodě [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parametry
`guidProgramId`\
[in] `GUID` k přiřazení k přidruženému programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí, `S_FALSE` zda by metoda [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) neměla být volána. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána během procesu připojení před voláním metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . `OnAttach`Metoda může provádět samotný proces připojení (v takovém případě se tato metoda vrátí `S_FALSE` ) nebo odložit proces připojení k `IDebugEngine2::Attach` metodě ( `OnAttach` Metoda vrátí hodnotu `S_OK` ). V obou událostech `OnAttach` může metoda nastavit program, který je `GUID` laděn na dané `GUID` .

## <a name="see-also"></a>Viz také
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
