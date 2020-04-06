---
title: IEEVisualizerService | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717938"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní implementuje klíčové metody, které poskytují funkce [rozhraníIDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) a [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní povolit vyhodnocení výrazu (EE) pro podporu vizualizérů typu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 EE volá [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) získat toto rozhraní jako součást jeho podporu pro vizualizéry typu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable

|Metoda|Popis|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Načte počet vlastních prohlížečů, o kterých tato služba ví.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Načte seznam vlastních prohlížečů.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Vrátí objekt proxy pro vlastnost.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Načte počet řetězců hodnot, které se mají zobrazit pro zadanou vlastnost nebo pole.|

## <a name="remarks"></a>Poznámky
 IDE používá rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) k určení, pokud existují žádné vlastní prohlížeče nebo typ vizualizéry pro vlastnost. Vytvořením visualizer služby (s [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), EE můžete `IDebugProperty3` dodávat funkce a [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (který podporuje prohlížení a změnu hodnoty vlastnosti) rozhraní a tím podporují typ vizualizéry.

 Pokud EE má vlastní prohlížeče, které sám implementuje, EE můžete připojit `CLSID`s těchto vlastních prohlížečů na konec seznamu vrácené [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). To umožňuje EE pro podporu obou typů vizualizérů a vlastní prohlížeče. Jen se ujistěte, že [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odráží přidání všech vlastních diváků.

 [Vizualizér typu a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pro diskusi o rozdílu mezi vizualizéry a diváky.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
