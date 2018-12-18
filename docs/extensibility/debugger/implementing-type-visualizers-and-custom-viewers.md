---
title: Implementace Vizualizérů typů a vlastních prohlížečů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fab6cba691a835c2213e5303c1be2419a79c18e9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927239"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementace vizualizérů typů a vlastních prohlížečů
> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka Chyba při vyhodnocování výrazu spravované](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample). 
  
 Vizualizérů typů a vlastních prohlížečů může uživatel zobrazit data určitého typu tak, aby lépe vystihuje než jednoduché výpis šestnáctkových čísel. Vyhodnocovače výrazů (EE) můžete přidružit konkrétní typy dat nebo proměnné vlastních prohlížečů. Tyto vlastní prohlížeče jsou implementované EE. EE může také podporovat vizualizátory, externí typ, které může pocházet z jiného dodavatele třetích stran nebo dokonce koncového uživatele.  
  
## <a name="discussion"></a>Diskuse  
  
### <a name="type-visualizers"></a>Vizualizérů typů  
 Visual Studio vyzve k zadání seznam vizualizérů typů a vlastních prohlížečů pro každý objekt, který se má zobrazit v okně kukátko. Vyhodnocovače výrazů (EE) poskytuje seznam, pro každý typ, pro kterou chce podporovat vizualizérů typů a vlastních prohlížečů. Volání [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) spustit celý proces přístup k vizualizérů typů a vlastních prohlížečů (viz [Visualizing a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)podrobnosti o volací sekvence).  
  
### <a name="custom-viewers"></a>Vlastních prohlížečů  
 Vlastních prohlížečů jsou implementovány v EE pro konkrétní datový typ a jsou reprezentovány [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) rozhraní. Vlastní prohlížeč není tak účinná jako typ vizualizéru, protože je k dispozici pouze při provádění EE, který implementuje tuto konkrétní vlastní prohlížeč. Implementace vlastní prohlížeč je jednodušší než implementace vizualizérů typů podporu. Však podporuje vizualizérů typů poskytuje maximální flexibilitu pro koncového uživatele pro vizualizaci svá data. Zbytek této diskuse se týká pouze vizualizérů typů.  
  
## <a name="interfaces"></a>Rozhraní  
 EE implementuje následující rozhraní pro podporu vizualizérů typu, který se má používat Visual Studio:  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  EE spotřebovává následující rozhraní pro podporu vizualizérů typů:  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Viz také:  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)