---
title: IDebugBreakpointUnboundEvent2::GetReason | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9830309f0a40aee37982554e8920a95d289eb74c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734717"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
Získá důvod, proč zarážka byla nevázaná.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason
);
```

```csharp
int GetReason(
    out enum_ BP_UNBOUND_REASON pdwUnboundReason
);
```

## <a name="parameters"></a>Parametry
`pdwUnboundReason`\
[out] Vrátí hodnotu z [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) výčtu určující důvod, proč byla zarážka nevázaná.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Důvody zahrnují zarážku je odskočit do jiného umístění po operaci úprava a pokračovat nebo určení, že zarážka byla vázána omylem.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro **cbreakpointUnboundDebugEventBase** objekt, který zpřístupňuje rozhraní [IDebugBreakpointUnboundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason)
{
    HRESULT hRes = E_FAIL;

    if ( EVAL(pdwUnboundReason) )
    {
        *pdwUnboundReason = m_dwReason;

        hRes = S_OK;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Viz také
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
