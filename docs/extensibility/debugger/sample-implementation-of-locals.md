---
title: Ukázková implementace místních hodnot | Microsoft Docs
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
ms.openlocfilehash: 86aacb096001bdf634fe019ae9a28f01745c3ce0
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011889"
---
# <a name="sample-implementation-of-locals"></a>Ukázková implementace místních hodnot
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Následuje přehled toho, jak Visual Studio získává místní hodnoty pro metodu z vyhodnocovacího filtru výrazů (EE):

1. Sada Visual Studio volá [GetDebugProperty –](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) modul ladění (de), aby získala objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který představuje všechny vlastnosti rámce zásobníku, včetně místních hodnot.

2. `IDebugStackFrame2::GetDebugProperty` volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) k získání objektu, který popisuje metodu, ve které došlo k zarážce. DE dodá poskytovatele symbolů ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adresu ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) a Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` volá [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) se zadaným `IDebugAddress` objektem, aby získala [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) , která představuje metodu obsahující zadanou adresu.

4. `IDebugContainerField`Pro rozhraní [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) se dotazuje na rozhraní. Je toto rozhraní, které poskytuje přístup k lokálním hodnotám metody.

5. `IDebugExpressionEvaluator::GetMethodProperty` Vytvoří instanci třídy (volanou `CFieldProperty` v ukázce), která spouští `IDebugProperty2` rozhraní pro reprezentaci místních hodnot metody. `IDebugMethodField`Objekt je umístěn v tomto `CFieldProperty` objektu spolu s `IDebugSymbolProvider` `IDebugAddress` objekty, a `IDebugBinder` .

6. Když `CFieldProperty` je objekt inicializován, je volána metoda [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) pro `IDebugMethodField` objekt, aby bylo možné získat [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturu, která obsahuje všechny nezobrazitelné informace o samotné metodě.

7. `IDebugExpressionEvaluator::GetMethodProperty` Vrátí `CFieldProperty` objekt jako `IDebugProperty2` objekt.

8. Visual Studio volá [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) u vráceného `IDebugProperty2` objektu pomocí filtru `guidFilterLocalsPlusArgs` , který vrací objekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující lokální hodnoty metody. Tento výčet je vyplněn voláními [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Po [volání sady](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) Visual Studio k získání [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury pro každé místní prostředí. Tato struktura obsahuje ukazatel na `IDebugProperty2` rozhraní pro místní.

10. Visual Studio volá metodu [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pro každý místní, aby získala název, hodnotu a typ místní proměnné. Tyto informace se zobrazí v okně **místní** hodnoty.

## <a name="in-this-section"></a>V této části
 [Implementovat GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Popisuje implementaci [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Vytvořit výčet místních](../../extensibility/debugger/enumerating-locals.md) hodnot Popisuje, jak ladicí stroj (DE) provede volání výčtu místních proměnných nebo argumentů.

 [Získat místní vlastnosti](../../extensibility/debugger/getting-local-properties.md) Popisuje, jak příkaz DE provede volání, aby získal název, typ a hodnotu jedné nebo více lokálních hodnot.

 [Získat místní hodnoty](../../extensibility/debugger/getting-local-values.md) V této části najdete popis získání hodnoty místního, která vyžaduje služby objektu pořadače uvedené v kontextu vyhodnocení.

 [Vyhodnotit lokální](../../extensibility/debugger/evaluating-locals.md) hodnoty Vysvětluje, jak se vyhodnocují místní hodnoty.

## <a name="related-sections"></a>Související oddíly
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md) Poskytuje argumenty, které jsou předány, když DE volá vyhodnocovací filtr výrazů (EE).

 [Ukázka mycee](/previous-versions/) Ukazuje jeden implementační postup pro vytvoření vyhodnocovacího filtru výrazů pro jazyk MyC.

## <a name="see-also"></a>Viz také:
- [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)