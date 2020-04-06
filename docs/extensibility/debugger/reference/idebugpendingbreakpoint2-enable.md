---
title: IDebugPendingBreakpoint2::Povolit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f796aef9533e3861a870b0a0543ae6b4aeb11de1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725890"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Přepíná povolený stav čekající zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable(
    int fEnable
);
```

## <a name="parameters"></a>Parametry
`fEnable`\
[v] Nastavte nenulovou`TRUE`hodnotu ( ) chcete-li`FALSE`povolit čekající zarážku nebo nulu ( ) zakázat.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_BP_DELETED` pokud byla zarážka odstraněna.

## <a name="remarks"></a>Poznámky
Pokud je povolena nebo zakázána čekající zarážka, jsou všechny zarážky z ní vázány na stejný stav.

Tato metoda může být volána tolikrát, kolikrát je to nutné, i v případě, že zarážka je již povolena nebo zakázána.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CPendingBreakpoint` tuto metodu pro jednoduchý objekt, který zveřejňuje rozhraní [IDebugPendingBreakpoint2.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

```cpp
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the bound breakpoint member variable is valid, then enable or
        // disable the bound breakpoint.
        if (m_pBoundBP)
        {
            m_pBoundBP->Enable(fEnable);
        }
        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to enabled or disabled depending on the passed BOOL condition.
        m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;
        hr = S_OK;

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
