---
title: IDebugDynamicField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731316"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Toto rozhraní představuje typ proměnné.

## <a name="syntax"></a>Syntaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno zprostředkovateli symbolů jako základní třída pro libovolný typ, který lze určit za běhu. Toto je pouze pro spravovaný kód.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní představuje základní třídu, ze které lze odvodit více specializovaných rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Toto rozhraní neposkytuje žádné jiné metody `IDebugField`než ty, které jsou zděděny z aplikace .

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
