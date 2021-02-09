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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83d6a37a5b83cd71123521db70920fd3d454e059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870061"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje objekt Array.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
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
