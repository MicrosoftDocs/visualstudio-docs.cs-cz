---
description: Toto rozhraní představuje kolekci objektů, které implementují rozhraní IDebugField.
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7534173fe927f1486e3f3c190ff2e427bb51bec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052915"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Toto rozhraní představuje kolekci objektů, které implementují rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntax

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno zprostředkovatelem symbolů pro poskytování sad objektů, které implementují rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Všimněte si, že se nejedná o standardní výčet modelu COM z důvodu přítomnosti metody [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je vráceno pomocí [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) a [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní implementuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Načte další sadu objektů [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) z výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Přeskočí zadaný počet položek.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Obnoví výčet na první položku.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Načte kopii aktuálního výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Načte počet položek ve výčtu.|

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
