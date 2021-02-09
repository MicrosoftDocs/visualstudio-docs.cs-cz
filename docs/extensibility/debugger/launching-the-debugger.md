---
title: Spouští se ladicí program | Microsoft Docs
description: Přečtěte si o sekvenci metod a událostí s jejich správnými atributy potřebnými ke spuštění ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9f8bc85672fc89205ab25fa9954e1c28e10f859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926393"
---
# <a name="launch-the-debugger"></a>Spuštění ladicího programu
Spuštění ladicího programu vyžaduje odeslání správné posloupnosti metod a událostí s jejich správnými atributy.

## <a name="sequences-of-methods-and-events"></a>Sekvence metod a událostí

1. Správce ladění relace (SDM) se volá výběrem nabídky **ladění** a následným výběrem možnosti **Spustit**. Další informace najdete v tématu [spuštění programu](../../extensibility/debugger/launching-a-program.md).

2. Volání SDM volá metodu [Attach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

3. Na základě modelu procesu ladění (DE) `IDebugProgramNodeAttach2::OnAttach` Metoda vrátí jednu z následujících metod, která určuje, co se stane další.

     Pokud se `S_FALSE` vrátí, ladicí stroj (de) se načte do procesu virtuálního počítače.

     -nebo-

     Pokud se `S_OK` vrátí, bude de načtena v procesu SDM. SDM pak provede následující úlohy:

    1. Volá [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pro získání informací o modulu de.

    2. Společně vytvoří DE.

    3. Volání – [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. DE pošle [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM s `EVENT_SYNC` atributem.

5. DE pošle [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM s `EVENT_SYNC` atributem.

6. DE pošle [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM s `EVENT_SYNC` atributem.

7. DE pošle [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM s `EVENT_SYNC` atributem.

8. DE pošle [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM s `EVENT_SYNC` atributem.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
- [Spuštění programu](../../extensibility/debugger/launching-a-program.md)
