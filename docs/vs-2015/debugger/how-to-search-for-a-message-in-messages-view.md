---
title: 'Postupy: hledání zprávy v zobrazení zpráv | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c89a763389abe364fe70166e63b41f932581837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783935"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Postupy: Hledání zprávy v zobrazení zpráv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Konkrétní zprávu můžete v zobrazení zprávy vyhledat pomocí jejího popisovače, typu nebo ID zprávy jako kritéria vyhledávání. Kterákoli z nich, nebo kombinace, budou platná vyhledávací kritéria. Lze také zadat počáteční směr hledání. Pole v dialogovém okně jsou předem načtena s atributy aktuálně vybrané zprávy.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Hledání zprávy v zobrazení zpráv  
  
1. Uspořádejte okna tak, aby se zobrazilo okno Spy + + a [zobrazení aktivní zprávy](../debugger/messages-view.md) .  
  
2. V nabídce **Hledat** vyberte možnost **najít zprávu**.  
  
    Otevře se [dialogové okno hledání zpráv](../debugger/message-search-dialog-box.md) .  
  
3. Přetáhněte **Nástroj hledání** přes požadované okno. Při přetahování nástroje se v dialogovém okně **hledání zprávy** zobrazí podrobnosti o vybraném okně.  
  
    ani  
  
    Pokud máte popisovač okna, jehož zprávy chcete prošetřit, zadejte ho do textového pole **popisovač** .  
  
    ani  
  
    Pokud znáte typ nebo ID zprávy, které chcete, vyberte je v rozevíracích nabídkách **typ** a **zpráva** a vymažte textové pole **popisovač** .  
  
4. Vymažte všechna pole, pro která nechcete zadávat hodnoty.  
  
   > [!TIP]
   > Pokud chcete omezit přehlednost obrazovky, vyberte možnost **Skrýt Spy** . Tato možnost zachová hlavní okno nástroje Spy + + a v horní části ostatních aplikací se zobrazí pouze dialogové okno **Najít okno** . Po kliknutí na tlačítko **OK** nebo **Zrušit**dojde k obnovení hlavního okna nástroje Spy + +, nebo když zrušíte zaškrtnutí políčka **Skrýt Spy + +** .  
  
5. Pro počáteční směr hledání vyberte **nahoru** nebo **dolů** .  
  
6. Klikněte na **OK**.  
  
   Pokud se najde shodná zpráva, zvýrazní se v okně zobrazení zpráv. Viz [zobrazení zprávy](../debugger/messages-view.md).
