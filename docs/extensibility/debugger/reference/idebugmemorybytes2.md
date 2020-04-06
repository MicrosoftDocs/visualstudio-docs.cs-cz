---
title: IDebugMemoryBytes2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727503"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Toto rozhraní představuje bajty paměti.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující bajty v paměti.

## <a name="notes-for-callers"></a>Poznámky pro volající
- [Funkce GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) vrátí toto rozhraní a poskytuje přístup k systémové paměti. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) a [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) vrátí toto rozhraní poskytnout přístup k bajtů objektu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugMemoryBytes2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Přečte sekvenci bajtů začínajících na daném místě.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zápisy `dwCount` bajtů, `pStartContext`počínaje .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Získá velikost v bajtů paměti reprezentované tímto rozhraním.|

## <a name="remarks"></a>Poznámky
 Pro vlastnosti rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představující pole `IDebugMemoryBytes2` poskytuje rozhraní pro přístup k hodnotám v tomto poli.

 Zobrazení paměti **sady Visual** Studio volá [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) k načtení `IDebugMemoryBytes2` rozhraní pro přístup k systémové paměti. Adresa, ke které má být získán přístup, je získána analýzou výrazu zadaného jako adresa do zobrazení `IDebugProperty2` paměti a následným vyhodnocením analyzovaného výrazu pomocí [funkce EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) k získání rozhraní. Volání [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) vrátí [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) který popisuje adresu paměti. Tento kontext paměti je pak předán [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
