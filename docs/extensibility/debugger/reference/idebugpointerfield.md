---
title: IDebugPointerField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725591"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Toto rozhraní představuje typ ukazatele.

## <a name="syntax"></a>Syntaxe

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní představující ukazatel.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [queryinterface](/cpp/atl/queryinterface) získat toto rozhraní z rozhraní [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) pokud [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) vrátí `FIELD_TYPE_POINTER`.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod na rozhraní `IDebugField` `IDebugContainerField` a toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující cíl ukazatele.|

## <a name="remarks"></a>Poznámky
 V jazyce C/C++ může být ukazatel kontejner, pokud se používá s zápisem pole. Například, `char *pString`given `pString` , má typ `char`ukazatele na . `pString[3]`má typ kontejneru, který je `char` ukazatel, který odkazuje na čtvrtý prvek tohoto kontejneru.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
