---
title: IEEVisualizerServiceProvider | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717882"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje přístup k metodě, která může vytvořit službu vizualizéru, která se používá ke zpracování úloh vizualizéru typu pro rozhraní IDE.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní k vytvoření visualizer objektu služby,`CLSID`který zase slouží k poskytování id třídy (s) typu vizualizérů do IDE Visual Studio.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Vyhodnocení výrazu (EE) volá [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable

|Metoda|Popis|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Vytvoří službu vizualizéru|

## <a name="remarks"></a>Poznámky
 Rozhraní `IEEVisualizerServiceProvider` je získáno během implementace [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Visualizer služba, která vytvoří toto rozhraní se používá k poskytování funkcí [rozhraní IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) které EE je zodpovědný za implementaci. EE je také zodpovědný za implementaci rozhraní [IEEVisualizerDataProvider,](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) který umožňuje typ vizualizéry zobrazit a upravit hodnotu vlastnosti.

 Podrobnosti o interakci těchto rozhraní najdete v tématu [Vizualizace a zobrazení dat.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)
