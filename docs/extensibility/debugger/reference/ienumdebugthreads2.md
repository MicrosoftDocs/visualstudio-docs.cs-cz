---
description: Toto rozhraní vytvoří výčet vláken spuštěných v aktuální relaci ladění.
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3706b9ff004dbe283952dbc3740f8ec4bcb056b2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225731"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Toto rozhraní vytvoří výčet vláken spuštěných v aktuální relaci ladění.

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní tak, aby představovalo seznam vláken v programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Zavolejte [EnumThreads –](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pro získání tohoto rozhraní, které představuje seznam všech vláken ve všech programech spuštěných v procesu. Voláním [EnumThreads –](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) získáte toto rozhraní, které představuje seznam vláken spuštěných v programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugThreads2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Načte zadaný počet vláken v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Přeskočí zadaný počet vláken v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Získá počet vláken v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio obvykle získá toto rozhraní pro aktualizaci okna **vlákna** a také k získání prvního vlákna seznamu, aby bylo možné volat metodu [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)a [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Spuštěním](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
