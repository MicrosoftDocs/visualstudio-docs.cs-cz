---
title: Požadovaná rozhraní dodavatele portů | Microsoft Docs
description: Seznamte se s rozhraními, která musí dodavatel portu spustit. Dodavatel portů dodává porty a implementuje je.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96cf70302839a9de3c5fb0fec01136d9700ee17e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902368"
---
# <a name="required-port-supplier-interfaces"></a>Požadovaná rozhraní dodavatele portů
Dodavatel portu musí implementovat rozhraní [IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Dodavatel portů dodává porty a implementuje je. Proto musí spustit následující rozhraní:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Popisuje port a výčet všech procesů spuštěných na tomto portu.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Poskytuje pro spouštění a ukončování procesů na portu.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Poskytuje mechanismus pro programy spuštěné v kontextu tohoto portu, které ho upozorní na vytvoření a zničení uzlu programu. Další informace najdete v tématu [Programové uzly](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Poskytuje bod připojení pro [IDebugPortEvents2.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Operace dodavatele portu
 Jímka [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) přijímá oznámení při vytváření a zničení procesů a programů na portu. Port je vyžadován k odeslání [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) při vytvoření procesu a [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) při zničení procesu na portu. Port je také potřeba k odeslání [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) při vytvoření programu a [IDebugProgramDestroyEvent2,](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) když je program zničen v procesu spuštěném na portu.

 Port obvykle odesílá události vytvoření a zničení programu v reakci na metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) a [RemoveProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

 Vzhledem k tomu, že port může spouštět a ukončuje fyzické procesy i logické programy, musí ladicí modul implementovat také následující rozhraní:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Popisuje fyzický proces. Musí být implementovány alespoň následující metody:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Poskytuje způsob, jak se SDM připojit a odpojit od procesu.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Popisuje logický program. Musí být implementovány alespoň následující metody:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Poskytuje způsob připojení SDM k tomuto programu.

## <a name="see-also"></a>Viz také
- [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)
