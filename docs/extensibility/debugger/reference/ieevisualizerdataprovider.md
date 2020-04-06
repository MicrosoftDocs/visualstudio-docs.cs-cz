---
title: IEEVisualizerDataProvider | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718051"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní poskytuje možnost změnit hodnotu objektu prostřednictvím vizualizéru typu.

## <a name="syntax"></a>Syntaxe

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní pro podporu úpravy dat na objekt vlastnosti prostřednictvím vizualizéru typu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se používá při vytváření objektu [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) prostřednictvím volání [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Další podrobnosti najdete v [tématu Vizualizace a zobrazení dat.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable

|Metoda|Popis|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Určuje, zda je možné aktualizovat objekt (a následně jeho hodnotu), kterou představuje tento vizualizér.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Vynutí přehodnocení objektu pro tento vizualizér.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Získá existující objekt pro tento vizualizér (žádné vyhodnocení se provádí).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualizuje objekt pro tento vizualizér, a tím změní hodnotu, kterou vizualizační systém představuje.|

## <a name="remarks"></a>Poznámky
 Visualizer služby (reprezentované rozhraní [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) a vrácené [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) `IEEVisualizerDataProvider` udržuje odkaz na objekt implementující rozhraní. V důsledku toho `IEEVisualizerDataProvider` rozhraní by neměla být implementována na stejný objekt, který implementuje `IEEVisualizerService` [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) pokud tento objekt udržuje odkaz na objekt: cyklický odkaz výsledky a zablokování dojde při zničení objektů. Doporučeným přístupem je `IEEVisualizerDataProvider` implementace na samostatný `IDebugProperty2` objekt, na `IUnknown::AddRef` který objekt deleguje bez volání na něj.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)
