---
title: IDebugExpression2::EvaluateAsync | Dokumentace Microsoftu
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
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b478e5ee9a58a7a44b8614602d333a6d16375e5b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792590"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda asynchronně vyhodnotí výraz.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Kombinace příznaků z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) výčet, který řídí vyhodnocení výrazu.  
  
 `pExprCallback`  
 [in] Tento parametr je vždy hodnota null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. Typické chybový kód je:  
  
|Chyba|Popis|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Jiný výraz je právě vyhodnocována a vyhodnocení souběžných výrazu se nepodporuje.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda by měla vrátit okamžitě po zahájení jeho vyhodnocení výrazu. Při úspěšném vyhodnocení výrazu, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) se musí odeslat na [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) události zpětného volání, jak prostřednictvím [připojit ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) nebo [připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CExpression` objekt, který implementuje [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) rozhraní.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

