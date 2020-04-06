---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe22f18d4574ffde48cea975bff8d8f5801ca465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735068"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Získá [Objekt IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) který popisuje důvod, proč nebyla vázána zarážka.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

## <a name="parameters"></a>Parametry
`ppErrorBP`\
[out] Vrátí objekt [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) který popisuje upozornění nebo chybu.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Po `IDebugErrorBreakpoint2` získání rozhraní volejte metodu [GetBreakpointResolution,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abyste získali objekt [IDebugErrorBreakpointResolution2.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) Potom [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metoda může být použita k určení neplatné umístění, neplatný výraz nebo důvody, proč čekající zarážka nebyla vázána, jako je například kód ještě není načten a tak dále.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro objekt **CBreakpointSetDebugEventBase,** který zpřístupňuje rozhraní [IDebugBreakpointErrorEvent2.](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
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
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
