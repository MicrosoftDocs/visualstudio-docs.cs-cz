---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 274610f84ff0447684eae6f5f728672d61aa08e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926160"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Získá [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) objekt, který je popsaný i důvod, proč nebyl vázán zarážku.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `ppErrorBP`  
 [out] Vrátí [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) objekt, který popisuje upozornění nebo chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po `IDebugErrorBreakpoint2` získat rozhraní, zavolejte [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) metodu k získání [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) objektu. Pak bude [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metody slouží k určení neplatné umístění, neplatný výraz nebo důvody, proč nebyl vázán čekající zarážka, jako je například kód není načtený a tak dále.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CBreakpointSetDebugEventBase** objekt, který zveřejňuje [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) rozhraní.  
  
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
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)