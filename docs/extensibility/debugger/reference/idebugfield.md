---
title: IDebugField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728751"
---
# <a name="idebugfield"></a>IDebugField
Toto rozhraní představuje pole, to znamená popis symbolu nebo typu.

## <a name="syntax"></a>Syntaxe

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní jako základní třídu pro všechna pole.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je základní třídou pro všechna pole. Na základě vrácené hodnoty [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), toto rozhraní může vrátit více specializovaných rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface). Kromě toho mnoho rozhraní `IDebugField` vrátit objekty z různých metod.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugField`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Získá zobrazitelné informace o symbolnebo typ.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Získá druh pole.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Získá typ pole.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Získá kontejner pole.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Získá adresu pole.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Získá velikost pole v bajtů.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Získá rozšířené informace o poli.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porovná dvě pole.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Získá nezávislé informace o symbolnebo typ.|

## <a name="remarks"></a>Poznámky
 Typ je ekvivalentní jazyku `typedef`C .

 V následujícím příkladu jazyka `weather` C++ je `sunny` typ `stormy` třídy a jsou symboly:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Zda pole představuje symbol nebo typ lze určit voláním [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) a zkoumání [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) výsledek. Pokud `FIELD_KIND_TYPE` je bit nastaven, pole je typ `FIELD_KIND_SYMBOL` a pokud je bit nastaven, jedná se o symbol.

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
