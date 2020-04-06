---
title: IDebugStopCompleteEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719440"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Ladicí modul (DE) může odeslat tuto volitelnou událost správci ladění relace (SDM) při zastavení programu.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory

Toto rozhraní bylo zavedeno s Visual Studio 2005. Předchozí verze nepodporovaly asynchronní zastavení.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) je volána SDM ve víceprocesových nebo víceprogramových scénářích. Když jeden program odešle událost zastavení do SDM, SDM požaduje, aby ostatní programy zastavit, příliš.

Stop se používá k asynchronní informování sdm, že program byl zastaven. Informování SDM je užitečné pro překladač ladicí modul, kde někdy žádný kód běží uvnitř laděný program, takže [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nelze dokončit synchronně. Pokud ladicí modul chce použít toto asynchronní `S_ASYNC_STOP` oznámení, musí vrátit z [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
