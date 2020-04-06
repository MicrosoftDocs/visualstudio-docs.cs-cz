---
title: Implementace vizualizérů typů a vlastních prohlížečů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738510"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementace vizualizérů typů a vlastních prohlížečů
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Zadejte vizualizéry a vlastní prohlížeče umožňují uživateli zobrazit data určitého typu způsobem, který je smysluplnější než jednoduchý šestnáctkový výpis čísel. Vyhodnocení výrazu (EE) může přidružit vlastní prohlížeče ke konkrétním typům dat nebo proměnných. Tyto vlastní prohlížeče jsou implementovány EE. EE může také podporovat vizualizéry externího typu, které mohou pocházet od jiného dodavatele třetí strany nebo dokonce od koncového uživatele.

## <a name="discussion"></a>Diskuse

### <a name="type-visualizers"></a>Typ vizualizéry
 Visual Studio požádá o seznam vizualizérů typu a vlastní prohlížeče pro každý objekt, který má být zobrazen v okně kukátka. Vyhodnocení výrazu (EE) poskytuje takový seznam pro každý typ, pro který chce podporovat vizualizéry typu a vlastní prohlížeče. Volání [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) spustit celý proces přístupu k typu vizualizéry a vlastní prohlížeče (vizualizovat [a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md) pro podrobnosti o pořadí volání).

### <a name="custom-viewers"></a>Vlastní prohlížeče
 Vlastní prohlížeče jsou implementovány v EE pro konkrétní datový typ a jsou reprezentovány rozhraním [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Vlastní prohlížeč není tak flexibilní jako vizualizér typu, protože je k dispozici pouze v případě, že eE, který implementuje tento konkrétní vlastní prohlížeč je spuštěn. Implementace vlastního prohlížeče je jednodušší než implementace podpory pro vizualizéry typů. Podpora vizualizérů typu však poskytuje maximální flexibilitu koncovému uživateli pro vizualizaci dat. Zbývající část této diskuse se týká pouze typ vizualizéry.

## <a name="interfaces"></a>Rozhraní
 EE implementuje následující rozhraní pro podporu vizualizérů typu, které mají být spotřebovány visual studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE spotřebovává následující rozhraní pro podporu vizualizérů typu:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
