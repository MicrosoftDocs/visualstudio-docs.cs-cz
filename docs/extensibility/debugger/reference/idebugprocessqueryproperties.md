---
description: Toto rozhraní je rozšířením rozhraní implementovaného IDebugProcess2 implementací.
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8205b96723a1b48da46e6e19162c50139c9fe71d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166213"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Toto rozhraní je rozšířením rozhraní implementovaného [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementací. Umožňuje implementátorovi získat informace o prostředí procesu ladění.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Implementujte toto rozhraní, aby se získaly informace o spouštěcím prostředí procesu ladění.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProcessQueryProperties` .

|Metoda|Popis|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Dotaz na hodnotu vlastnosti.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Dotaz na hodnoty vlastností.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je naimplementované zřídka.

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
