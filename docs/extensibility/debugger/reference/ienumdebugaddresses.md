---
description: Toto rozhraní představuje kolekci objektů, které implementují rozhraní IDebugAddress.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea9e4115c1664e1dcd05041f7ece056b5de01dae
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222637"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Toto rozhraní představuje kolekci objektů, které implementují rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno zprostředkovatelem symbolů pro poskytování sad objektů, které implementují rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Všimněte si, že se nejedná o standardní výčet modelu COM z důvodu přítomnosti metody [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je vráceno pomocí [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) a [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní implementuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Načte další sadu objektů [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) z výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Přeskočí zadaný počet položek.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Obnoví výčet na první položku.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Načte kopii aktuálního výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Načte počet položek ve výčtu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní obvykle používá ladicí stroj k určení vhodné adresy pro vyhodnocení výrazu.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
