---
title: Rozhraní pro vyhodnocení výrazu | Dokumentace Microsoftu
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
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c7365e17749d69d0dc36e06c3d11d053a44e94d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774832"
---
# <a name="expression-evaluation-interfaces"></a>Rozhraní pro vyhodnocení výrazu
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Následují rozhraní pro vyhodnocení výrazu pro [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladění sady SDK.  
  
## <a name="discussion"></a>Diskuse  
 Tato rozhraní se používají k vyhodnocení výrazů v zásobníku volání během režimu pozastavení. Tyto jsou implementované jenom pro běžné language vyhodnocovače výrazů za běhu (EE).  
  
 Každé rozhraní v tabulce ukazuje komponenta, která můžete implementovat z následujícího seznamu:  
  
-   Ladicí stroj (DE)  
  
-   Chyba při vyhodnocování výrazu (EE)  
  
-   Visual Studio (VS)  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Představuje číselná aliasu pro proměnnou.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Představuje číselná aliasu pro proměnnou a umožňuje vyhodnocovače výrazů (EE) k získání aliasu domény aplikace.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Představuje objekt typu pole.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Představuje objekt spravovaného pole a umožňuje vyhodnocovače výrazů (EE) k určení základní indexu (dolní meze) pro pole.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Představuje vazač, vytvoří vazbu ladění symboly pro skutečné adresy v paměti.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Stejné jako [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) rozhraní ale poskytuje přístup pro typy, aliasy a vlastních vizualizérů.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Představuje vyhodnocovací filtr výrazů.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Představuje rozšířenou verzi vyhodnocovače výrazů (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Představuje vyhodnocovače výrazů (EE) s strom rozšířené analyzátor.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Představuje funkci.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Představuje funkci a zvyšuje [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraní.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umožňuje vyhodnocovače výrazů (EE) pro zobrazení zprávy v okně výstupu ladicího programu.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Představuje objekt spravovaný kód.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Základní rozhraní, který představuje jakýkoli symbol vázán na adresu paměti.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stejné jako [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) rozhraní, ale poskytuje přístup k dalším informacím.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Představuje analyzovaný připravený, který se má vyhodnotit výraz.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Představuje ukazatel.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Představuje ukazatel v strom analýzy a rozšiřuje **IDebugPointerObject** rozhraní.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Umožňuje změnit hodnotu typ prostřednictvím vizualizér typů.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|sada VS|Poskytuje přístup k vlastních prohlížečů a vizualizérů typů.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|sada VS|Poskytuje možnost vytvářet [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objektu.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Představuje kolekci [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty.|  
  
## <a name="see-also"></a>Viz také  
 [Reference k rozhraní API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

