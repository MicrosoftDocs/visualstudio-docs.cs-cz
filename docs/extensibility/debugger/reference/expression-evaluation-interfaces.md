---
title: Rozhraní vyhodnocení výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be9582f965fe1d8a00c97548dbc5f458ae4e1198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107397"
---
# <a name="expression-evaluation-interfaces"></a>Rozhraní vyhodnocení výrazu
> [!IMPORTANT]
>  V sadě Visual Studio 2015 se již nepoužívá tímto způsobem implementace vyhodnocovače výrazů. Informace o implementaci vyhodnocovače výrazů CLR, najdete v tématu [vyhodnocovače výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Toto jsou rozhraní vyhodnocení výrazu pro [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladění SDK.  
  
## <a name="discussion"></a>Diskusní  
 Tato rozhraní se používají k vyhodnocení výrazů v zásobníku volání při režimu pozastavení. Implementují se pouze pro běžné jazyk vyhodnocovače výrazů runtime (EE).  
  
 Každé rozhraní v tabulce znázorňuje komponenty, která můžete implementovat z následujícího seznamu:  
  
-   Ladění modulu (DE)  
  
-   Vyhodnocovací filtr výrazů (EE)  
  
-   Visual Studio (VS)  
  
|Rozhraní|Implementované|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Představuje alias číselné proměnné.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Představuje alias číselné proměnné a umožňuje (EE) k získání doménu aplikace pro alias vyhodnocovací filtr výrazů.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Představuje objekt array.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Představuje objekt spravované pole a umožňuje (EE) k určení základní indexu (dolní meze) pro pole vyhodnocovací filtr výrazů.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|NĚMECKO|Představuje vazač, vazby ladění symbolů skutečné adresy v paměti.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|NĚMECKO|Stejné jako [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) rozhraní ale poskytuje přístup k vlastní vizualizérech, typy a aliasy.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Představuje vyhodnocovací filtr výrazů.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Představuje rozšířenou verzi (EE) vyhodnocovací filtr výrazů.|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Představuje (EE) vyhodnocovací filtr výrazů s strom rozšířené analyzátor.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Představuje funkci.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Představuje funkci a zlepšuje [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraní.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|NĚMECKO|Umožňuje vyhodnocení výrazu (EE) k zobrazení zprávy v okně výstupu ladicího programu.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Představuje objekt spravovaného kódu.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Základní rozhraní, který reprezentuje všechny symbol vázán na adresu paměti.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stejné jako [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) rozhraní ale poskytuje přístup k dalším informacím.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Představuje výraz analyzovaný připravené k vyhodnocení.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Představuje ukazatel.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Představuje ukazatel v strom analýzy a rozšiřuje **IDebugPointerObject** rozhraní.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Umožňuje změnit hodnotu typ prostřednictvím vizualizéru typu.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|sada VS|Poskytuje přístup k vlastní prohlížečů a vizualizérech typu.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|sada VS|Poskytuje možnost vytvářet [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objektu.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Představuje kolekci [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace rozhraní API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Zápis vyhodnocovací filtr výrazů CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)