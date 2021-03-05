---
description: Níže jsou uvedené rozhraní pro vyhodnocení výrazu pro sadu SDK pro ladění sady Visual Studio.
title: Rozhraní pro vyhodnocení výrazu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d380fcce087fad3dc6b101e78cbc514ba19b1052
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158732"
---
# <a name="expression-evaluation-interfaces"></a>Rozhraní pro vyhodnocení výrazu
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Níže jsou uvedené rozhraní pro vyhodnocení výrazu pro [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sadu SDK pro ladění.

## <a name="discussion"></a>Diskuse
 Tato rozhraní se používají k vyhodnocení výrazů v zásobníku volání během režimu přerušení. Jsou implementované pouze v případě, že jsou vyhodnocovací filtry výrazů za běhu běžného jazyka (EE).

 Každé rozhraní v tabulce zobrazuje komponentu, která ji může implementovat z následujícího seznamu:

- Ladicí stroj (DE)

- Vyhodnocení výrazu (EE)

- Visual Studio (VS)

|Rozhraní|Implementuje|Popis|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Představuje numerický alias pro proměnnou.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Představuje numerický alias pro proměnnou a umožňuje vyhodnocovacímu filtru výrazů (EE) získat doménu aplikace pro daný alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Představuje objekt Array.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Představuje objekt spravovaného pole a umožňuje vyhodnocovacímu filtru výrazů (EE) určit základní index (dolní meze) pro pole.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Představuje pořadač, který váže symboly ladění na skutečné adresy v paměti.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Stejné jako rozhraní [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , ale poskytuje přístup k typům, aliasům a vlastním vizualizacím.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Představuje vyhodnocovací filtr výrazů.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Představuje rozšířenou verzi vyhodnocovacího filtru výrazů (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Představuje vyhodnocovací filtr výrazů (EE) pomocí rozšířeného stromu analyzátoru.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Představuje funkci.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Představuje funkci a vylepšuje rozhraní [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umožňuje vyhodnocovacímu filtru výrazů (EE) zobrazit zprávu v okně výstupu ladicího programu.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Představuje objekt spravovaného kódu.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Základní rozhraní, které představuje libovolný symbol vázaný na adresu paměti.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Stejné jako rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , ale poskytuje přístup k dalším informacím.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Představuje analyzovaný výraz připravený k vyhodnocení.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Představuje ukazatel.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Představuje ukazatel ve stromové struktuře analýzy a rozšiřuje rozhraní **IDebugPointerObject** .|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Poskytuje možnost Upravit hodnotu typu prostřednictvím Vizualizér typu.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|sada VS|Poskytuje přístup k vlastním divákům a typům vizualizují.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|sada VS|Poskytuje možnost vytvořit objekt [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Představuje kolekci objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Zápis pro vyhodnocovač výrazů modulu CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
