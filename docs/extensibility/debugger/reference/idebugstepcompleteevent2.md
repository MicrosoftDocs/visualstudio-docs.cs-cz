---
title: IDebugStepCompleteEvent2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289609c93cf0e58eb44500bff135282d01212bbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719460"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Toto rozhraní je odesláno ladicím strojem (DE) správci ladění relace (SDM), když ladicí program dokončí krok do, krok přes nebo krok z řádku zdrojového kódu nebo příkazu nebo instrukce.

## <a name="syntax"></a>Syntaxe

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní sestavy dokončení operace kroku. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá [QueryInterface](/cpp/atl/queryinterface) pro `IDebugEvent2` přístup k rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události hlásit dokončení operace kroku. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) která je poskytována sdm, když je připojen k programu, který je odladěn.

## <a name="remarks"></a>Poznámky
 Po dokončení kroku je laděný program opět pozastaven a ide aktualizuje všechna okna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
