---
title: IDebugExpression2::EvaluateSync | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4a10860a9edd93e92686eb1c054778b9e5ac16a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786948"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda vyhodnotí výraz synchronně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Kombinace příznaků z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) výčet, který řídí vyhodnocení výrazu.  
  
 `dwTimeout`  
 [in] Maximální doba v milisekundách pro čekání před návratem z této metody. Použití `INFINITE` čekat po neomezenou dobu.  
  
 `pExprCallback`  
 [in] Tento parametr je vždy hodnota null.  
  
 `ppResult`  
 [out] Vrátí [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objekt, který obsahuje výsledek vyhodnocení výrazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. Jsou některé typické chybové kódy:  
  
|Chyba|Popis|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Jiný výraz je právě vyhodnocována a vyhodnocení souběžných výrazu se nepodporuje.|  
|E_EVALUATE_TIMEOUT|Vypršel časový limit vyhodnocení.|  
  
## <a name="remarks"></a>Poznámky  
 Pro synchronní hodnocení není nutné pro odeslání události zpět do sady Visual Studio po dokončení hodnocení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CExpression` objekt, který implementuje [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) rozhraní.  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

