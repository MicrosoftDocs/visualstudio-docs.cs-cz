---
title: IDebugEngineProgram2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730297"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Toto rozhraní poskytuje podporu ladění s více vlákny.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul implementuje toto rozhraní pro podporu souběžného ladění více vláken. Toto rozhraní je implementováno na stejném objektu, který implementuje rozhraní [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface) získáte `IDebugProgram2` toto rozhraní z rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugEngineProgram2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Zastaví všechna vlákna spuštěná v tomto programu.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Hodinky pro provádění (nebo přestat sledovat pro spuštění) dojít v daném vlákně.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Umožňuje (nebo zakáže) vyhodnocení výrazu dojít v daném vlákně, i v případě, že program je zastaven.|

## <a name="remarks"></a>Poznámky
 Visual Studio volá toto rozhraní v reakci na událost [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a nastavit stavy "Watch for Thread Step" a "Watch for Expression Evaluation on Thread" programu. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) je volána vždy, když má být program zastaven; Tato metoda dává programu možnost ukončit všechna vlákna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
