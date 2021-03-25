---
description: Toto rozhraní představuje typ proměnné.
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf1d72bfa38e6af0419e696b267699d10340cc68
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094078"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Toto rozhraní představuje typ proměnné.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno poskytovateli symbolů jako základní třídou pro libovolný typ, který lze určit za běhu. Toto je pouze pro spravovaný kód.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní představuje základní třídu, ze které lze odvodit specializovaná rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní neposkytuje žádné metody, které nejsou zděděné z `IDebugField` .

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
