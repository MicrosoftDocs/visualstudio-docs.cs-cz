---
title: Adresa IDebugAddress | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f281ceb1f305c5774fedbf725f2e6a9481d073d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736589"
---
# <a name="idebugaddress"></a>IDebugAddress
Toto rozhraní představuje adresu položky. Je vrácena obslužnou rutinou symbolu.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní představující adresu objektu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Mnoho metod na mnoha rozhraních vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Načte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) strukturu popisující objekt a jeho umístění.|

## <a name="remarks"></a>Poznámky
 Zprostředkovatel symbolu vrátí toto rozhraní představující objekt a jeho umístění v rámci určitého oboru (například funkce, metoda nebo třída). Toto rozhraní je vrácena z a předána různé metody poskytovatele symbolu a vyhodnocení výrazu. Za normálních okolností je poskytovatel symbolu jedinou entitou, která potřebuje interpretovat obsah tohoto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
