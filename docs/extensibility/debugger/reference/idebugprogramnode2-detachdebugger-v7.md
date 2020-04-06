---
title: IDebugProgramNode2::DetachDebugger_V7 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722108"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Zastaralé. NEPOUŽÍVEJTE.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Návratová hodnota

Implementace by měla `E_NOTIMPL`vždy vrátit .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 se tato metoda `E_NOTIMPL`již nepoužívá a měla by vždy vrátit .

Tato metoda je volána při neočekávaně ukončení ladicího programu. Při volání této metody DE by měl pokračovat v programu, jako by uživatel odpojen od něj. Žádné další události ladění by měly být odeslány. Program by měl být ve stavu, ve kterém je připojitelný z jiné instance ladicího programu.

## <a name="see-also"></a>Viz také

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
