---
title: Připojování k programu | Microsoft Docs
description: Přečtěte si, jak Visual Studio implementuje ladicí program, který se připojí k programu po registraci programu s příslušným portem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d880edbea79f56cbd2c90905b0bc2f712dba59b1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055268"
---
# <a name="attach-to-the-program"></a>Připojit k programu
Po zaregistrování programů pomocí příslušného portu je nutné připojit ladicí program k programu, který chcete ladit.

## <a name="choose-how-to-attach"></a>Volba způsobu připojení
 Existují tři způsoby, jak se správce ladění relace (SDM) pokusí připojit k laděnému programu.

1. Pro programy, které modul pro ladění spouští pomocí metody [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (typické pro interpretované jazyky), SDM získává rozhraní [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) z objektu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) přidruženého k programu, ke kterému se připojuje. Pokud model SDM může získat `IDebugProgramNodeAttach2` rozhraní, model SDM pak zavolá metodu [Attach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . `IDebugProgramNodeAttach2::OnAttach`Metoda vrátí `S_OK` , aby označovala, že se k programu nepřipojila a že se k programu mohou připojit jiné pokusy.

2. Pokud SDM může získat rozhraní [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) z programu, ke kterému se připojujete, zavolá model SDM metodu [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . Tento přístup je typický pro programy, které spustil dodavatel portů vzdáleně.

3. Pokud se program nedá připojit prostřednictvím `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` metod nebo, model SDM načte ladicí modul (Pokud ještě není načtený) voláním `CoCreateInstance` funkce a pak zavolá metodu [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) . Tento přístup je typický pro programy spouštěné místně dodavatelem portu.

    Je také možné, že vlastní dodavatel portu volá `IDebugEngine2::Attach` metodu v implementaci metody vlastního dodavatele portu `IDebugProgramEx2::Attach` . V takovém případě se v takovém případě vlastní dodavatel portu spustí ladicí stroj na vzdáleném počítači.

   Příloha se dosahuje, když správce ladění relace (SDM) volá metodu [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .

   Pokud spustíte DE v rámci stejného procesu jako aplikace, která se má ladit, je nutné implementovat následující metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Po `IDebugEngine2::Attach` zavolání metody proveďte následující kroky v implementaci `IDebugEngine2::Attach` metody:

1. Odešle objekt události [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM. Další informace najdete v tématu [posílání událostí](../../extensibility/debugger/sending-events.md).

2. Zavolejte metodu [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) pro objekt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , který byl předán `IDebugEngine2::Attach` metodě.

     Vrátí `GUID` , který se používá k identifikaci programu. `GUID`Musí být uložen v objektu, který představuje místní program, do de a musí být vrácen, pokud `IDebugProgram2::GetProgramId` je metoda volána na `IDebugProgram2` rozhraní.

    > [!NOTE]
    > Při implementaci `IDebugProgramNodeAttach2` rozhraní `GUID` je program předán `IDebugProgramNodeAttach2::OnAttach` metodě. `GUID`Používá se pro program `GUID` vrácený `IDebugProgram2::GetProgramId` metodou.

3. Odešle objekt události [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , který oznamuje protokolu SDM, že `IDebugProgram2` byl vytvořen místní objekt, který reprezentuje program do de. Podrobnosti najdete v tématu [posílání událostí](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Nejedná se o stejný `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metodě. Dřív předaný `IDebugProgram2` objekt je rozpoznán pouze pomocí portu a je samostatným objektem.

## <a name="see-also"></a>Viz také
- [Příloha na základě spuštění](../../extensibility/debugger/launch-based-attachment.md)
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
