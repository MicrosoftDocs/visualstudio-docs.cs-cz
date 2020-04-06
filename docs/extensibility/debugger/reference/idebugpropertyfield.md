---
title: IDebugPropertyField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720694"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Toto rozhraní poskytuje funkce, které umožňují získání a nastavení vlastnosti.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní na stejném objektu, který implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Toto rozhraní je specializace, která podporuje koncept vlastností na třídu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface) získáte toto rozhraní z rozhraní [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) pokud vrátí `FIELD_KIND_PROP`metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraních [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) a [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Získá metodu, která získá vlastnost.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Získá metodu, která nastaví vlastnost.|

## <a name="remarks"></a>Poznámky
 Vlastnost je koncept spravovaného kódu a představuje metodu, která je považována za proměnnou. Vlastnosti neexistují v nespravovaném jazyce C++.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
