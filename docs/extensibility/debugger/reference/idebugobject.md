---
title: IDebugObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726309"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt, který vytvoří pořadač zapouzdřit hodnoty symbolů a výrazů.

## <a name="syntax"></a>Syntaxe

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní představují objekt.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je základní třída pro všechny objekty, které vyhodnocení výrazu používá v analyzované výrazy. Je vrácena [voláníbind](../../../extensibility/debugger/reference/idebugbinder-bind.md) metody. [QueryInterface](/cpp/atl/queryinterface) získá specializovanější rozhraní z tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugObject`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Získá velikost objektu.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Získá hodnotu objektu jako po sobě jdoucí řady bajtů.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Nastaví hodnotu objektu z po sobě jdoucích řad bajtů.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Nastaví referenční hodnotu tohoto objektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Získá kontext paměti, který představuje adresu hodnoty objektu.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Vytvoří kopii spravovaného objektu v adresním prostoru ladicího modulu.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testuje, zda tento objekt je nulový odkaz.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porovná objekt s tímto.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Určuje, zda je tento objekt jen pro čtení.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Určuje, zda je objekt transparentní proxy server.|

## <a name="remarks"></a>Poznámky
 Vyhodnocení výrazu používá toto rozhraní jako základní třídu k reprezentaci objektů ve stromu analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Vytvořit vazbu](../../../extensibility/debugger/reference/idebugbinder-bind.md)
