---
title: IDebugExpression2::EvaluateSync | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729671"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Tato metoda vyhodnocuje výraz synchronně.

## <a name="syntax"></a>Syntaxe

```cpp
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

## <a name="parameters"></a>Parametry
`dwFlags`\
[v] Kombinace příznaků z výčtu [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) které řídí vyhodnocení výrazu.

`dwTimeout`\
[v] Maximální doba v milisekundách čekání před návratem z této metody. Slouží `INFINITE` k čekání na neurčito.

`pExprCallback`\
[v] Tento parametr je vždy nulovou hodnotou.

`ppResult`\
[out] Vrátí objekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který obsahuje výsledek vyhodnocení výrazu.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Některé typické chybové kódy jsou:

|Chyba|Popis|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|V současné době je vyhodnocován jiný výraz a současné vyhodnocení výrazu není podporováno.|
|E_EVALUATE_TIMEOUT|Časový čas vyhodnocení vypršel.|

## <a name="remarks"></a>Poznámky
Pro synchronní vyhodnocení není nutné odeslat událost zpět do sady Visual Studio po dokončení hodnocení.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CExpression` tuto metodu pro jednoduchý objekt, který implementuje rozhraní [IDebugExpression2.](../../../extensibility/debugger/reference/idebugexpression2.md)

```cpp
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
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
