---
title: Připojení a odpojení programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739266"
---
# <a name="attaching-and-detaching-to-a-program"></a>Připojení a odpojení k programu
Připojení ladicího programu vyžaduje odeslání správné posloupnosti metod a událostí se správnými atributy.

## <a name="sequence-of-methods-and-events"></a>Posloupnost metod a událostí

1. Správce ladění relace (SDM) volá [metodu OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    Na základě modelu procesu ladicí `IDebugProgramNodeAttach2::OnAttach` modul (DE) metoda vrátí jednu z následujících metod, která určuje, co se stane dál.

    Pokud `S_FALSE` je vrácena, ladicí modul byl úspěšně připojen k programu. V opačném případě [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda je volána k dokončení procesu připojení.

    Pokud `S_OK` je vrácena, DE má být načten ve stejném procesu jako SDM. SDM provádí následující úkoly:

   1. Volání [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) získat informace o motoru DE.

   2. Spoluvytváří DE.

   3. Volání [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. DE odešle [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM `EVENT_SYNC` s atributem.

3. DE odešle [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM `EVENT_SYNC` s atributem.

4. DE odešle [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM `EVENT_SYNC_STOP` s atributem.

   Odpojení od programu je jednoduchý dvoustupňový proces:

5. SDM volání [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. DE odešle [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
