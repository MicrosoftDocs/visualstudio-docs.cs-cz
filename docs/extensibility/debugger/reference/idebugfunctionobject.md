---
description: Toto rozhraní představuje funkci.
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e9a579212a34a10fc9999867d88dfbd277a9c3fe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150585"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje funkci.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní pro reprezentaci funkce.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je specializací rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) a je získáno pomocí [QueryInterface](/cpp/atl/queryinterface) na `IDebugObject` rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `IDebugFunctionObject` rozhraní zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Vytvoří primitivní datový objekt.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Vytvoří objekt pomocí konstruktoru.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Vytvoří objekt bez konstruktoru.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Vytvoří objekt Array.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Vytvoří objekt String.|
|[Vyhodnotit](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Volá funkci a vrátí výslednou hodnotu jako objekt.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní umožňuje, aby vyhodnocovací filtr výrazů představoval funkce ve stromu analýz. `Create`Metody v tomto rozhraní slouží k vytvoření objektů představujících vstupní parametry metody. Funkci lze následně spustit voláním metody [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) , která vrací objekt reprezentující vrácenou hodnotu funkce.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
