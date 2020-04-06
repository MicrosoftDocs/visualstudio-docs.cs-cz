---
title: IDebugDisassemblyStream2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732042"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Toto rozhraní představuje proud instrukcí.

## <a name="syntax"></a>Syntaxe

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní pro podporu demontáže kódu programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metoda vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugDisassemblyStream2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Přečte pokyny počínaje aktuální polohou v datovém proudu demontáže.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Přesune ukazatel pro čtení v datovém proudu demontáže o daný počet instrukcí vzhledem k zadané poloze.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Vrátí identifikátor umístění kódu pro určitý kontext kódu.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Vrátí objekt kontextu kódu odpovídající zadanému identifikátoru umístění kódu.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Vrátí identifikátor umístění kódu, který představuje aktuální umístění kódu.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Získá zdrojový dokument přidružený k této demontáži datového proudu.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Získá rozsah této demontáže datového proudu.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Získá velikost tohoto datového proudu demontáže.|

## <a name="remarks"></a>Poznámky
 Datový proud demontáže lze vytvořit tak, aby reprezentoval celý adresní prostor nebo pouze funkci nebo modul v prostoru. Každá instrukce je reprezentována [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) struktury vrácené volání [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
