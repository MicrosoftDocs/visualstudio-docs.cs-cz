---
title: IDebugProgramNameChangedEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722144"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Odesláno z ladicího modulu (DE) do správce ladění relace (SDM) při změně názvu programu.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 De implementuje toto rozhraní hlásit, že název programu se změnil. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. Modul SDM používá [queryinterface](/cpp/atl/queryinterface) pro přístup k rozhraní **IDebugEvent2.**

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události k nahlášení změny názvu programu. DE odešle tuto událost pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm při připojení k programu, který je odladěn. Dodavatel vlastního portu odešle tuto událost pomocí rozhraní I.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
