---
title: Připojení přímo k programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739264"
---
# <a name="attach-directly-to-a-program"></a>Připojení přímo k programu
Uživatelé, kteří chtějí ladit programy v procesu, který je již spuštěn, obvykle postupujte podle tohoto procesu:

1. V prostředí IDE zvolte příkaz **Procesy ladění** z nabídky **Nástroje.**

    Zobrazí se dialogové okno **Procesy.**

2. Zvolte proces a klepněte na tlačítko **Připojit.**

    Zobrazí se dialogové okno **Připojit k procesu** se seznamem všech ladicích motorů nainstalovaných v počítači.

3. Zadejte des, které mají být používány k ladění vybraného procesu, a klepněte na tlačítko **OK**.

   Ladicí balíček spustí relaci ladění a předá jí seznam des. Relace ladění zase předá tento seznam spolu s funkcí zpětného volání do vybraného procesu a potom požádá proces o výčet spuštěných programů.

   Programově v reakci na požadavek uživatele ladicí balíček vytvoří instance správce ladění relace (SDM) a předá mu seznam vybraných des. Spolu se seznamem ladicí balíček předá rozhraní SDM [IDebugCallbackback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Ladicí balíček předá seznam DEs vybranému procesu voláním [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). SDM pak volá [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na portu výčet programů spuštěných v procesu.

   Od tohoto okamžiku je každý ladicí modul připojen k programu přesně tak podrobně popsanému v [připojování po spuštění](../../extensibility/debugger/attaching-after-a-launch.md), se dvěma výjimkami.

   Z důvodu efektivity jsou des, které jsou implementovány ke sdílení adresního prostoru s SDM jsou seskupeny tak, aby každý DE má sadu programů, které bude připojit k. V tomto případě [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) volání [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) a předá pole programů připojit.

   Druhou výjimkou je, že události při spuštění odeslané de připojení k programu, který je již spuštěn obvykle nezahrnují událost vstupního bodu.

## <a name="see-also"></a>Viz také
- [Odesílání událostí spuštění po spuštění](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
