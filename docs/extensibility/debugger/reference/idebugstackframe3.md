---
title: IDebugStackFrame3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719466"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Toto rozhraní rozšiřuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro zpracování zachycených výjimek.

## <a name="syntax"></a>Syntaxe

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní na stejném objektu, který implementuje rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro podporu zachycených výjimek.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` na rozhraní získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Zpracovává výjimku pro aktuální rámec zásobníku před jakýmkoli pravidelným zpracováním výjimek.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Vrátí kontext kódu, pokud by došlo k unwind zásobníku.|

## <a name="remarks"></a>Poznámky
 Zachycená výjimka znamená, že ladicí program může zpracovat výjimku před tím, než jsou všechny normální rutiny zpracování výjimek volány časem spuštění. Zachycení výjimky v podstatě znamená, že doba běhu předstírat, že je obslužná rutina výjimky k dispozici i v případě, že není.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) je volána během všech normálních událostí zpětného volání výjimky (jedinou výjimkou je, pokud ladíte kód smíšeného režimu (spravovaný a nespravovaný kód), v takovém případě výjimku nelze zachytit během zpětného volání poslední šance). Pokud DE neimplementuje `IDebugStackFrame3`, nebo DE vrátí chybu z IDebugStackFrame3::`InterceptCurrentException` (například `E_NOTIMPL`), pak ladicí program bude zpracovávat výjimku normálně.

 Zachycením výjimky ladicí program může umožnit uživateli provést změny stavu laděného programu a potom pokračovat v provádění v místě, kde byla vyvolána výjimka.

> [!NOTE]
> Zachycené výjimky jsou povoleny pouze ve spravovaném kódu, tedy v programu, který je spuštěn pod clr (Common Language Runtime).

 Ladicí modul označuje, že podporuje zachycení výjimek nastavením "metricExceptions" na hodnotu 1 za běhu pomocí `SetMetric` funkce. Další informace naleznete v [tématu SDK Helpers for Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
