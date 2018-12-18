---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119247"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Modul ladění (DE) může poslat této události volitelné pro relaci ladění správce (SDM), pokud program byla zastavena.

## <a name="syntax"></a>Syntaxe

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory

Toto rozhraní byla zavedena v systému Visual Studio 2005. Předchozí verze nepodporuje asynchronní zastavit.

[Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) volá SDM ve scénářích více procesů nebo více program. V případě, že jeden program odesílá události zastavení SDM, požaduje SDM ostatních programů příliš zastavit.

Asynchronně informovat SDM, který program přestal slouží k zastavení. Informuje o SDM je užitečné pro modul překladač ladění, kde někdy žádný kód běží uvnitř vyladěnou programu, tak [Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nelze dokončit, synchronně. Pokud modul ladění chce využít toto asynchronní oznámení, musí vracet `S_ASYNC_STOP` z [Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll