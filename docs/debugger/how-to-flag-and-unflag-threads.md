---
title: 'Postupy: označení a odstranění označení vlákna | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d26c87867e071b7dafce80d95e4bc46cb88bb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891372"
---
# <a name="how-to-flag-and-unflag-threads"></a>Postupy: Označení a odstranění označení vlákna
Můžete označit příznakem vlákna, které chcete věnovat zvláštní pozornost označením s ikonou v **vlákna**, **paralelní zásobníky** (zobrazení vláken), **paralelní sledování**a  **Vlákna GPU** systému windows. Tato ikona vám může pomoct a ostatní vlákna s příznakem odlišili od ostatních vláken.  
  
Vlákna s příznaky také přijímat zvláštní zacházení v **vlákna** seznamu **umístění ladění** nástrojů a v dalších vícevláknové ladění systému windows. Můžete zobrazit všechna vlákna nebo pouze vlákna s příznakem v **vlákna** seznamu nebo v jiných oknech.
  
### <a name="to-flag-or-unflag-a-thread"></a>Chcete-li označit nebo zrušit označení vlákna 
  
- V **vlákna** nebo **paralelní sledování** okně Najít vlákno, které vás zajímají a kliknutím na ikonu příznaku zaškrtněte nebo zrušte příznak. 
- V **paralelní zásobníky** okna, klikněte pravým tlačítkem na vlákno nebo skupina vláken a vyberte **příznak / <thread>**  nebo **Unflag / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Chcete-li odznačit všechna vlákna  
  
-   V **vlákna** okna, klikněte pravým tlačítkem na libovolného vlákna a pak klikněte na **odznačit všechna vlákna**.
-   V **paralelní sledování** okna, vyberte všechny vlákna označená příznakem, klikněte pravým tlačítkem a vyberte **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   Zvolte **zobrazit vlákna pouze s příznakem** tlačítko v jednom z vícevláknové ladění systému windows.  
  
### <a name="to-flag-just-my-code"></a>Chcete-li označit jen můj kód  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, klikněte na ikonu vlajky.  
  
2.  V rozevíracím seznamu, klikněte na tlačítko **příznak funkce pouze můj kód**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>K nastavení příznaku vláken, které jsou spojeny s vybrané moduly  
  
1.  Na panelu nástrojů **vlákna** okna, klikněte na ikonu vlajky.  
  
2.  V rozevíracím seznamu, klikněte na tlačítko **volba vlastního modulu příznaků**.  
  
3.  V **vyberte moduly** dialogového okna, vyberte moduly, které chcete.  
  
4.  (Volitelné) V **hledání** zadejte řetězec k vyhledání konkrétních modulů.  
  
5.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Návod: Ladění vícevláknové aplikace pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md)