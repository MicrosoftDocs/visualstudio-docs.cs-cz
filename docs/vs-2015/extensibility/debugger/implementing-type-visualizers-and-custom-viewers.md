---
title: Implementace Vizualizérů typů a vlastních prohlížečů | Dokumentace Microsoftu
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
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11d047904e932646eedc974a50590dbe0a9ea99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791277"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementace vizualizérů typů a vlastních prohlížečů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Vizualizérů typů a vlastních prohlížečů umožňuje uživateli zobrazit data určitého typu tak, aby lépe vystihuje než jednoduché výpis šestnáctkových čísel. Vyhodnocovače výrazů (EE) můžete přidružit konkrétní typy dat nebo proměnné vlastních prohlížečů. Tyto vlastní prohlížeče jsou implementované EE. EE může také podporovat vizualizátory, externí typ, které může pocházet z jiného dodavatele třetích stran nebo dokonce koncového uživatele.  
  
## <a name="discussion"></a>Diskuse  
  
### <a name="type-visualizers"></a>Vizualizérů typů  
 Visual Studio vyzve k zadání seznam vizualizérů typů a vlastních prohlížečů pro každý objekt, který se má zobrazit v okně kukátko. Vyhodnocovače výrazů (EE) poskytuje seznam, pro každý typ, pro kterou chce podporovat vizualizérů typů a vlastních prohlížečů. Volání [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) spustit celý proces přístup k vizualizérů typů a vlastních prohlížečů (viz [Visualizing a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)podrobnosti o volací sekvence).  
  
### <a name="custom-viewers"></a>Vlastních prohlížečů  
 Vlastních prohlížečů jsou implementovány v EE pro konkrétní datový typ a jsou reprezentovány [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) rozhraní. Vlastní prohlížeč není tak účinná jako typ vizualizéru, protože je k dispozici pouze při provádění EE, který implementuje tuto konkrétní vlastní prohlížeč. Implementace vlastní prohlížeč je jednodušší než implementace vizualizérů typů podporu. Ale podporuje vizualizérů typů poskytuje maximální flexibilitu pro koncového uživatele pro vizualizaci dat nebo její. Zbytek této diskuse se týká pouze vizualizérů typů.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Zápis vyhodnocovací filtr výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

