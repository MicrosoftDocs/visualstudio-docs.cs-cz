---
description: Toto rozhraní představuje typ výčtu.
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f78e8d2560224ad22a58b74823530b6be4b1efb8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153206"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Toto rozhraní představuje typ výčtu.

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní, aby představovalo výčet.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pokud se vrátí [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) , použijte [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Metody v pořadí VTable
 Kromě metod v `IDebugField` `IDebugContainerField` rozhraních a implementuje toto rozhraní následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující název tohoto výčtového typu.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Vrátí název konstanty výčtu přidružené k dané hodnotě.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Vrátí hodnotu přidruženou k danému názvu konstanty výčtu.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Vrací hodnotu přidruženou k dané konstantě výčtu, ale ignoruje velikost písmen.|

## <a name="remarks"></a>Poznámky
 Je to základní symbol, který je ve skutečnosti vázaný na umístění s [vazbou](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Zapisovat](../../../extensibility/debugger/reference/idebugbinder-bind.md)
