---
title: 'Postupy: použití okna paralelního sledování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697495"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Postupy: Použití okna paralelního sledování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V paralelním okno Kukátko lze současně zobrazit hodnoty, které jeden výraz obsahuje ve více vláknech. Každý řádek představuje vlákno, které běží v aplikaci, ale vlákno může být reprezentované ve více řádcích. Přesněji řečeno, každý řádek představuje volání funkce, jejíž signatura funkce odpovídá funkci v aktuálním bloku zásobníku. Položky, které jsou ve sloupcích, můžete řadit, přeřadit, odebírat a seskupovat. Vlákna můžete označit, zrušit jeho příznak, zablokovat (pozastavit) a uvolnit (pokračovat). V okně **paralelní sledování** se zobrazí následující sloupce:  
  
- Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.  
  
- Sloupec rámce, ve kterém šipka indikuje vybraný snímek.  
  
- Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úlohu a vlákno.  
  
  > [!TIP]
  > Chcete-li zobrazit informace o úkolu v okně **paralelní kukátko** , je nutné otevřít okno **Paralelní úlohy** .  
  
- **\<Add Watch>** Sloupec, ve kterém můžete zadat výrazy ke sledování.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Zobrazení paralelního okno Kukátko  
  
1. Nastavte zarážku v kódu.  
  
2. Na řádku nabídek klikněte na položku **ladit**, **Spustit ladění**. Počkejte, než aplikace dorazí na zarážku.  
  
3. V panelu nabídek zvolte položku **ladit**, **okna**, **paralelní kukátko**a pak zvolte okno kukátka. Můžete otevřít až čtyři okna.  
  
### <a name="to-add-a-watch-expression"></a>Přidání výrazu kukátka  
  
- Vyberte **\<Add Watch>** a zadejte výraz kukátka.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Označení nebo odoznačení vlákna vláknem  
  
- Vyberte sloupec příznak pro řádek nebo otevřete místní nabídku pro vlákno a zvolte **příznak** nebo zrušit **označení**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
- V levém horním rohu okna **paralelního sledování** vyberte tlačítko Zobrazit pouze s příznakem.  
  
### <a name="to-switch-frames"></a>Přepnutí snímků  
  
- Dvakrát klikněte na sloupec rámce. (Klávesnice: vyberte řádek a stiskněte klávesu ENTER.)  
  
### <a name="to-sort-a-column"></a>Postup řazení sloupce  
  
- Vyberte záhlaví sloupce.  
  
### <a name="to-group-threads"></a>Seskupení vláken  
  
- Otevřete místní nabídku pro paralelní okno Kukátko, zvolte možnost **Seskupit podle**a pak zvolte příslušnou položku v podnabídce.  
  
### <a name="to-freeze-or-thaw-threads"></a>Zablokování nebo odmrazení vláken  
  
- Otevřete místní nabídku řádku a vyberte možnost **ukotvit** nebo **rozmrazit**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Export dat v paralelním okno Kukátko  
  
- Klikněte na tlačítko **otevřít v aplikaci Excel** a pak zvolte možnost **otevřít v aplikaci Excel** nebo **exportovat do sdíleného svazku clusteru**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Filtrování podle logického výrazu  
  
- Zadejte logický výraz do pole **filtrovat podle logického výrazu** . Ladicí program vyhodnotí výraz pro každý kontext vlákna. Zobrazí se pouze řádky, ve kterých je hodnota `true` zobrazena.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Návod: ladění aplikace C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
