---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67a5bfe92547738a672cb6881234ae80f76aeda8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869762"
---
# <a name="idebugfield"></a>IDebugField
Toto rozhraní představuje pole, které je popisem symbolu nebo typu.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní jako základní třídu pro všechna pole.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je základní třídou pro všechna pole. Na základě návratové hodnoty [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)může toto rozhraní vracet více specializovaných rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface). Kromě toho mnoho rozhraní vrací `IDebugField` objekty z různých metod.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugField` .

|Metoda|Popis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Získá nezobrazitelné informace o symbolu nebo typu.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Získá typ pole.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Získá typ pole.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Načte kontejner pole.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Získá adresu pole.|
|[GetSize –](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Získá velikost pole v bajtech.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Získá Rozšířené informace o poli.|
|[Výši](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porovná dvě pole.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Načte informace nezávislé na typu symbolu nebo typu.|

## <a name="remarks"></a>Poznámky
 Typ je ekvivalentní jazyku jazyka C `typedef` .

 V následujícím příkladu jazyka C++ `weather` je typ třídy, a `sunny` a `stormy` jsou symboly:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Určuje, zda pole představuje symbol nebo typ lze určit voláním [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) a kontrolou výsledku [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Pokud `FIELD_KIND_TYPE` je bit nastaven, pole je typu a pokud `FIELD_KIND_SYMBOL` je bit nastaven, je symbol.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
