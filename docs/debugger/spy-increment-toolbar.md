---
title: Panel nástrojů nástroje Spy ++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f90c9f249ea0091d7cd5b899ffcd9b7cdadc5a7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477378"
---
# <a name="spy-toolbar"></a>Panel nástrojů nástroje Spy++
V panelu nabídek v nástroji Spy ++ zobrazí panel nástrojů. K zobrazení nebo skrytí panelu nástrojů na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
 Ovládací prvky jsou k dispozici na panelu nástrojů.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
  
|Tlačítko|Efekt|  
|------------|------------|  
|![Spy&#43; &#43; Windows tlačítko](../debugger/media/icon_spy--_windows.gif "Icon_Spy ++ _Windows")|Zobrazí stromové zobrazení systému windows a ovládací prvky v systému. Další informace najdete v tématu [zobrazení oken](../debugger/windows-view.md).|  
|![Spy&#43; &#43; zpracovává tlačítko](../debugger/media/icon_spy--_processes.gif "Icon_Spy ++ _Processes")|Zobrazuje stromovou strukturu procesů, které jsou v systému. Další informace najdete v tématu [zobrazení procesů](../debugger/processes-view.md).|  
|![Spy&#43; &#43; vláken tlačítko](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Zobrazí stromové zobrazení vláken v systému. Další informace najdete v tématu [zobrazení vláken](../debugger/threads-view.md).|  
|![Spy&#43; &#43; zprávy tlačítko](../debugger/media/icon_spy--_messages.gif "Icon_Spy ++ _Messages")|Okno pro zobrazení oken zpráv vytvoří a otevře **možnosti zprávy** pole, ve kterém můžete vybrat okna, jejichž zprávy se zobrazí a také zvolit další možnosti. Další informace najdete v tématu [zobrazení zpráv](../debugger/messages-view.md).|  
|![Spy&#43; &#43; protokolu tlačítko Start](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Spustí protokolování zpráv a zobrazí datového proudu zpráv. Tento ovládací prvek je k dispozici pouze tehdy, když **zprávy** okno je aktivní okno. Další informace najdete v tématu [postupy: spuštění a zastavení displeje protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; zastavit tlačítko](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy ++ _StopLog")|Protokolování a zobrazení datového proudu zpráv, zpráv se zastaví. Tento ovládací prvek je k dispozici pouze tehdy, když **zprávy** okno je aktivní okno. Další informace najdete v tématu [postupy: spuštění a zastavení displeje protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; protokolu tlačítko Možnosti můžete](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy ++ _LogOptions")|Zobrazí [možnosti zprávy](../debugger/message-options-dialog-box.md) dialogové okno. Tento dialog a vyberte windows zprávy typy pro zobrazení. Tento ovládací prvek je k dispozici pouze tehdy, když **zprávy** okno je aktivní okno.|  
|![Spy&#43; &#43; protokolu tlačítko Vymazat](../debugger/media/spy--_clearlog.gif "nástroje Spy ++ _ClearLog")|Vymaže obsah aktivní **zprávy** okno. Tento ovládací prvek je k dispozici pouze tehdy, když **zprávy** okno je aktivní okno.|  
|![Spy&#43; &#43; najít tlačítko okno](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy ++ _FindWindow")|Otevře se [najít okno](../debugger/find-window-dialog-box.md) dialogové okno, která vám umožní nastavit kritéria vyhledávání okno a zobrazit vlastnosti nebo zprávy. Další informace najdete v tématu [postupy: používání vyhledávacího nástroje](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; najít první okno tlačítko](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Vyhledá aktuální zobrazení pro odpovídající okno, proces, vlákno nebo zprávy.|  
|![Spy&#43; &#43; najít tlačítko Další okno](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Vyhledá aktuální zobrazení pro další odpovídající okno, proces, vlákno nebo zprávy. Tento ovládací prvek (a související nabídky příkaz) je k dispozici jenom v případě, že je platný vyhledávací výsledek, který není jedinečný. Například pokud použijete jako kritérium hledání ve stromové struktuře okno popisovač okna, vytváří jedinečný výsledky, protože v okně stromové struktury, která má tento popisovač; je pouze jeden interval v tomto případě **najít další** není k dispozici.|  
|![Spy&#43; &#43; najít předchozí okno tlačítko](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Vyhledá aktuální zobrazení předchozího odpovídající okna, proces, vlákno nebo zprávy. Tento ovládací prvek (a související nabídky příkaz) je k dispozici jenom v případě, že je platný vyhledávací výsledek, který není jedinečný. Například pokud použijete jako kritérium hledání ve stromové struktuře okno popisovač okna, vytváří jedinečný výsledky, protože v okně stromové struktury, která má tento popisovač; je pouze jeden interval v tomto případě **najít předchozí** není k dispozici.|  
|![Spy&#43; &#43; tlačítko Průzkumníku vlastnost](../debugger/media/icon_spy--_propexp.gif "Icon_Spy ++ _PropExp")|Zobrazí vlastnosti okna, který je vybraný v zobrazení oken.|  
|![Spy&#43; &#43; tlačítko Aktualizovat](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Aktualizuje zobrazení systému.|  
  
## <a name="see-also"></a>Viz také  
 [Použití nástroje Spy ++](../debugger/using-spy-increment.md)   
 [Zobrazení nástroje Spy ++](../debugger/spy-increment-views.md)   
 [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)