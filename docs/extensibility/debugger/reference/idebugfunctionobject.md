---
title: IDebugFunctionObject | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728500"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní představuje funkci.

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu implementuje toto rozhraní představují funkci.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je specializace rozhraní [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) a je `IDebugObject` získánpomocí [QueryInterface](/cpp/atl/queryinterface) na rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)rozhraní `IDebugFunctionObject` zveřejňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Vytvoří primitivní datový objekt.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Vytvoří objekt pomocí konstruktoru.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Vytvoří objekt bez konstruktoru.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Vytvoří objekt pole.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Vytvoří objekt řetězce.|
|[Vyhodnotit](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Volá funkci a vrátí výslednou hodnotu jako objekt.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní umožňuje vyhodnocení výrazu představují funkce ve stromu analýzy. Metody `Create` v tomto rozhraní se používají k vytvoření objektů představujících vstupní parametry metody. Funkce pak může být spuštěna voláním metody [Evaluate,](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) která vrací objekt představující vrácenou hodnotu funkce.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
