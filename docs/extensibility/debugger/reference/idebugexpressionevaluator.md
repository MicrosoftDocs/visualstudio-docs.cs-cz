---
title: IDebugExpressionEvaluator | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729382"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Toto rozhraní představuje vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Vyhodnocení výrazu musí implementovat toto rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
Chcete-li získat toto rozhraní, vytvořte `CoCreateInstance` instanci vyhodnocení výrazu prostřednictvím metody pomocí ID třídy (CLSID) vyhodnocení. Viz příklad.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
V následující tabulce jsou `IDebugExpressionEvaluator`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Převede řetězec výrazu na analyzovaný výraz.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Získá místní proměnné, argumenty a další vlastnosti metody.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Převede umístění metody a posun na adresu paměti.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Určuje, který jazyk se má použít k vytvoření tiskových výsledků.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Nastaví kořenový adresář registru. Používá se pro ladění vedle sebe.|

## <a name="remarks"></a>Poznámky
V typické situaci ladicí modul (DE) konkretizuje vyhodnocení výrazu (EE) v důsledku volání [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Vzhledem k tomu, že DE zná jazyk a dodavatele EE, který chce použít, de získá CLSID EE z registru `GetEEMetric` [(pomocné sedy sdk pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkce, , pomáhá s tímto načítání).

Po EE je vytvořena instance, DE volá [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) analyzovat výraz a uložit jej do [Objektu IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Později volání [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) vyhodnotí výraz.

## <a name="requirements"></a>Požadavky
Záhlaví: ee.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak vytvořit instanci vyhodnocení výrazu dané zprostředkovatele symbola a adresu ve zdrojovém kódu. Tento příklad používá `GetEEMetric`funkci , z [pomocníků sady SDK pro knihovnu ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

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
