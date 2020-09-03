---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727688"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Toto rozhraní umožňuje vyhodnocovacímu filtru výrazů (EE) volat vlastnosti nebo metody v instancích třídy hodnot (například `System.Decimal` ) a nastavit jejich hodnotu bez volání [vyhodnocování](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) v laděném programu.

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
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
