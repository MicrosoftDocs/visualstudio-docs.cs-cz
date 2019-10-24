---
title: Panel nástrojů Spy + + | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fa1dfe0917fece3c814678295c5abd6013b426b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729741"
---
# <a name="spy-toolbar"></a>Panel nástrojů nástroje Spy++
Panel nástrojů se zobrazí v panelu nabídek v nástroji Spy + +. Chcete-li zobrazit nebo skrýt panel nástrojů, klikněte v nabídce **zobrazení** na příkaz **panel nástrojů**.

 Na panelu nástrojů jsou k dispozici následující ovládací prvky.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Tlačítko|Efekt|
|------------|------------|
|![Tlačítko&#43; &#43; programu Spy Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Zobrazí stromové zobrazení oken a ovládacích prvků v systému. Další informace najdete v tématu [zobrazení oken](../debugger/windows-view.md).|
|![Tlačítko&#43; &#43; procesy Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Zobrazí stromové zobrazení procesů v systému. Další informace najdete v tématu [zobrazení procesů](../debugger/processes-view.md).|
|![Tlačítko&#43; &#43; Spy Threads](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Zobrazí stromové zobrazení vláken v systému. Další informace naleznete v tématu [zobrazení vláken](../debugger/threads-view.md).|
|![Tlačítko&#43; &#43; Spy zprávy](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Vytvoří okno pro zobrazení zpráv okna a otevře dialogové okno **Možnosti zprávy** , ve kterém můžete vybrat okno, ve kterém se budou zobrazovat zprávy, a také vybrat další možnosti. Další informace najdete v tématu [zobrazení zpráv](../debugger/messages-view.md).|
|![Tlačítko&#43; &#43; pro spuštění protokolu Spy](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Spustí protokolování zpráv a zobrazí datový proud zprávy. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem. Další informace najdete v tématu [Postup: spuštění a zastavení zobrazení protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43; &#43; – tlačítko protokolu zastavení](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Zastaví protokolování zpráv a zobrazí datový proud zprávy. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem. Další informace najdete v tématu [Postup: spuštění a zastavení zobrazení protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Tlačítko&#43; &#43; možnosti protokolu Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Zobrazí dialogové okno [Možnosti zprávy](../debugger/message-options-dialog-box.md) . Pomocí tohoto dialogového okna můžete vybrat typy oken a zpráv pro zobrazení. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem.|
|![Spy&#43; &#43; – tlačítko pro vymazání protokolu](../debugger/media/spy--_clearlog.gif "_ClearLog Spy + +")|Vymaže obsah okna aktivní **zprávy** . Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem.|
|![Tlačítko&#43; &#43; Spy najít okno](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Otevře dialogové okno [Najít okno](../debugger/find-window-dialog-box.md) , ve kterém můžete nastavit kritéria hledání oken a zobrazit vlastnosti nebo zprávy. Další informace naleznete v tématu [How to: use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|
|![Tlačítko&#43; &#43; Spy najít první okno](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Vyhledá v aktuálním zobrazení, které odpovídá oknu, procesu, vláknu nebo zprávě.|
|![Tlačítko&#43; &#43; Spy najít další okno](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Vyhledá v aktuálním zobrazení další vyhovující okno, proces, vlákno nebo zprávu. Tento ovládací prvek (a související příkaz nabídky) je k dispozici pouze v případě, že existuje platný výsledek hledání, který není jedinečný. Například při použití popisovače okna jako kritérium hledání ve stromové struktuře okna vytvoří jedinečné výsledky, protože ve stromu okna je pouze jedno okno s tímto popisovačem; v této instanci není k dispozici příkaz **Najít další** .|
|![Tlačítko&#43; &#43; Spy najít předchozí okno](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Vyhledá v aktuálním zobrazení předchozí vyhovující okno, proces, vlákno nebo zprávu. Tento ovládací prvek (a související příkaz nabídky) je k dispozici pouze v případě, že existuje platný výsledek hledání, který není jedinečný. Například při použití popisovače okna jako kritérium hledání ve stromové struktuře okna vytvoří jedinečné výsledky, protože ve stromu okna je pouze jedno okno s tímto popisovačem; v této instanci není k dispozici příkaz **Najít předchozí** .|
|![Tlačítko&#43; &#43; Průzkumníka vlastností Spy](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Zobrazí vlastnosti okna, které je vybráno v zobrazení pro systém Windows.|
|![Tlačítko&#43; &#43; aktualizace Spy](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Aktualizuje systémová zobrazení.|

## <a name="see-also"></a>Viz také:
- [Použití nástroje Spy++](../debugger/using-spy-increment.md)
- [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)
- [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)