---
description: Toto rozhraní je odesláno ladicím modulem (DE) do Správce ladění relace (SDM) po dokončení vyhodnocení asynchronního výrazu.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092199"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Toto rozhraní je odesláno ladicím modulem (DE) do Správce ladění relace (SDM) po dokončení vyhodnocení asynchronního výrazu.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo dokončení vyhodnocení výrazu zahájené voláním [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, aby nahlásil dokončení vyhodnocení výrazu. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojen k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugExpressionEvaluationCompleteEvent2` .

|Metoda|Popis|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Získá původní výraz.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Získá výsledek vyhodnocení výrazu.|

## <a name="remarks"></a>Poznámky
 DE musí odeslat tuto událost, zda bylo vyhodnocení úspěšné nebo ne.

 Pokud vyhodnocení nebylo úspěšné, `DEBUG_PROPINFO_VALUE` příznaky a nebudou `DEBUG_PROPINFO_ATTRIB` nastaveny ve struktuře [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , kterou vrací [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) je vytvořen pomocí příkazu de a vráceného v `IDebugExpressionEvaluationCompleteEvent2` události, pokud selhalo vyhodnocení).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
