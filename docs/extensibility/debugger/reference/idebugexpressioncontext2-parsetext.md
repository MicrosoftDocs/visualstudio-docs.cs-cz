---
title: IDebugExpressionContext2::PArseText | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8494c9c90c4cb6e94115c542a25e12e948f7064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729645"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analyzuje výraz v textové podobě pro pozdější vyhodnocení.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parametry
`pszCode`\
[v] Výraz, který má být analyzován.

`dwFlags`\
[v] Kombinace příznaků z [výčtu PARSEFLAGS,](../../../extensibility/debugger/reference/parseflags.md) který řídí analýzu.

`nRadix`\
[v] Radix, který se má použít při analýzě všech číselných informací v . `pszCode`

`ppExpr`\
[out] Vrátí objekt [IDebugExpression2,](../../../extensibility/debugger/reference/idebugexpression2.md) který představuje analyzovaný výraz, který je připraven pro vazbu a vyhodnocení.

`pbstrError`\
[out] Vrátí chybovou zprávu, pokud výraz obsahuje chybu.

`pichError`\
[out] Vrátí index znaků chyby `pszCode` v aplikaci, pokud výraz obsahuje chybu.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Při volání této metody ladicí modul (DE) by měl analyzovat výraz a ověřit jeho správnost. `pbstrError` Parametry `pichError` a mohou být vyplněny, pokud je výraz neplatný.

Všimněte si, že výraz není vyhodnocen, pouze analyzován. Pozdější volání metod [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) vyhodnotí analyzovaný výraz.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CEnvBlock` tuto metodu pro jednoduchý objekt, který zveřejňuje rozhraní [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Tento příklad považuje výraz, který má být analyzován jako název proměnné prostředí a načte hodnotu z této proměnné.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
