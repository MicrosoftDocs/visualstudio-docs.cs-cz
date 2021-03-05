---
description: Toto rozhraní představuje vyhodnocovací filtr výrazů.
title: IDebugExpressionEvaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b2e1fb465155bac2aa4be2b0d0a041715bf63bfa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152348"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Toto rozhraní představuje vyhodnocovací filtr výrazů.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Vyhodnocení výrazu musí implementovat toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
Chcete-li získat toto rozhraní, vytvořte instanci vyhodnocení výrazu prostřednictvím `CoCreateInstance` metody pomocí ID třídy (CLSID) vyhodnocení. Podívejte se na příklad.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDebugExpressionEvaluator` .

|Metoda|Popis|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) (Parsování)|Převede řetězec výrazu na analyzovaný výraz.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Získá místní proměnné, argumenty a další vlastnosti metody.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Převede umístění metody a posun na adresu paměti.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Určuje jazyk, který se použije k vytváření tisknutelných výsledků.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Nastaví kořen registru. Používá se pro souběžné ladění.|

## <a name="remarks"></a>Poznámky
V typické situaci modul ladění (DE) vytvoří instanci vyhodnocovacího filtru výrazů (EE) jako výsledek volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Vzhledem k tomu, že DE zná jazyk a dodavatele v et, který chce použít, DE Získá identifikátor CLSID EE z registru ( [pomocníka sady SDK pro funkci ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `GetEEMetric` , pomáhá s tímto načítáním).

Po vytvoření instance [EE volání de vyvolá analýzu výrazu](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) a uloží jej do objektu [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) . Později volání [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) vyhodnotí výraz.

## <a name="requirements"></a>Požadavky
Záhlaví: ee. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit instanci vyhodnocovacího filtru pro daný poskytovatele symbolů a adresu ve zdrojovém kódu. Tento příklad používá funkci, `GetEEMetric` z [pomocníků sady SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) knihovny dbgmetric. lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
