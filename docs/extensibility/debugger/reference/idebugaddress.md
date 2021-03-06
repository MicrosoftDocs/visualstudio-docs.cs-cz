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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89e192f61e4cda809e8e6c90106cbe081392a044
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094416"
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
