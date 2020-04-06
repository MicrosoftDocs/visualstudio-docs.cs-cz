---
title: IDebugFunctionPosition2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c260b6316207b0079a2ca8893b851db8b1288ba6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728306"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Toto rozhraní představuje abstraktní pozici funkce ve zdrojovém dokumentu.

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující pozici funkce v rámci zdrojového dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je dodáván jako součást [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) unie (konkrétně [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) struktury), která je zase součástí [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury, který se používá při vytváření čekající zarážky.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugFunctionPosition2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Získá název funkce, která je relativní vzhledem k této pozici.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Získá posun od začátku funkce.|

## <a name="remarks"></a>Poznámky
 Pozice reprezentovaná tímto rozhraním je textová, konkrétně [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
