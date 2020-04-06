---
title: IDebugEnumField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7885f36a113809e81279498a769e257af4f1cde2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730167"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Toto rozhraní představuje typ výčtu.

## <a name="syntax"></a>Syntaxe

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní představující výčt.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [queryinterface](/cpp/atl/queryinterface) získat toto rozhraní z rozhraní [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) pokud [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) vrátí `FIELD_TYPE_ENUM`.

## <a name="methods-in-vtable-order"></a>Metody v pořadí VTable
 Kromě metod na rozhraní `IDebugField` `IDebugContainerField` a toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Vrátí [pole IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující název pro tento typ výčtu.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Vrátí název konstanty výčtu přidružené k dané hodnotě.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Vrátí hodnotu přidruženou k názvu konstanty daného výčtu.|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Vrátí hodnotu přidruženou k názvu konstanty daného výčtu, ale ignoruje případ.|

## <a name="remarks"></a>Poznámky
 Jedná se o základní symbol, který je ve skutečnosti vázán na umístění s [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Vytvořit vazbu](../../../extensibility/debugger/reference/idebugbinder-bind.md)
