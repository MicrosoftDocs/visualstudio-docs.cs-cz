---
title: Připojení a odpojení programu | Microsoft Docs
description: Přečtěte si, jak odeslat správnou sekvenci metod a událostí se správnými atributy pro připojení ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d41f9e3f88f28dbbb83e9c7e00fe8b8afd434c26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837746"
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
