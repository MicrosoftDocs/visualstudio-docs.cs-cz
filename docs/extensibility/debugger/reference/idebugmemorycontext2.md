---
title: IDebugMemoryContext2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727424"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Toto rozhraní představuje pozici v adresním prostoru počítače, ve které je laděný program.

## <a name="syntax"></a>Syntaxe

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující adresu v paměti.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) nebo [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) vrátí toto rozhraní. Také volání [Přidat](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) a [Odečíst](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) vrátit nové kopie tohoto rozhraní po příslušné aritmetické operace byla použita.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugMemoryContext2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Získá uživatelem zobrazitelný název pro tento kontext.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Získá informace, které popisuje tento kontext.|
|[Přidat](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Přidá zadanou hodnotu k adrese aktuálního kontextu k vytvoření nového kontextu.|
|[Odečíst](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odečte zadanou hodnotu z adresy aktuálního kontextu a vytvoří nový kontext.|
|[Porovnání](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porovná dva kontexty způsobem označeným porovnáním příznaků.|

## <a name="remarks"></a>Poznámky
 Visual Studio **memory** okno volá [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) získat `IDebugMemoryContext2` rozhraní, které obsahuje vyhodnocený výraz použitý pro adresu paměti. Tento kontext je pak předán [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) zadat adresu ke čtení nebo zápisu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
