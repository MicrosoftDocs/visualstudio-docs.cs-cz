---
title: Implementace typů vizualizace a vlastních prohlížečů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b780f2115400fd43e8915a5109c960cab99bf131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835563"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementace vizualizérů typů a vlastních prohlížečů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Typy vizualizací a vlastní čtenáři umožňují uživateli zobrazit data konkrétního typu způsobem, který je smysluplnější než jednoduchý hexadecimální výpis čísel. Vyhodnocovací filtr výrazů (EE) může přidružit vlastní diváky k určitým typům dat nebo proměnných. Tyto vlastní prohlížeče jsou implementovány v EE. EE může podporovat také externí typy vizualizací, které mohou pocházet od jiného dodavatele třetí strany nebo i od koncového uživatele.  
  
## <a name="discussion"></a>Diskuse  
  
### <a name="type-visualizers"></a>Typy vizualizací  
 Visual Studio si vyžádá seznam typů vizualizací a vlastní čtenáři pro všechny objekty, které se mají zobrazit v okně kukátka. Vyhodnocovací filtr výrazů (EE) poskytuje takový seznam pro každý typ, pro který chce podporovat typy vizualizací a vlastní prohlížeče. Volání [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) a [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) zahájí celý proces přístupu k typům vizualizují a vlastním divákům (Další informace o volající sekvenci naleznete v tématu [vizualizace a zobrazení dat](../../extensibility/debugger/visualizing-and-viewing-data.md) ).  
  
### <a name="custom-viewers"></a>Vlastní čtenáři  
 Vlastní prohlížeče jsou implementovány v EE pro určitý datový typ a jsou reprezentovány rozhraním [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Vlastní prohlížeč není tak flexibilní jako Vizualizér typu, protože je k dispozici pouze v případě, že je k dispozici pouze v případě, že je prováděna aplikace, která implementuje konkrétní vlastní prohlížeč. Implementace vlastního prohlížeče je jednodušší než implementace podpory pro vizualizace typů. Nicméně podporuje vizualizace typu, které koncovým uživatelům umožní vizualizovat jeho data, aby mohl získat maximální flexibilitu. Zbývající část této diskuze se týká jenom vizualizací typu.  
  
## <a name="interfaces"></a>Rozhraní  
 EE implementuje následující rozhraní pro podporu typů vizualizací, které mají být spotřebovány v aplikaci Visual Studio:  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  V EE se spotřebovávají následující rozhraní pro podporu typů vizualizací:  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Viz také  
 [Zápis vyhodnocovacího filtru výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Vizualizace a zobrazování dat](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
