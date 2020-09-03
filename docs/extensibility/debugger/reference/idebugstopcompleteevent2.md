---
title: IDebugStopCompleteEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719440"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Ladicí stroj (DE) může poslat tuto volitelnou událost správci ladění relace (SDM), když se program zastaví.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory

Toto rozhraní bylo představeno se sadou Visual Studio 2005. Předchozí verze nepodporovaly asynchronní zastavování.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) se volá v modelu SDM ve scénářích s více procesy nebo s více programy. Když jeden program pošle událost zastavení do SDM, požadavky SDM na zastavení také vyžádají jiné programy.

Stop se používá k asynchronnímu informování SDM, že se program zastavil. Informování modelu SDM je užitečné pro ladicí stroj překladače, kde někdy v laděném programu není spuštěn žádný kód, takže [zastavení](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nelze dokončit synchronně. Pokud ladicí stroj chce použít toto asynchronní oznámení, musí se vrátit z jeho `S_ASYNC_STOP` [zastavení](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
