---
title: Nastavení sledování u proměnných v paralelních vláken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9381479fdfa3d64f3504e947f49411b99d53e2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857949"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Nastavení sledování u proměnných v paralelních vláken v sadě Visual Studio
V okně paralelního sledování můžete najednou zobrazit hodnoty, které obsahuje jeden výraz ve více vláknech. Každý řádek představuje vlákno, na kterém běží v aplikaci však vlákno může být reprezentován více řádků. Přesněji řečeno každý řádek představuje volání funkce, jejíž podpis funkce odpovídá funkci na aktuální rámec zásobníku. Můžete řadit, změnit pořadí, odebrat a seskupit položky, které jsou ve sloupcích. Můžete označit příznakem, odznačit, ukotvit (Pozastavit) a uvolnit vlákna (pokračovat). Tyto sloupce se zobrazí v **paralelní sledování** okno:  
  
- Sloupec příznaku, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.  
  
- Aktuální vlákno sloupce, ve kterém žlutá šipka označuje aktuální vlákno (zelená šipka s vlnitým ocáskem znamená, že mimo aktuální vlákno má aktuální kontext ladicího programu).  
  
- Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úloh a vlákna.  
  
  > [!TIP]
  >  Pro informace o úkolu zobrazované v **paralelní sledování** okna, je nutné nejprve otevřít **úloh** okna.  
  
- Prázdnou *Přidat kukátko* sloupce, ve kterých můžete zadat výrazy, které chcete sledovat.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Chcete-li zobrazit okno paralelního sledování  
  
1.  Nastavte zarážku v kódu.  
  
2.  V panelu nabídky zvolte **ladění**, **spustit ladění**. Vyčkat, než aplikace k dosažení zarážky.  
  
3.  V panelu nabídky zvolte **ladění**, **Windows**, **paralelní sledování**a klikněte na tlačítko okna kukátka. Můžete otevřít až čtyři windows.  
  
### <a name="to-add-a-watch-expression"></a>Přidání výrazu kukátka  
  
-   Vyberte jednu z prázdnou *Přidat kukátko* sloupce a pak zadejte výrazu.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Chcete-li označit nebo zrušit označení vlákna  
  
-   Vyberte sloupec příznaku pro řádek (první sloupec), nebo otevřete místní nabídku pro vlákno a zvolte **příznak** nebo **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   Zvolte **zobrazit pouze označená příznakem** tlačítko v levém horním rohu **paralelní sledování** okna.  
  
### <a name="to-switch-to-another-thread"></a>Chcete-li přepnout do jiného vlákna  
  
-   Poklepejte na sloupec aktuální vlákno (druhý sloupec). (Klávesnice: Vyberte řádek, a stiskněte klávesu Enter.)  
  
### <a name="to-sort-a-column"></a>Chcete-li seřadit sloupec  
  
-   Vyberte záhlaví sloupce.  
  
### <a name="to-group-threads"></a>Do skupiny vláken  
  
-   Otevřete místní nabídku pro okno paralelního sledování, zvolte **Group**a pak zvolte položku odpovídající podnabídky.  
  
### <a name="to-freeze-or-thaw-threads"></a>Chcete-li zmrazit nebo odblokovat vlákna  
  
-   Otevřete místní nabídku pro řádek a zvolte **ukotvit** nebo **uvolnit**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Export dat v okně paralelního sledování  
  
-   Zvolte **otevřít v aplikaci Excel** tlačítko a pak zvolte **otevřít v aplikaci Excel** nebo **Export do souboru CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Chcete-li filtrovat podle logického výrazu  
  
-   Zadejte logický výraz v **filtrovat podle logického výrazu** pole. Ladicí program vyhodnotí výraz pro každý kontext vlákna. Pouze řádky, kde je hodnota `true` jsou zobrazeny.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: použití okna vláken GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Návod: Ladění aplikace C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)