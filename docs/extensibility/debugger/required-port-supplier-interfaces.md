---
title: Požadovaná rozhraní pro dodavatele portů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713154"
---
# <a name="required-port-supplier-interfaces"></a>Požadovaná rozhraní dodavatele portů
Dodavatel portu musí implementovat rozhraní [IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Dodavatel portů dodává porty a implementuje je. Proto musí spustit následující rozhraní:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Popisuje port a vyjmenovává všechny procesy spuštěné na portu.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Poskytuje pro spouštění a ukončování procesů na portu.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Poskytuje mechanismus pro programy spuštěné v kontextu tohoto portu, který jej upozorní na vytváření a zničení uzlu programu. Další informace naleznete v tématu [Program uzly](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Poskytuje spojovací bod pro [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Provoz dodavatele přístavu
 [Jímka IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) obdrží oznámení při procesu a programy jsou vytvořeny a zničeny na portu. Port je nutné odeslat [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) při vytvoření procesu a [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) při zničení procesu na portu. Port je také nutné odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) při vytvoření programu a [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) při zničení programu v procesu spuštěného na portu.

 Port obvykle odesílá program vytvořit a zničit události v reakci na [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) a [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metody, v uvedeném pořadí.

 Vzhledem k tomu, že port může spustit a ukončit fyzické procesy i logické programy, musí být ladicí modul implementována také následujícími rozhraními:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Popisuje fyzický proces. Musí být zavedeny alespoň tyto metody:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Poskytuje způsob, jak sDM připojit a odpojit sám od procesu.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Popisuje logický program. Musí být zavedeny alespoň tyto metody:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Poskytuje způsob, jak sDM připojit k tomuto programu.

## <a name="see-also"></a>Viz také
- [Implementace dodavatele portů](../../extensibility/debugger/implementing-a-port-supplier.md)
