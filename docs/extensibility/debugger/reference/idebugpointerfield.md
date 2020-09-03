---
title: IDebugPointerField | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725591"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Toto rozhraní představuje typ ukazatele.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní, aby představovalo ukazatel.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pokud se vrátí [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) , použijte [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v `IDebugField` `IDebugContainerField` rozhraních a implementuje toto rozhraní následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující cíl ukazatele.|

## <a name="remarks"></a>Poznámky
 V C/C++ může být ukazatel kontejnerem, pokud se používá se zápisem pole. Například předané `char *pString` , `pString` má typ ukazatele na `char` . `pString[3]` má typ kontejneru, který je ukazatel na `char` který odkazuje na čtvrtý prvek daného kontejneru.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
