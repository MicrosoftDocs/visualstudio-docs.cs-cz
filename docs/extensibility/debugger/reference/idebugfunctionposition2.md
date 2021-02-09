---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e05cc09d2c252ddeaadc3cfa1b40e1a5797b6d79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920898"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Toto rozhraní představuje abstraktní pozici funkce ve zdrojovém dokumentu.

## <a name="syntax"></a>Syntax

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo pozici funkce ve zdrojovém dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se dodává jako součást [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) unie (konkrétně [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) struktura), která je součástí [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury, která se používá při vytváření nedokončené zarážky.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugFunctionPosition2` .

|Metoda|Popis|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Získá název funkce, ke které je tato pozice relativní.|
|[GetOffset –](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Získá posun od začátku funkce.|

## <a name="remarks"></a>Poznámky
 Pozice reprezentovaná tímto rozhraním je založená na textu, konkrétně [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktuře.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
