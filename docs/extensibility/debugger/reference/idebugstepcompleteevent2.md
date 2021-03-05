---
description: Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když je program laděný, a dokončuje krok do, krok za krokem nebo krok mimo řádek zdrojového kódu nebo příkazu nebo instrukce.
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f366b9eb1d9406ba5207016ca97ea40d1fd48529
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149532"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když je program laděný, a dokončuje krok do, krok za krokem nebo krok mimo řádek zdrojového kódu nebo příkazu nebo instrukce.

## <a name="syntax"></a>Syntax

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, aby nahlásilo dokončení operace kroku. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [](/cpp/atl/queryinterface) přístup k rozhraní QueryInterface `IDebugEvent2` .

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a pošle tento objekt události, aby nahlásil dokončení operace kroku. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.

## <a name="remarks"></a>Poznámky
 Po dokončení kroku se program, který se právě ladí, pozastaví a IDE aktualizuje všechna jeho okna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
