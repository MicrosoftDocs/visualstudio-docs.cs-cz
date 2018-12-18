---
title: IDebugBinder | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3514d280b6718fc670f3bdac35b6bbacbbf2b09c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105093"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  V sadě Visual Studio 2015 se již nepoužívá tímto způsobem implementace vyhodnocovače výrazů. Informace o implementaci vyhodnocovače výrazů CLR, najdete v tématu [vyhodnocovače výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Toto rozhraní váže pole symbolu, obvykle vrácené zprostředkovatelem symbol, kontext paměti nebo objekt, který obsahuje aktuální hodnotu symbolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní podporuje vyhodnocení výrazu a modul ladění (DE), musí být implementována.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní se používá při vyhodnocení výrazu a obvykle se používá při provádění [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugBinder`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Vazby](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Získá kontext paměti nebo objekt, který obsahuje aktuální hodnotu symbolu.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Určuje typ spuštění objektu.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Převede adresu umístění nebo paměti objektu kontextu paměti.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Získá [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objekt použitý k vytvoření parametry funkce.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Získá typ přesný proměnné.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní vrátí objekty, které jsou používány vyhodnocovací filtr výrazů v analyzovat stromy. Vyhodnocení výrazu analyzuje výraz pomocí zprostředkovatele symbol převést symboly ve výrazu instancí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), které popisují každou symbol z hlediska její typ a umístění ve zdrojovém kódu. [Vazby](../../../extensibility/debugger/reference/idebugbinder-bind.md) metoda převede `IDebugField` objekty ke [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) typ objektů, které připojit nebo bind symbol, který má skutečnou hodnotu v paměti. Tyto `IDebugObject` objekty jsou pak uloženy v strom analýzy pro pozdější vyhodnocení.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)