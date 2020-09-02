---
title: Zobrazení zpráv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157496"
---
# <a name="messages-view"></a>Zobrazení zpráv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každé okno má přidružený datový proud zprávy. Tento datový proud zpráv se zobrazí v okně zobrazení zpráv. Zobrazí se popisovač okna, kód zprávy a zpráva. Můžete také vytvořit zobrazení zpráv pro vlákno nebo proces. To vám umožní zobrazit zprávy odesílané do všech oken vlastněných konkrétním procesem nebo vláknem, což je zvláště užitečné při zachytávání inicializačních zpráv oken.  
  
 Zobrazí se okno typické zobrazení zpráv. Všimněte si, že první sloupec obsahuje popisovač okna a druhý sloupec obsahuje kód zprávy (vysvětlení najdete v části [kódy zpráv](../debugger/message-codes.md)). Dekódovatelné parametry zprávy a návratové hodnoty jsou napravo.  
  
 ![Zobrazení zpráv Spy&#43;&#43; ](../debugger/media/spy-messagesview.png "_MessagesView nástroje Spy + +")  
Zobrazení zpráv Spy + +  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Otevření zobrazení zpráv pro okno, proces nebo vlákno  
  
1. Přesuňte fokus na zobrazení [systému Windows](../debugger/windows-view.md), [procesy](../debugger/processes-view.md)nebo okno [zobrazení vláken](../debugger/threads-view.md) .  
  
2. Vyhledejte uzel pro položku, jejíž zprávy chcete prošetřit, a vyberte ji.  
  
3. V nabídce **Spy** vyberte **protokolové zprávy**.  
  
     Otevře se [dialogové okno Možnosti zprávy](../debugger/message-options-dialog-box.md) .  
  
4. Vyberte možnosti pro zprávu, kterou chcete zobrazit.  
  
5. Kliknutím na tlačítko **OK** zahajte protokolování zpráv.  
  
     Otevře se okno zobrazení zprávy a do panelu nástrojů Spy + + se přidá nabídka **zprávy** . V závislosti na vybraných možnostech zprávy zahájí streamování do okna zobrazení aktivní zprávy.  
  
6. Máte-li dostatek zpráv, v nabídce **zprávy** vyberte možnost **zastavit protokolování** .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Řízení zobrazení zpráv](../debugger/how-to-control-messages-view.md)  
 Vysvětluje, jak spravovat zobrazení zpráv.  
  
 [Hledání zprávy v zobrazení zpráv](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Vysvětluje, jak najít konkrétní zprávu v zobrazení zprávy.  
  
 [Spuštění a zastavení zobrazení protokolu zpráv](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Vysvětluje, jak spustit a zastavit protokolování zpráv.  
  
 [Kódy zpráv](../debugger/message-codes.md)  
 Definuje kódy pro zprávy uvedené v zobrazení zprávy.  
  
 [Zobrazení vlastností zprávy](../debugger/how-to-display-message-properties.md)  
 Jak zobrazit další informace o zprávě  
  
## <a name="related-sections"></a>Související oddíly  
 [Zobrazení nástroje Spy++](../debugger/spy-increment-views.md)  
 Vysvětluje zobrazení stromové struktury nástroje Spy + + pro Windows, zprávy, procesy a vlákna.  
  
 [Použití nástroje Spy++](../debugger/using-spy-increment.md)  
 Zavádí nástroj Spy + + a vysvětluje, jak ho lze použít.  
  
 [Dialogové okno možností zpráv](../debugger/message-options-dialog-box.md)  
 Slouží k výběru zpráv, které jsou uvedeny v zobrazení aktivní zprávy.  
  
 [Dialogové okno hledání zpráv](../debugger/message-search-dialog-box.md)  
 Slouží k vyhledání uzlu pro určitou zprávu v zobrazení zprávy.  
  
 [Dialogové okno vlastností zpráv](../debugger/message-properties-dialog-box.md)  
 Slouží k zobrazení vlastností zprávy vybrané v zobrazení zprávy.  
  
 [Referenční dokumentace nástroje Spy++](../debugger/spy-increment-reference.md)  
 Obsahuje oddíly popisující jednotlivé nabídky a dialogová okna nástroje Spy + +.
