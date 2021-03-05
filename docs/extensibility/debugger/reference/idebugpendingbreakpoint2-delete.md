---
description: Odstraní tuto nevyřízenou zarážku a všechny zarážky, které jsou z něho svázané.
title: IDebugPendingBreakpoint2::D dstranit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Delete
helpviewer_keywords:
- IDebugPendingBreakpoint2::Delete method
- Delete method
ms.assetid: 4cb5ed81-6f0c-41ce-a770-5adb6b4bf5d9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 459e21fa7cc9e43d09d56f4537dd9a3bf2a978b3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143074"
---
# <a name="idebugpendingbreakpoint2delete"></a>IDebugPendingBreakpoint2::Delete
Odstraní tuto nevyřízenou zarážku a všechny zarážky, které jsou z něho svázané.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Delete(
    void
);
```

```csharp
int Delete();
```

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí, `E_BP_DELETED` zda byla zarážka odstraněna.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CPendingBreakpoint` objekt, který implementuje rozhraní [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

```cpp
HRESULT CPendingBreakpoint::Delete(void)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the pending breakpoint has bound and has an associated bound
        // breakpoint, delete and release the bound breakpoint and set the
        // pointer to NULL.
        if (m_pBoundBP)
        {
            m_pBoundBP->Delete();
            m_pBoundBP->Release();
            m_pBoundBP = NULL;
        }
        // If the pending breakpoint did not bind and has an associated
        // error breakpoint, release the error breakpoint and set the
        // pointer to NULL.
        if (m_pErrorBP)
        {
            m_pErrorBP->Release();
            m_pErrorBP = NULL;
        }

        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to deleted.
        m_state.state = PBPS_DELETED;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
