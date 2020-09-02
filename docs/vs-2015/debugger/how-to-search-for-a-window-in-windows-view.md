---
title: 'Postupy: hledání okna v zobrazení Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9d7a64191db82d5fb0b82518d3db1cf1eb1e0ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858771"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Postupy: Hledání okna v zobrazení oken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyhledat konkrétní okno v zobrazení Windows pomocí jeho popisovače, titulku, třídy nebo kombinace jeho titulku a třídy jako kritéria hledání. Můžete také zadat počáteční směr hledání. Pole v dialogovém okně zobrazí atributy vybraného okna ve stromu okna.  
  
 Začněte se stromovou strukturou rozbalenou na druhou úroveň (všechny systémy Windows, které jsou podřízené počítači), abyste mohli identifikovat okna na úrovni počítače podle názvu a názvu třídy. Po výběru okna na úrovni plochy můžete tuto úroveň rozbalit a najít tak konkrétní podřízené okno.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Hledání okna v zobrazení Windows  
  
1. Uspořádejte okna tak, aby se zobrazila okna Spy + +, [Windows View](../debugger/windows-view.md) a cílové okno.  
  
2. V nabídce **Hledat** vyberte možnost **Najít okno**.  
  
     Otevře se [dialogové okno hledání okna](../debugger/window-search-dialog-box.md) .  
  
    > [!TIP]
    > Pokud chcete omezit přehlednost obrazovky, vyberte možnost **Skrýt Spy** . Tato možnost skrývá hlavní okno nástroje Spy + + a v horní části ostatních aplikací zůstane viditelné pouze dialogové okno pro **hledání okna** . Po kliknutí na tlačítko **OK** nebo **Zrušit**dojde k obnovení hlavního okna nástroje Spy + +, nebo když zrušíte zaškrtnutí políčka **Skrýt Spy + +** .  
  
3. Přetáhněte **Nástroj hledání** přes cílové okno. Při přetahování nástroje se v dialogovém okně **hledání okna** zobrazí podrobnosti o vybraném okně.  
  
     ani  
  
     Pokud znáte popisovač okna, které chcete (například z ladicího programu), můžete ho zadat do pole **popisovač** .  
  
     ani  
  
     Pokud znáte titulek nebo třídu požadovaného okna, můžete je zadat do textových polí **Caption** a **Class** a vymazat textové pole **popisovač** .  
  
4. Pro počáteční směr hledání vyberte **nahoru** nebo **dolů** .  
  
5. Klikněte na **OK**.  
  
     Pokud je nalezeno párové okno, je zvýrazněno v okně [zobrazení systému Windows](../debugger/windows-view.md) .
