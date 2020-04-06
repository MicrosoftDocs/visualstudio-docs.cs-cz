---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f208c52bd45953aaad9efab9b6b65b15b3b759c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735355"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
Vytvoří čítač zarážky, které byly vázány na tuto událost.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumBoundBreakpoints( 
    IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
    out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Vrátí objekt [IEnumDebugBoundBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) který vyjmenovává všechny zarážky vázané z této události.

## <a name="return-value"></a>Návratová hodnota
Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud neexistují žádné vázané zarážky; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Seznam vázaných zarážek je pro ty, které jsou vázány na tuto událost a nemusí být celý seznam zarážek vázaných z čekající zarážky. Chcete-li získat seznam všech zarážek vázaných na čekající zarážku, zavolejte metodu [GetPendingBreakpoint,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) abyste získali přidružený objekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) a pak zavolejte metodu [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) abyste získali objekt [IEnumDebugBoundBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) který obsahuje všechny vázané zarážky pro čekající zarážku.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro **cBreakpointSetDebugEventBase** objekt, který zpřístupňuje rozhraní [IDebugBreakpointBoundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(
    IEnumDebugBoundBreakpoints2 **ppEnum)
{
    HRESULT hRes = E_FAIL;

    if ( ppEnum )
    {
        if ( m_pEnumBound )
        {
            hRes = m_pEnumBound->Clone(ppEnum);

            if ( EVAL(S_OK == hRes) )
                (*ppEnum)->Reset();
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Viz také
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
