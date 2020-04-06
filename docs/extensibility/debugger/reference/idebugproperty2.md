---
title: IDebugProperty2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721223"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Toto rozhraní představuje vlastnost rámce zásobníku, vlastnost dokumentu programu nebo jinou vlastnost. Vlastnost je obvykle výsledkem vyhodnocení výrazu.

> [!NOTE]
> Toto použití "vlastnost" by neměla být zaměňována `IDebugProperty2` s tím smyslu členské proměnné třídy, i když může představovat takovou entitu.

## <a name="syntax"></a>Syntaxe

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní představují určitý druh hodnoty. Hodnota může být například číselná hodnota v důsledku vyhodnocení výrazu, kontext paměti používaný pro zobrazení paměti nebo seznam registrů a jejich hodnot.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) nebo [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) získat toto rozhraní, které představuje výsledek hodnocení. `IDebugExpression2::EvaluateAsync`vrátí toto rozhraní odesláním rozhraní [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do sdm, což zase volá [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) k načtení vlastnosti.

- [Funkce GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) vrátí toto rozhraní, aby poskytla přidružený dokument skriptu.

- [Funkce GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) vrátí toto rozhraní jako návratovou hodnotu funkce.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) vrátí toto rozhraní představují různé vlastnosti programu, jako je například název nebo kontext paměti.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) vrátí toto rozhraní představují různé vlastnosti rámce zásobníku, jako jsou například místní proměnné.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProperty2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Vyplní [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strukturu, která popisuje vlastnost.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Nastaví hodnotu vlastnosti z řetězce.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Nastaví hodnotu vlastnosti z hodnoty daného odkazu.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Vyjmenovává děti z nemovitosti.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Vrátí nadřazenou vlastnost.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Vrátí vlastnost, která popisuje nejvíce odvozené vlastnosti vlastnosti.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Vrátí bajty paměti, které tvoří hodnotu vlastnosti.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Vrátí kontext paměti pro hodnotu vlastnosti.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Vrátí velikost hodnoty vlastnosti v bajtech.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Vrátí odkaz na hodnotu této vlastnosti.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Vrátí rozšířené informace o vlastnosti.|

## <a name="remarks"></a>Poznámky
 Vlastnost, jak je `IDebugProperty2` reprezentovánrozhraní, lze si myslet jako hodnotu s názvem, typ a adresu. Obecněji řečeno, `IDebugProperty2` může představovat cokoli, co má hierarchickou strukturu, s rodiči a podřízenými uzly.

 Vlastnost je obvykle přechodné, trvající pouze tak dlouho, jak aktuální rámec zásobníku, například. Na druhé straně odkaz, jak je reprezentován rozhraní [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) trvá tak dlouho, dokud hodnota zůstane v paměti.

 Rozhraní IDE můžete `IDebugProperty2` použít rozhraní, aby uživatelé procházet a upravovat vlastnosti za běhu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
