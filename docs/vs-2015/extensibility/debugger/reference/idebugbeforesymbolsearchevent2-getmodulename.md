---
title: IDebugBeforeSymbolSearchEvent2::GetModuleName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 251f3e89dba4ad4385db59d70b9f473d7ad4fb5f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754094"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte název modulu, která se právě ladí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetModuleName(   
   BSTR *pbstrModuleName  
);  
```  
  
```csharp  
public int GetModuleName (  
   string pbstrModuleName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrModuleName`  
 [out] Název modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CDebugBeforeSymbolSearchEventBase** objekt, který zveřejňuje [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) rozhraní.  
  
```cpp#  
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (m_bstrModuleName)  
    {  
  
        *pbstrModuleName = SysAllocString( m_bstrModuleName);  
  
        if (*pbstrModuleName)  
        {  
            hRes = S_OK;  
        }  
    }  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)

