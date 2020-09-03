---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722640"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Toto rozhraní představuje program, který je spuštěn v procesu a rozšiřuje [provádění](../../../extensibility/debugger/reference/idebugprogram2-execute.md) tím, že poskytuje informace o vláknech.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Modul ladění (DE) a vlastní dodavatel portu implementují toto rozhraní tak, aby představovalo program v procesu. Správce ladění relace (SDM) implementuje také toto rozhraní, aby poskytovalo informace, které se mají [připojit](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Poznámky pro volající
 Událost [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) vrací toto rozhraní pro nový program. Toto rozhraní se používá také jako parametr pro mnoho metod na více rozhraních.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProgram3` .

|Metoda|Popis|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Spustí program. Vlákno je vráceno, aby poskytovalo ladicí informace o tom, ve kterém vlákně uživatel zobrazuje, když je spuštěn.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Poznámky
 Program je kontejner vláken spuštěný v určité architektuře run-time, zatímco proces se skládá z jednoho nebo více programů.

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Další](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Událost](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
