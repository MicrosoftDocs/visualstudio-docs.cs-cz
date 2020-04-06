---
title: IDebugPendingBreakpoint2::Delete | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd6e2d61eb7a7ce927a966281bba2f0cbf470dc6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725913"
---
# <a name="idebugpendingbreakpoint2delete"></a>IDebugPendingBreakpoint2::Delete
Odstraní tuto čekající zarážku a všechny zarážky z ní vázané.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Delete(
    void
);
```

```csharp
int Delete();
```

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_BP_DELETED` pokud byla zarážka odstraněna.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CPendingBreakpoint` tuto metodu pro jednoduchý objekt, který implementuje rozhraní [IDebugPendingBreakpoint2.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

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
