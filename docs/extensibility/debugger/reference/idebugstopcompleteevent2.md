---
description: Ladicí stroj (DE) může poslat tuto volitelnou událost správci ladění relace (SDM), když se program zastaví.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087142"
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
