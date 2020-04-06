---
title: IEnumDebugAddresses | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717584"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Toto rozhraní představuje kolekci objektů implementujících rozhraní [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno zprostředkovatelem symbolů k poskytování sad objektů, které implementují rozhraní [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Všimněte si, že se nejedná o standardní výčet COM z důvodu přítomnosti [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) metody.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je vrácena [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) a [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Toto rozhraní implementuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Načte další sadu [iDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objekty z výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Přeskočí zadaný počet položek.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Obnoví výčet na první položku.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Načte kopii aktuálnívýčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Načte počet položek ve výčtu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní se obvykle používá ladicí stroj k určení příslušné adresy, která má být zadána vyhodnocení výrazu.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
