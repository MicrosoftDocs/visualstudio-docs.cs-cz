---
title: Ukázková implementace místních hodnot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e943fd7ba27fe21029bab4d818803186147476e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704892"
---
# <a name="sample-implementation-of-locals"></a>Ukázková implementace místních hodnot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Tady je přehled toho, jak Visual Studio získá národní prostředí pro metodu z vyhodnocovacího filtru výrazů (EE):  
  
1. Sada Visual Studio volá [GetDebugProperty –](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) modul ladění (de), aby získala objekt [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , který představuje všechny vlastnosti rámce zásobníku, včetně místních hodnot.  
  
2. `IDebugStackFrame2::GetDebugProperty` volá [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) k získání objektu, který popisuje metodu, ve které došlo k zarážce. DE dodá poskytovatele symbolů ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adresu ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) a Binder ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` volá [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) se zadaným `IDebugAddress` objektem pro získání [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujícího metodu obsahující zadanou adresu.  
  
4. `IDebugContainerField`Pro rozhraní [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) se dotazuje na rozhraní. Je toto rozhraní, které poskytuje přístup k lokálním hodnotám metody.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` Vytvoří instanci třídy (volanou `CFieldProperty` v ukázce), která implementuje `IDebugProperty2` rozhraní pro reprezentaci místních hodnot metody. `IDebugMethodField`Objekt je umístěn v tomto `CFieldProperty` objektu společně s `IDebugSymbolProvider` `IDebugAddress` `IDebugBinder` objekty a.  
  
6. Když `CFieldProperty` je objekt inicializován, je volána metoda [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) na objektu, která `IDebugMethodField` získá [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturu, která obsahuje všechny informace o samotné metodě.  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Vrátí `CFieldProperty` objekt jako `IDebugProperty2` objekt.  
  
8. Visual Studio volá [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) u vráceného `IDebugProperty2` objektu pomocí filtru `guidFilterLocalsPlusArgs` . Tím se vrátí objekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující místní metody. Tento výčet je vyplněn voláními [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Po [volání sady](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) Visual Studio k získání [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury pro každé místní prostředí. Tato struktura obsahuje ukazatel na `IDebugProperty2` rozhraní pro místní.  
  
10. Visual Studio volá metodu [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pro každý místní, aby získala název, hodnotu a typ místní proměnné. Toto jsou informace, které se zobrazují v okně **místních** hodnot.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Implementace GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Popisuje implementaci [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Vytváření výčtů pro místní hodnoty](../../extensibility/debugger/enumerating-locals.md)  
 Popisuje, jak ladicí stroj (DE) provede volání výčtu místních proměnných nebo argumentů.  
  
 [Načtení místních vlastností](../../extensibility/debugger/getting-local-properties.md)  
 Popisuje, jak příkaz DE provede volání, aby získal název, typ a hodnotu jedné nebo více lokálních hodnot.  
  
 [Načtení místních hodnot](../../extensibility/debugger/getting-local-values.md)  
 Tento článek popisuje získání hodnoty místního, která vyžaduje služby objektu pořadače uvedené v kontextu vyhodnocení.  
  
 [Vyhodnocení místních hodnot](../../extensibility/debugger/evaluating-locals.md)  
 Vysvětluje, jak se vyhodnocují místní hodnoty.  
  
## <a name="related-sections"></a>Související oddíly  
 [Kontext vyhodnocení](../../extensibility/debugger/evaluation-context.md)  
 Poskytuje argumenty, které jsou předány, když DE volá vyhodnocovací filtr výrazů (EE).  
  
 [Ukázka MyCEE](https://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Ukazuje jeden implementační postup pro vytvoření vyhodnocovacího filtru výrazů pro jazyk MyC.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení místních hodnot](../../extensibility/debugger/displaying-locals.md)
