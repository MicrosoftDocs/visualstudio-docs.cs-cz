---
description: Toto rozhraní umožňuje vyhodnocovacímu filtru výrazů (EE) volat vlastnosti nebo metody v instancích hodnotové třídy (například System. Decimal) a nastavit jejich hodnotu bez volání vyhodnocování v laděném programu.
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88eadb33aaccc09a7c4667ad01d9acee538169f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076859"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní umožňuje vyhodnocovacímu filtru výrazů (EE) volat vlastnosti nebo metody v instancích třídy hodnot (například `System.Decimal` ) a nastavit jejich hodnotu bez volání [vyhodnocování](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) v laděném programu.

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocovací filtr výrazů implementuje toto rozhraní, které představuje objekt spravovaného kódu, jako je například proměnná.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Chcete-li získat toto rozhraní, zavolejte [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , který představuje instanci hodnotové třídy.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `IDebugManagedObject` rozhraní zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Vrátí rozhraní, které představuje objekt spravovaného kódu a ze kterého lze získat libovolné příslušné rozhraní spravovaného kódu.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Nastaví hodnotu tohoto objektu na hodnotu zadaného objektu spravovaného kódu.|

## <a name="remarks"></a>Poznámky
 Vyhodnocovací filtr výrazů používá toto rozhraní k uložení objektu spravovaného kódu ve stromové struktuře analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní pro vyhodnocení výrazu](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Vyhodnotit](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
