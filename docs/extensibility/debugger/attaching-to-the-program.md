---
title: Připojení k programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739251"
---
# <a name="attach-to-the-program"></a>Připojení k programu
Po registraci programů s příslušným portem je nutné připojit ladicí program k programu, který chcete ladit.

## <a name="choose-how-to-attach"></a>Zvolte, jak se má připojit
 Existují tři způsoby, ve kterém ladicí správce relace (SDM) se pokusí připojit k programu, který je laděn.

1. Pro programy, které jsou spuštěny ladicí stroj prostřednictvím [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metoda (typické pro interpretované jazyky, například), SDM získá [rozhraní IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objekt upřipojeného k programu, který je připojen k. Pokud SDM lze `IDebugProgramNodeAttach2` získat rozhraní, SDM pak volá [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda. Metoda `IDebugProgramNodeAttach2::OnAttach` vrátí `S_OK` označující, že se nepřipojilk programu a že další pokusy mohou být provedeny připojit k programu.

2. Pokud SDM může získat rozhraní [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) z programu, který je připojen k, SDM volá [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metoda. Tento přístup je typický pro programy, které byly spuštěny vzdáleně dodavatelem portu.

3. Pokud program nelze připojit `IDebugProgramNodeAttach2::OnAttach` prostřednictvím `IDebugProgramEx2::Attach` metody nebo, SDM načte ladicí modul (pokud již není načten) voláním `CoCreateInstance` funkce a potom volá [Metodu Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md) Tento přístup je typický pro programy spuštěné místně dodavatelem portu.

    Je také možné pro dodavatele vlastního `IDebugEngine2::Attach` portu volat metodu v implementaci `IDebugProgramEx2::Attach` vlastní port dodavatele metody. Obvykle v tomto případě dodavatel vlastního portu spustí ladicí modul na vzdáleném počítači.

   Přílohy je dosaženo, když správce ladění relace (SDM) volá [Metodu Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Pokud spustíte DE ve stejném procesu jako aplikace, která má být laděna, pak je nutné implementovat následující metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Po `IDebugEngine2::Attach` volání metody postupujte takto při `IDebugEngine2::Attach` implementaci metody:

1. Odešlete objekt u události [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do objektu SDM. Další informace naleznete v [tématu Odesílání událostí](../../extensibility/debugger/sending-events.md).

2. Volání [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metoda na [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objekt, `IDebugEngine2::Attach` který byl předán metodě.

     Vrátí hodnotu, `GUID` která slouží k identifikaci programu. Musí `GUID` být uložen v objektu, který představuje místní program DE a `IDebugProgram2::GetProgramId` musí být `IDebugProgram2` vrácena při volání metody na rozhraní.

    > [!NOTE]
    > Pokud implementujete `IDebugProgramNodeAttach2` rozhraní, `GUID` program je `IDebugProgramNodeAttach2::OnAttach` předán metodě. Používá `GUID` se pro program `GUID` vrácené `IDebugProgram2::GetProgramId` metodou.

3. Odešlete objekt události [IDebugProgramCreateEvent2,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) který oznámí `IDebugProgram2` objektu SDM, že místní objekt byl vytvořen tak, aby reprezentoval program de. Podrobnosti naleznete v [tématu Sending Events](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Toto není `IDebugProgram2` stejný objekt, který `IDebugEngine2::Attach` byl předán do metody. Dříve předaný `IDebugProgram2` objekt je rozpoznán pouze portem a je samostatným objektem.

## <a name="see-also"></a>Viz také
- [Příloha založená na spuštění](../../extensibility/debugger/launch-based-attachment.md)
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Připojit](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md)
