---
description: Toto rozhraní rozšiřuje IDebugStackFrame2 a zpracovává zachycené výjimky.
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4049b728842e630a0f0b300130362b8efa8ceec0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053201"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Toto rozhraní rozšiřuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) a zpracovává zachycené výjimky.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní u stejného objektu, který implementuje rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro podporu zachycených výjimek.

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugStackFrame2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame3` zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Zpracovává výjimku pro aktuální rámec zásobníku před jakýmkoli pravidelným zpracováním výjimek.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Vrátí kontext kódu, pokud by došlo k odvíjení zásobníku.|

## <a name="remarks"></a>Poznámky
 Zachycená výjimka znamená, že ladicí program může zpracovat výjimku před všemi běžnými rutinami zpracování výjimky, které jsou volány za běhu. Zachytávání výjimky v podstatě znamená, že doba běhu předstírat, že je k dispozici obslužná rutina výjimky, i když není.

- [InterceptCurrentException –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) je volána během všech běžných událostí zpětného volání výjimky (jedinou výjimkou je, když ladíte kód smíšeného režimu (spravovaný a nespravovaný kód), v takovém případě nelze výjimku zachytit během zpětného volání s poslední pravděpodobností. Pokud DE neimplementuje `IDebugStackFrame3` nebo de vrátí chybu z IDebugStackFrame3:: `InterceptCurrentException` (například `E_NOTIMPL` ), ladicí program zpracuje výjimku normálně.

 Pomocí zachycení výjimky může ladicí program umožnit uživateli provádět změny ve stavu laděného programu a poté pokračovat v provádění v místě, kde byla výjimka vyvolána.

> [!NOTE]
> Zachycené výjimky jsou povoleny pouze ve spravovaném kódu, to znamená v programu, který je spuštěn pod modulem CLR (Common Language Runtime).

 Ladicí stroj indikuje, že podporuje zachycení výjimek nastavením "metricExceptions" na hodnotu 1 v době běhu pomocí `SetMetric` funkce. Další informace najdete v tématech [pomocníka sady SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
