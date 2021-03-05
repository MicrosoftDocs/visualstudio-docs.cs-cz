---
description: Toto rozhraní poskytuje funkce, které umožňují získat a nastavit vlastnost.
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 097d73485773052afa1e9852293211084a225099
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167903"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Toto rozhraní poskytuje funkce, které umožňují získat a nastavit vlastnost.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní u stejného objektu, který implementuje rozhraní [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Toto rozhraní je specializace, která podporuje koncept vlastností třídy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Použijte [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z rozhraní [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , pokud se vrátí metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v rozhraních [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) a [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Získá metodu, která získá vlastnost.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Získá metodu, která nastaví vlastnost.|

## <a name="remarks"></a>Poznámky
 Vlastnost je koncept spravovaného kódu a představuje metodu, která je považována za proměnnou. Vlastnosti neexistují v nespravovaném jazyce C++.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
