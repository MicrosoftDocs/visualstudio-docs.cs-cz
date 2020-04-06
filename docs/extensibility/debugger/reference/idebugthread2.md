---
title: IDebugThread2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718594"
---
# <a name="idebugthread2"></a>IDebugThread2
Toto rozhraní představuje vlákno spuštěné v programu.

## <a name="syntax"></a>Syntaxe

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující vlákno spuštění v jednom programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) získat toto rozhraní představující aktuálně aktivní vlákno.

 Toto rozhraní se také používá při vytváření požadavku na zarážky (viz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Toto rozhraní je také vrácena při řešení vázané nebo chybové zarážky (viz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) a [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugThread2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Načte seznam rámců zásobníku pro toto vlákno.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Získá název vlákna.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Nastaví název vlákna.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Získá program, ve kterém je spuštěno vlákno.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Určuje, zda další příkaz lze nastavit na daný rámec zásobníku a kontext kódu.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Nastaví další příkaz na daný rámec zásobníku a kontext kódu.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Získá identifikátor podprocesu systému.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Pozastaví vlákno.|
|[Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Obnoví vlákno.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Získá vlastnosti, které popisují vlákno.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Získá logické vlákno přidružené k tomuto fyzickému vláknu.|

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že jedno fyzické `IDebugThread2` vlákno může být spuštěno ve více programech, může více než jeden z více programů představovat stejné fyzické vlákno.

 Dojde-li k zarážky nebo výjimce, je událost odeslána voláním [události](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jedním z argumentů této metody `IDebugThread2` je rozhraní představující aktuální vlákno. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) se používá k získání rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pro aktuální rámec zásobníku.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [Událost](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
