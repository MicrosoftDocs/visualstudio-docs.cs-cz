---
description: Toto rozhraní poskytuje přístup k metodě, která může vytvořit službu Vizualizátoru, která se používá ke zpracování úkolů Vizualizér typů pro rozhraní IDE.
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 973135865b0b1c460f4c9000036f2af04a9ae3ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086687"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje přístup k metodě, která může vytvořit službu Vizualizátoru, která se používá ke zpracování úkolů Vizualizér typů pro rozhraní IDE.

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio implementuje toto rozhraní pro vytvoření objektu služby Vizualizátoru, který se zase používá k poskytnutí ID třídy pro `CLSID` typy vizualizací do integrovaného vývojového prostředí (IDE) sady Visual Studio.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Vyhodnocení výrazu (EE) volá [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) k získání tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable

|Metoda|Popis|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Vytvoří službu Vizualizátor.|

## <a name="remarks"></a>Poznámky
 `IEEVisualizerServiceProvider`Rozhraní se získá během implementace [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Služba vizualizér, kterou toto rozhraní vytvoří, slouží k poskytování funkcí rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , které je pro implementaci k za implementaci. EE je také zodpovědná za implementaci rozhraní [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , které umožňuje vizualizaci typů zobrazit a upravit hodnotu vlastnosti.

 Podrobnosti o interakci těchto rozhraní najdete v tématu [vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)
