---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727424"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Toto rozhraní představuje pozici v adresním prostoru počítače, na kterém je spuštěný program, který se právě ladí.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo adresu v paměti.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní vrátí volání [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) nebo [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) . Také volání funkce [Přidat](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) a [odečíst](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) vrátí nové kopie tohoto rozhraní po použití příslušné aritmetické operace.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugMemoryContext2` .

|Metoda|Popis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Získá uživatelsky zobrazitelný název pro tento kontext.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Získá informace, které popisují tento kontext.|
|[Přidat](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Přidá zadanou hodnotu k adrese aktuálního kontextu pro vytvoření nového kontextu.|
|[Odčítání](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odečte zadanou hodnotu od adresy aktuálního kontextu pro vytvoření nového kontextu.|
|[Porovnání](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porovná dva kontexty způsobem určeným pomocí porovnání příznaků.|

## <a name="remarks"></a>Poznámky
 Okno **paměti** sady Visual Studio volá [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) , aby získalo `IDebugMemoryContext2` rozhraní, které obsahuje vyhodnocený výraz použitý pro danou adresu paměti. Tento kontext se pak předává do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) a určí adresu pro čtení nebo zápis.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
