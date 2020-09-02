---
title: Panel nástrojů Spy + + | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a96a5765c98bf8e7d1c600fbd47478a88fa7175d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153894"
---
# <a name="spy-toolbar"></a>Panel nástrojů nástroje Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Panel nástrojů se zobrazí v panelu nabídek v nástroji Spy + +. Chcete-li zobrazit nebo skrýt panel nástrojů, klikněte v nabídce **zobrazení** na příkaz **panel nástrojů**.  
  
 Na panelu nástrojů jsou k dispozici následující ovládací prvky.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
  
|Tlačítko|Efekt|  
|------------|------------|  
|![Tlačítko Spy&#43;&#43; Windows](../debugger/media/icon-spy-windows.gif "_Windows Icon_Spy + +")|Zobrazí stromové zobrazení oken a ovládacích prvků v systému. Další informace najdete v tématu [zobrazení oken](../debugger/windows-view.md).|  
|![Tlačítko Spy&#43;&#43; procesy](../debugger/media/icon-spy-processes.gif "_Processes Icon_Spy + +")|Zobrazí stromové zobrazení procesů v systému. Další informace najdete v tématu [zobrazení procesů](../debugger/processes-view.md).|  
|![Tlačítko pro vlákna&#43;&#43; Spy](../debugger/media/icon-spy-threads.gif "_Threads Icon_Spy + +")|Zobrazí stromové zobrazení vláken v systému. Další informace naleznete v tématu [zobrazení vláken](../debugger/threads-view.md).|  
|![Tlačítko Spy&#43;&#43; zprávy](../debugger/media/icon-spy-messages.gif "_Messages Icon_Spy + +")|Vytvoří okno pro zobrazení zpráv okna a otevře dialogové okno **Možnosti zprávy** , ve kterém můžete vybrat okno, ve kterém se budou zobrazovat zprávy, a také vybrat další možnosti. Další informace najdete v tématu [zobrazení zpráv](../debugger/messages-view.md).|  
|![Tlačítko pro spuštění protokolu Spy&#43;&#43; ](../debugger/media/icon-spy-startlog.gif "_StartLog Icon_Spy + +")|Spustí protokolování zpráv a zobrazí datový proud zprávy. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem. Další informace najdete v tématu [Postup: spuštění a zastavení zobrazení protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43;&#43; – tlačítko zastavit protokol](../debugger/media/icon-spy-stoplog.gif "_StopLog Icon_Spy + +")|Zastaví protokolování zpráv a zobrazí datový proud zprávy. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem. Další informace najdete v tématu [Postup: spuštění a zastavení zobrazení protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Tlačítko Možnosti protokolu pro Spy&#43;&#43; ](../debugger/media/icon-spy-logoptions.gif "_LogOptions Icon_Spy + +")|Zobrazí dialogové okno [Možnosti zprávy](../debugger/message-options-dialog-box.md) . Pomocí tohoto dialogového okna můžete vybrat typy oken a zpráv pro zobrazení. Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem.|  
|![Spy&#43;&#43; – tlačítko Vymazat protokol](../debugger/media/spy-clearlog.gif "_ClearLog nástroje Spy + +")|Vymaže obsah okna aktivní **zprávy** . Tento ovládací prvek je k dispozici pouze v případě, že je okno **zprávy** aktivním oknem.|  
|![Tlačítko Spy&#43;&#43; najít okno](../debugger/media/icon-spy-findwindow.gif "_FindWindow Icon_Spy + +")|Otevře dialogové okno [Najít okno](../debugger/find-window-dialog-box.md) , ve kterém můžete nastavit kritéria hledání oken a zobrazit vlastnosti nebo zprávy. Další informace naleznete v tématu [How to: use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|  
|![Tlačítko Spy&#43;&#43; najít první okno](../debugger/media/icon-spy-window.gif "_Window Icon_Spy + +")|Vyhledá v aktuálním zobrazení, které odpovídá oknu, procesu, vláknu nebo zprávě.|  
|![Tlačítko Spy&#43;&#43; najít další okno](../debugger/media/icon-spy-nextwindow.gif "_NextWindow Icon_Spy + +")|Vyhledá v aktuálním zobrazení další vyhovující okno, proces, vlákno nebo zprávu. Tento ovládací prvek (a související příkaz nabídky) je k dispozici pouze v případě, že existuje platný výsledek hledání, který není jedinečný. Například při použití popisovače okna jako kritérium hledání ve stromové struktuře okna vytvoří jedinečné výsledky, protože ve stromu okna je pouze jedno okno s tímto popisovačem; v této instanci není k dispozici příkaz **Najít další** .|  
|![Tlačítko Spy&#43;&#43; najít předchozí okno](../debugger/media/icon-spy-prevwindow.gif "_PrevWindow Icon_Spy + +")|Vyhledá v aktuálním zobrazení předchozí vyhovující okno, proces, vlákno nebo zprávu. Tento ovládací prvek (a související příkaz nabídky) je k dispozici pouze v případě, že existuje platný výsledek hledání, který není jedinečný. Například při použití popisovače okna jako kritérium hledání ve stromové struktuře okna vytvoří jedinečné výsledky, protože ve stromu okna je pouze jedno okno s tímto popisovačem; v této instanci není k dispozici příkaz **Najít předchozí** .|  
|![Tlačítko Průzkumníka vlastností&#43;&#43; nástroje Spy](../debugger/media/icon-spy-propexp.gif "_PropExp Icon_Spy + +")|Zobrazí vlastnosti okna, které je vybráno v zobrazení pro systém Windows.|  
|![Tlačítko Spy&#43;&#43; Refresh](../debugger/media/icon-spy-refresh.gif "_Refresh Icon_Spy + +")|Aktualizuje systémová zobrazení.|  
  
## <a name="see-also"></a>Viz také  
 [Pomocí nástroje Spy + +](../debugger/using-spy-increment.md)   
 [Zobrazení nástroje Spy + +](../debugger/spy-increment-views.md)   
 [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)
