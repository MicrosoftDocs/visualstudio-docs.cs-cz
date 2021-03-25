---
description: Toto rozhraní představuje objekt, který vytvoří pořadač k zapouzdření hodnot symbolů a výrazů.
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18355c5b21f8df0fde5faa31caf8d64fb8f3f3fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054163"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt, který vytvoří pořadač k zapouzdření hodnot symbolů a výrazů.

## <a name="syntax"></a>Syntax

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní pro reprezentaci objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je základní třídou pro všechny objekty, které vyhodnocovací filtr výrazů používá v analyzovaných výrazech. Je vrácen voláním metody [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) . [QueryInterface](/cpp/atl/queryinterface) získá více specializovaných rozhraní z tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugObject` .

|Metoda|Popis|
|------------|-----------------|
|[GetSize –](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Získá velikost objektu.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Získá hodnotu objektu jako po sobě jdoucí řady bajtů.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Nastaví hodnotu objektu z po sobě jdoucí řady bajtů.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Nastaví referenční hodnotu tohoto objektu.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Získá kontext paměti, který představuje adresu hodnoty objektu.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Vytvoří kopii spravovaného objektu v adresním prostoru ladicího stroje.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testuje, zda je tento objekt odkaz s hodnotou null.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porovná objekt s tímto objektem.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Určuje, zda je tento objekt určen jen pro čtení.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Určuje, zda je objekt transparentním proxy serverem.|

## <a name="remarks"></a>Poznámky
 Vyhodnocovací filtr výrazů používá toto rozhraní jako základní třídu pro reprezentaci objektů ve stromu analýz.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Zapisovat](../../../extensibility/debugger/reference/idebugbinder-bind.md)
