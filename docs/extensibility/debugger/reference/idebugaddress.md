---
description: Toto rozhraní představuje adresu položky.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154961"
---
# <a name="idebugaddress"></a>IDebugAddress
Toto rozhraní představuje adresu položky. Je vrácen obslužnou rutinou symbolu.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní, aby představovalo adresu objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Mnoho metod v mnoha rozhraních vrací toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Načte strukturu [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) popisující objekt a jeho umístění.|

## <a name="remarks"></a>Poznámky
 Zprostředkovatel symbolů vrátí toto rozhraní pro reprezentaci objektu a jeho umístění v rámci určitého oboru (například funkce, metody nebo třídy). Toto rozhraní se vrátí z a předává do různých metod poskytovatele symbolů a vyhodnocovacího filtru výrazů. Obvykle je poskytovatel symbolů jedinou entitou, která potřebuje interpretovat obsah tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
