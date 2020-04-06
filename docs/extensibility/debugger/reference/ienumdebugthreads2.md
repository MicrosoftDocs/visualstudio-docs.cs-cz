---
title: IEnumDebugThreads2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715090"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Toto rozhraní vyjmenovává vlákna spuštěná v aktuální relaci ladění.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující seznam podprocesů v programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) získat toto rozhraní představující seznam všech podprocesů ve všech programech spuštěných v procesu. Volání [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) získat toto rozhraní představující seznam podprocesů spuštěných v programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugThreads2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Načte zadaný počet vláken v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Přeskočí zadaný počet podprocesů v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Získá počet podprocesů v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Visual Studio obvykle získá toto rozhraní aktualizovat **podprocesy** okna, jakož i získat první vlákno seznamu, za účelem volání [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)a [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Spuštění](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
