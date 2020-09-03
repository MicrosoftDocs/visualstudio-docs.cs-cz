---
title: IDebugMemoryBytes2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727503"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Toto rozhraní představuje bajty paměti.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo bajty v paměti.

## <a name="notes-for-callers"></a>Poznámky pro volající
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) vrátí toto rozhraní, aby poskytovalo přístup k systémové paměti. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) a [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) vrátí toto rozhraní, aby poskytovalo přístup k bajtům objektu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugMemoryBytes2` .

|Metoda|Popis|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Přečte sekvenci bajtů počínaje daným umístěním.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajty počínaje `pStartContext` .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Získá velikost paměti reprezentované tímto rozhraním (v bajtech).|

## <a name="remarks"></a>Poznámky
 V případě vlastností rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) představující pole poskytuje `IDebugMemoryBytes2` rozhraní pro přístup k hodnotám v tomto poli.

 **Zobrazení paměti** sady Visual Studio volá [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) k načtení `IDebugMemoryBytes2` rozhraní pro přístup k systémové paměti. Adresa, na kterou se má získat přístup, je získaná analýzou výrazu zadaného jako adresy do zobrazení paměti a následným vyhodnocením analyzovaného výrazu pomocí [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) k získání `IDebugProperty2` rozhraní. Volání [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) vrátí [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , které popisuje adresu paměti. Tento kontext paměti je pak předán do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
