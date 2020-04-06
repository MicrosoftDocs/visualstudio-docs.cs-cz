---
title: Příloha založená na spuštění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738469"
---
# <a name="launch-based-attachment"></a>Příloha založená na spuštění
Příloha programu založená na spuštění je automatická. Když je proces hostující program spuštěn sm, příloha založená na spuštění následuje cestu podobnou metodě ručního připojení. Další informace naleznete v [tématu Připojení k programu](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Proces připojování
 Hlavní rozdíl je posloupnost událostí po **Připojit** volání, takto:

1. Odešlete objekt u události **IDebugEngineCreateEvent2** do objektu SDM. Podrobnosti naleznete v tématu [Odesílání událostí](../../extensibility/debugger/sending-events.md).

2. Volání `IDebugProgram2::GetProgramId` metody v rozhraní **IDebugProgram2** předané **metodě Attach.**

3. Odešlete objekt události **IDebugProgramCreateEvent2,** který oznámí objektu SDM, že byl vytvořen místní objekt **IDebugProgram2,** který představuje program de.

4. Odešlete objekt události [IDebugThreadCreateEvent2,](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) který upozorní objekt SDM, že je pro proces, který byl spuštěn, vytvořen nový podproces.

## <a name="see-also"></a>Viz také
- [Odeslat požadované události](../../extensibility/debugger/sending-the-required-events.md)
- [Povolení odlažení programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
