---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0593a2ee8c519169bd8cb2eb23a83c4f5f3506a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898622"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Zastaralé. NEPOUŽÍVEJTE.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Návratová hodnota

Implementace by měla vždycky vracet `E_NOTIMPL` .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 tato metoda již není používána a měla by vždy vracet `E_NOTIMPL` .

Tato metoda se volá, když se ladicí program neočekávaně ukončí. Při volání této metody by měl DE obnovit program, jako by byl uživatel odpojen. Nejsou odesílány žádné další události ladění. Program by měl být ve stavu, ve kterém je připojen z jiné instance ladicího programu.

## <a name="see-also"></a>Viz také

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
