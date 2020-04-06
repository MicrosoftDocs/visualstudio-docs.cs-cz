---
title: Atribut IDebugCustomAttribute | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732680"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Toto rozhraní představuje vlastní atribut a může poskytnout název, nadřazený a typ třídy atributu.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní za účelem podpory vlastních atributů přidružených ke symbolu. Obvykle je implementována na vlastní objekt.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) vrátí toto rozhraní. Volání metody [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) vrátí rozhraní [IEnumDebugCustomAttributes.](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugCustomAttribute`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Získá pole, ke kterému je připojen aktuální atribut.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Získá typ třídy vlastní atribut.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Získá název vlastní atribut.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Získá informace o atributu jako objekt blob bajtů.|

## <a name="remarks"></a>Poznámky
 Vlastní atribut je struktura pro C#, která poskytuje vlastní metadata přidružená k určité třídě nebo metodě.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
