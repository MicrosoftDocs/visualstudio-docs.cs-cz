---
description: Toto rozhraní představuje vlastní atribut a může poskytovat název, nadřazený typ a třídu atributu.
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b96f4330371e8fb18b75a6ad6f17d61cccd3812
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095430"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Toto rozhraní představuje vlastní atribut a může poskytovat název, nadřazený typ a třídu atributu.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní, aby podporoval vlastní atributy přidružené k symbolu. Obvykle se implementuje na svém vlastním objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) vrátí toto rozhraní. Volání metody [EnumCustomAttributes –](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) vrátí rozhraní [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugCustomAttribute` .

|Metoda|Popis|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Získá pole, ke kterému je přiřazen aktuální atribut.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Získá typ třídy vlastního atributu.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Získá název vlastního atributu.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Získá informace o atributu jako objekt BLOB bajtů.|

## <a name="remarks"></a>Poznámky
 Vlastní atribut je struktura pro jazyk C#, která poskytuje vlastní metadata přidružená ke konkrétní třídě nebo metodě.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
