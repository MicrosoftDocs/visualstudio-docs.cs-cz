---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718594"
---
# <a name="idebugthread2"></a>IDebugThread2
Toto rozhraní představuje vlákno spuštěné v programu.

## <a name="syntax"></a>Syntax

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, aby představovalo vlákno provádění v jednom programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [getthread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) pro získání tohoto rozhraní představující aktuálně aktivní vlákno.

 Toto rozhraní se používá také při vytváření požadavku na zarážku (viz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Toto rozhraní se také vrátí při překladu vázané nebo chybové zarážky (viz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) a [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugThread2` .

|Metoda|Popis|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Načte seznam rámců zásobníku pro toto vlákno.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Získá název vlákna.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Nastaví název vlákna.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Získá program, ve kterém je vlákno spuštěno.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Určuje, zda lze další příkaz nastavit na daný rámec zásobníku a kontext kódu.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Nastaví další příkaz na daný rámec zásobníku a kontext kódu.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Získá identifikátor systémového vlákna.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Pozastaví vlákno.|
|[Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Obnoví vlákno.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Získá vlastnosti, které popisují vlákno.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Získá logické vlákno přidružené k tomuto fyzickému vláknu.|

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že jedno fyzické vlákno může být spuštěno ve více programech, může být více než jeden program ve více `IDebugThread2` než jednom programu představovat stejné fyzické vlákno.

 Při výskytu zarážky nebo výjimky je událost odeslána voláním [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jedním z argumentů této metody je `IDebugThread2` rozhraní představující aktuální vlákno. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se používá k získání rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro aktuální rámec zásobníku.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
