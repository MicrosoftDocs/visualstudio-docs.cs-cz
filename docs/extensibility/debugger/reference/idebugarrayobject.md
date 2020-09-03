---
title: IDebugArrayObject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736211"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt Array.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní, aby představovalo pole.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) může toto rozhraní získat pomocí [QueryInterface](/cpp/atl/queryinterface) , pokud objekt představuje pole.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v `IDebugObject` rozhraní jsou na rozhraní implementovány následující metody `IDebugArrayObject` .

|Metoda|Popis|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Získá počet prvků v poli.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Získá prvek pole.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Načte všechny prvky pole.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Získá rozměr pole.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Získá rozměry pole.|

## <a name="remarks"></a>Poznámky
 Vyhodnocovací filtr výrazů používá toto rozhraní k reprezentaci polí ve stromové struktuře analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
