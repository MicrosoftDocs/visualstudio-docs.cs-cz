---
title: Rozhraní pro vyhodnocení výrazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736943"
---
# <a name="expression-evaluation-interfaces"></a>Rozhraní pro vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Následují rozhraní pro vyhodnocení výrazu [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pro ladicí sdk.

## <a name="discussion"></a>Diskuse
 Tato rozhraní se používají k vyhodnocení výrazů v zásobníku volání během režimu přerušení. Jsou implementovány pouze pro hodnotitelé exprese běžného jazyka run-time (EE).

 Každé rozhraní v tabulce zobrazuje součást, která ji může implementovat z následujícího seznamu:

- Ladicí modul (DE)

- Evaluátor výrazů (EE)

- Visual Studio (VS)

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Představuje číselný alias proměnné.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Představuje číselný alias pro proměnnou a umožňuje vyhodnocení výrazu (EE) získat doménu aplikace pro alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Představuje objekt pole.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Představuje objekt spravovaného pole a umožňuje vyhodnocení výrazu (EE) k určení základního indexu (dolní hranice) pro pole.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Představuje pořadač, který váže ladicí symboly na skutečné adresy v paměti.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Stejné jako rozhraní [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) ale poskytuje přístup k typům, aliasům a vlastním vizualizérům.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Představuje vyhodnocení výrazu.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Představuje vylepšenou verzi vyhodnocení výrazu (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Představuje vyhodnocení výrazu (EE) s rozšířeným stromem analyzátoru.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Představuje funkci.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Představuje funkci a vylepšuje rozhraní [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umožňuje vyhodnocení výrazu (EE) zobrazit zprávu ve výstupním okně ladicího programu.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Představuje objekt spravovaného kódu.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Základní rozhraní, které představuje libovolný symbol vázaný na adresu paměti.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stejné jako rozhraní [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) ale poskytuje přístup k dalším informacím.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Představuje analyzovaný výraz připravený k vyhodnocení.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Představuje ukazatel.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Představuje ukazatel ve stromu analýzy a rozšiřuje rozhraní **IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Poskytuje možnost upravit hodnotu typu prostřednictvím vizualizéru typu.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|sada VS|Poskytuje přístup k vlastním prohlížečům a typem vizualizérů.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|sada VS|Poskytuje možnost vytvořit objekt [IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Představuje kolekci [iDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objekty.|

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Zápis pro vyhodnocovač výrazů modulu CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
