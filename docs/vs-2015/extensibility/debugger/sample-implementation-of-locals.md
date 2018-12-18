---
title: Ukázková implementace místních hodnot | Dokumentace Microsoftu
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
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ca64ed08060df3a03dbb178fc636ca243e1e48d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756818"
---
# <a name="sample-implementation-of-locals"></a>Ukázková implementace místních hodnot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Tady je přehled o způsobu, jakým Visual Studio získává místních hodnot pro metodu vyhodnocovací filtr výrazů (EE):  
  
1.  Visual Studio volá stroje ladění (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zobrazíte [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objekt, který reprezentuje všechny vlastnosti rámce zásobníku, včetně oknech místní hodnoty.  
  
2.  `IDebugStackFrame2::GetDebugProperty` volání [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) získat objekt, který popisuje způsob, ve kterém došlo k zarážce. DE dodá poskytovatel symbolů ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adresu ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) a vazač ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` volání [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) pomocí zadané `IDebugAddress` můžete získat [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) představující metodu obsahující zadanou adresu.  
  
4.  `IDebugContainerField` Rozhraní se dotázali [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) rozhraní. Je toto rozhraní, která poskytuje přístup k místní hodnoty metody.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` vytvoří instanci třídy (volá `CFieldProperty` v ukázce), který implementuje `IDebugProperty2` rozhraní pro reprezentaci metody místních hodnot. `IDebugMethodField` Objektu je umístěn v tomto `CFieldProperty` objektů spolu s `IDebugSymbolProvider`, `IDebugAddress` a `IDebugBinder` objekty.  
  
6.  Při `CFieldProperty` objekt je inicializován, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) je volán na `IDebugMethodField` objektu získat [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturu, která obsahuje všechny zobrazitelné informace o metodě, samotný .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Vrátí `CFieldProperty` objektu jako `IDebugProperty2` objektu.  
  
8.  Visual Studio volání [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) na vrácený `IDebugProperty2` objektu s filtrem `guidFilterLocalsPlusArgs`. Tím se vrátí [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objekt, který obsahuje místní hodnoty metody. Tento výčet je vyplněn volání [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio volání [Další](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) získat [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) strukturu pro každý místní. Tato struktura obsahuje ukazatel `IDebugProperty2` rozhraní pro místní.  
  
10. Visual Studio volání [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pro každý místní získat název, hodnotu a typ na místní. Toto je informace, které se zobrazí **místní hodnoty** okna.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Popisuje implementaci [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Vytváření výčtů pro místní hodnoty](../../extensibility/debugger/enumerating-locals.md)  
 Popisuje, jak ladicího stroje (DE) provede volání na výčet lokálních proměnných nebo argumentů.  
  
 [Načtení místních vlastností](../../extensibility/debugger/getting-local-properties.md)  
 Popisuje, jak je DE zavolá se získat název, typ a hodnotu jednoho nebo více místních hodnot.  
  
 [Načtení místních hodnot](../../extensibility/debugger/getting-local-values.md)  
 Tento článek popisuje získání hodnoty místní proměnné, která vyžaduje služby objekt vazače Dal kontext vyhodnocení.  
  
 [Vyhodnocení místních hodnot](../../extensibility/debugger/evaluating-locals.md)  
 Vysvětluje, jak se vyhodnocují místních hodnot.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Poskytuje argumenty předávané při volání DE vyhodnocovací filtr výrazů (EE).  
  
 [Ukázka MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Ukazuje jedním ze způsobů implementace vyhodnocovače výrazů jazyka MyC vytvoření.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)

