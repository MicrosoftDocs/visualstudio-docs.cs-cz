---
title: IDebugArrayObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736211"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt pole.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní představují pole.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) může získat toto rozhraní pomocí [QueryInterface,](/cpp/atl/queryinterface) pokud objekt představuje pole.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod na `IDebugObject` rozhraní jsou implementovány následující metody `IDebugArrayObject` na rozhraní.

|Metoda|Popis|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Získá počet prvků v poli.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Získá prvek pole.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Získá všechny prvky pole.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Získá pořadí pole.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Získá dimenze pole.|

## <a name="remarks"></a>Poznámky
 Vyhodnocení výrazu používá toto rozhraní k reprezentaci polí ve stromu analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
