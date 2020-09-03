---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718051"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje možnost změnit hodnotu objektu prostřednictvím Vizualizér typu.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní pro podporu úprav dat u objektu vlastnosti pomocí Vizualizér typů.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se používá při vytváření objektu [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) prostřednictvím volání [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Další podrobnosti najdete v tématu [vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable

|Metoda|Popis|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Určuje, zda je možné aktualizovat objekt (a následně jeho hodnotu), kterou tento Vizualizér představuje.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Vynutí opětovné vyhodnocení objektu pro tento Vizualizér.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Získá existující objekt pro tento Vizualizér (žádné vyhodnocení se nedokončilo).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualizuje objekt pro tento vizualizér, čímž se změní hodnota, kterou Vizualizér prezentuje.|

## <a name="remarks"></a>Poznámky
 Služba Vizualizér (reprezentovaná rozhraním [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) a vrácená [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) udržuje odkaz na objekt implementující `IEEVisualizerDataProvider` rozhraní. V důsledku toho `IEEVisualizerDataProvider` by rozhraní nemělo být implementováno na stejný objekt, který implementuje rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , pokud tento objekt udržuje odkaz na `IEEVisualizerService` objekt: cyklický odkaz výsledky a zablokování dojde při zničení objektů. Doporučený postup je implementovat `IEEVisualizerDataProvider` na samostatný objekt, ke kterému se `IDebugProperty2` objekt deleguje bez volání `IUnknown::AddRef` .

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)
