---
title: Připojení a odpojení programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a751e6aa70c1aacd5df598e0c0e62da3b9d14b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903154"
---
# <a name="attaching-and-detaching-to-a-program"></a>Připojení k programu a jeho odpojení
Připojení ladicího programu vyžaduje odeslání správné posloupnosti metod a událostí se správnými atributy.

## <a name="sequence-of-methods-and-events"></a>Sekvence metod a událostí

1. Správce ladění relace (SDM) volá metodu [Attach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

    Na základě modelu procesu ladění (DE) `IDebugProgramNodeAttach2::OnAttach` Metoda vrátí jednu z následujících metod, která určuje, co se stane další.

    Pokud `S_FALSE` je vrácena, ladicí modul byl úspěšně připojen k programu. V opačném případě je volána metoda [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) k dokončení procesu připojení.

    Pokud `S_OK` je vrácena, bude de načtena do stejného procesu jako SDM. SDM provádí následující úlohy:

   1. Volá [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pro získání informací o modulu de.

   2. Společně vytvoří DE.

   3. Volání – [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. DE pošle [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM s `EVENT_SYNC` atributem.

3. DE pošle [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM s `EVENT_SYNC` atributem.

4. DE pošle [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM s `EVENT_SYNC_STOP` atributem.

   Odpojení od programu je jednoduchý proces se dvěma kroky, jak je znázorněno níže:

5. Volání SDM se [odpojí](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. DE pošle [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
