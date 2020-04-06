---
title: Spuštění ladicího programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738454"
---
# <a name="launch-the-debugger"></a>Spuštění ladicího programu
Spuštění ladicího programu vyžaduje odeslání správné posloupnosti metod a událostí s jejich vlastníatributy.

## <a name="sequences-of-methods-and-events"></a>Sekvence metod a událostí

1. Správce ladění relace (SDM) se nazývá výběrem nabídky **Ladění** a pak výběrem **start**. Další informace naleznete [v tématu Spuštění programu](../../extensibility/debugger/launching-a-program.md).

2. SDM volá [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda.

3. Na základě modelu procesu ladicí `IDebugProgramNodeAttach2::OnAttach` modul (DE) metoda vrátí jednu z následujících metod, která určuje, co se stane dál.

     Pokud `S_FALSE` vrátí, ladicí modul (DE) má být načten v procesu virtuálního počítače.

     -nebo-

     Pokud `S_OK` vrátí DE má být načten v procesu SDM. SDM pak provádí následující úkoly:

    1. Volání [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) získat informace o motoru DE.

    2. Spoluvytváří DE.

    3. Volání [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. DE odešle [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM `EVENT_SYNC` s atributem.

5. DE odešle [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM `EVENT_SYNC` s atributem.

6. DE odešle [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM `EVENT_SYNC` s atributem.

7. DE odešle [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM `EVENT_SYNC` s atributem.

8. DE odešle [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM `EVENT_SYNC` s atributem.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
- [Spuštění programu](../../extensibility/debugger/launching-a-program.md)
