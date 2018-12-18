---
title: Zobrazení zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f896650d7979365346d493c5aac06340007cbb7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784374"
---
# <a name="messages-view"></a>Zobrazení zpráv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každé okno má datové proudy přidružené zpráv. Zobrazí okno pro zobrazení zprávy tohoto datového proudu zpráv. Popisovač okna, kód zprávy a zpráva se zobrazí. Můžete vytvořit zobrazení zprávy pro vlákna nebo procesu stejně. To umožňuje zobrazit zprávy, pošle se všem oknům vlastní konkrétní proces nebo vlákno, které je zvláště užitečné pro zaznamenání inicializace zprávy okna.  
  
 Typické okno zobrazení zpráv se zobrazí pod. Mějte na paměti, že první sloupec obsahuje popisovač okna a druhý sloupec obsahuje kód zprávy (podrobně [kódy zpráv](../debugger/message-codes.md)). Dekódovaná zpráva parametry a návratové hodnoty se na pravé straně.  
  
 ![Spy&#43; &#43; zobrazení zpráv](../debugger/media/spy-messagesview.png "nástroje Spy ++ _MessagesView")  
Zobrazení zpráv Spy ++  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Otevření zobrazení zpráv pro okna, procesu nebo vlákna  
  
1.  Přesuňte fokus [zobrazení Windows](../debugger/windows-view.md), [zobrazení procesů](../debugger/processes-view.md), nebo [zobrazení vláken](../debugger/threads-view.md) okno.  
  
2.  Najít uzel pro položku, jejíž zprávy, které chcete prověřit a vyberte ji.  
  
3.  Z **Spy** nabídce zvolte **zprávy protokolu**.  
  
     [Dialogové okno možností zpráv](../debugger/message-options-dialog-box.md) otevře.  
  
4.  Vyberte požadované možnosti pro zprávu, kterou chcete zobrazit.  
  
5.  Stisknutím klávesy **OK** zahájíte protokolování zpráv.  
  
     Otevře se okno pro zobrazení zprávy a s **zprávy** nabídka se přidá na panel nástrojů nástroje Spy ++. V závislosti na vybrané možnosti, zprávy začít Streamovat do aktivního okna zobrazení zprávy.  
  
6.  Pokud máte dostatek zpráv, zvolte **zastavit protokolování** z **zprávy** nabídky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Řízení zobrazení zpráv](../debugger/how-to-control-messages-view.md)  
 Vysvětluje, jak spravovat zobrazení zpráv.  
  
 [Hledání zprávy v zobrazení zpráv](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Vysvětluje, jak najít konkrétní zprávu v zobrazení zpráv.  
  
 [Spuštění a zastavení displeje protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Vysvětluje, jak spustit a zastavit protokolování zpráv.  
  
 [Kódy zpráv](../debugger/message-codes.md)  
 Definuje kódy pro zprávy, které jsou uvedené v zobrazení zpráv.  
  
 [Zobrazení vlastností zpráv](../debugger/how-to-display-message-properties.md)  
 Jak zobrazit další informace o zprávě.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)  
 Vysvětluje, zobrazení stromu nástroje Spy ++ windows, zpráv, procesy a vlákna.  
  
 [Použití nástroje Spy++](../debugger/using-spy-increment.md)  
 Seznámíte se nástroje Spy ++, jak je možné.  
  
 [Dialogové okno možností zpráv](../debugger/message-options-dialog-box.md)  
 Slouží k výběru zprávy, které jsou uvedené v zobrazení aktivního zprávy.  
  
 [Dialogové okno pro vyhledávání zpráv](../debugger/message-search-dialog-box.md)  
 Umožňuje najít uzel pro konkrétní zprávu v zobrazení zpráv.  
  
 [Dialogové okno vlastností zpráv](../debugger/message-properties-dialog-box.md)  
 Slouží k zobrazení vlastnosti zprávy vybrána v zobrazení zpráv.  
  
 [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)  
 Obsahuje části s popisem každé nástroje Spy ++ nabídky a dialogové okno pole.



