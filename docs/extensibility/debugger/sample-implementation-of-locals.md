---
title: Ukázková implementace místních obyvatel | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713077"
---
# <a name="sample-implementation-of-locals"></a>Ukázková implementace místních obyvatel
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Následuje přehled o tom, jak Visual Studio získá místní pro metodu z vyhodnocení výrazu (EE):

1. Visual Studio volá ladicí modul (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) získat [objekt IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) který představuje všechny vlastnosti rámce zásobníku, včetně místních obyvatel.

2. `IDebugStackFrame2::GetDebugProperty`volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) získat objekt, který popisuje metodu, ve které došlo k zarážky. DE poskytuje zprostředkovatele symbolu ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adresu ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) a pořadač ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`volá [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) s `IDebugAddress` dodaným objektem získat [IDebugContainerField,](../../extensibility/debugger/reference/idebugcontainerfield.md) který představuje metodu obsahující zadanou adresu.

4. Rozhraní `IDebugContainerField` je dotazován o rozhraní [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Je to rozhraní, které poskytuje přístup k místní metody.

5. `IDebugExpressionEvaluator::GetMethodProperty`instance třídy (volána `CFieldProperty` v ukázce), která spouští `IDebugProperty2` rozhraní reprezentovat místní hodnoty metody. Objekt `IDebugMethodField` je umístěn `CFieldProperty` v tomto `IDebugSymbolProvider`objektu spolu s , `IDebugAddress`a `IDebugBinder` objekty.

6. Při `CFieldProperty` inicializování objektu [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) je volána na `IDebugMethodField` objekt získat [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) struktury, která obsahuje všechny zobrazitelné informace o samotné metody.

7. `IDebugExpressionEvaluator::GetMethodProperty`vrátí `CFieldProperty` objekt jako `IDebugProperty2` objekt.

8. Visual Studio volá [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) na vrácený `IDebugProperty2` objekt s filtrem `guidFilterLocalsPlusArgs`, který vrátí Objekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující místní hodnoty metody. Tento výčet je vyplněn [voláním EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio volá [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) získat [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturu pro každý místní. Tato struktura obsahuje ukazatel `IDebugProperty2` na rozhraní pro místní.

10. Visual Studio volá [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pro každý místní získat místní název, hodnotu a typ. Tyto informace se zobrazí v okně **Locals.**

## <a name="in-this-section"></a>V tomto oddílu
 [Implementovat vlastnost GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Popisuje implementaci [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Vyjmenovat místní obyvatele](../../extensibility/debugger/enumerating-locals.md) Popisuje, jak ladicí modul (DE) provede volání výčet místníproměnné nebo argumenty.

 [Získat místní vlastnosti](../../extensibility/debugger/getting-local-properties.md) Popisuje, jak DE volání získat název, typ a hodnotu jednoho nebo více místních obyvatel.

 [Získat místní hodnoty](../../extensibility/debugger/getting-local-values.md) Popisuje získání hodnoty local, která vyžaduje služby objektu pořadače dané kontextu hodnocení.

 [Vyhodnocení místních obyvatel](../../extensibility/debugger/evaluating-locals.md) Vysvětluje, jak jsou vyhodnocovány místní obyvatelé.

## <a name="related-sections"></a>Související oddíly
 [Souvislosti hodnocení](../../extensibility/debugger/evaluation-context.md) Poskytuje argumenty, které jsou předány při VOLÁNÍ DE vyhodnocení výrazu (EE).

 [MyCEE vzorek](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Ukazuje jeden přístup implementace k vytvoření vyhodnocení výrazu pro jazyk MyC.

## <a name="see-also"></a>Viz také
- [Zobrazení místních obyvatel](../../extensibility/debugger/displaying-locals.md)
