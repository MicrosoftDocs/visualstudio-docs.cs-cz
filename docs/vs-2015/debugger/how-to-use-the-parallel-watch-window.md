---
title: 'Postupy: použití okna paralelního sledování | Dokumentace Microsoftu'
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
manager: ghogen
ms.openlocfilehash: 43783ad2b7d0f08aace55ff3b974d64301a38db2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753130"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Postupy: Použití okna paralelního sledování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V okně paralelního sledování můžete najednou zobrazit hodnoty, které obsahuje jeden výraz ve více vláknech. Každý řádek představuje vlákno, na kterém běží v aplikaci však vlákno může být reprezentován více řádků. Přesněji řečeno každý řádek představuje volání funkce, jejíž podpis funkce odpovídá funkci na aktuální rámec zásobníku. Můžete řadit, změnit pořadí, odebrat a seskupit položky, které jsou ve sloupcích. Můžete označit příznakem, odznačit, ukotvit (Pozastavit) a uvolnit vlákna (pokračovat). Tyto sloupce se zobrazí v **paralelní sledování** okno:  
  
- Sloupec příznaku, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.  
  
- Sloupec rámce, ve kterém šipka označuje vybraný rámec.  
  
- Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úloh a vlákna.  
  
  > [!TIP]
  >  Je nutné otevřít **paralelních úkolů** okno, aby obsahovalo informace o úkolu v **paralelní sledování** okna.  
  
- **\<Přidat kukátko >** sloupec, ve kterém můžete zadat výrazy, které chcete sledovat.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Chcete-li zobrazit okno paralelního sledování  
  
1.  Nastavte zarážku v kódu.  
  
2.  V panelu nabídky zvolte **ladění**, **spustit ladění**. Vyčkat, než aplikace k dosažení zarážky.  
  
3.  V panelu nabídky zvolte **ladění**, **Windows**, **paralelní sledování**a klikněte na tlačítko okna kukátka. Můžete otevřít až čtyři windows.  
  
### <a name="to-add-a-watch-expression"></a>Přidání výrazu kukátka  
  
-   Vyberte  **\<Přidat kukátko >** a pak zadejte výrazu.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Chcete-li označit nebo zrušit označení vlákna  
  
-   Vyberte sloupec příznaku pro řádek, nebo otevřete místní nabídku pro vlákno a zvolte **příznak** nebo **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   V levém horním rohu klikněte na tlačítko Zobrazit pouze s příznakem **paralelní sledování** okna.  
  
### <a name="to-switch-frames"></a>Chcete-li přepnout snímků  
  
-   Poklepejte na sloupec rámce. (Klávesnice: Vyberte řádek, a stiskněte klávesu Enter.)  
  
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
 [Návod: Ladění aplikace C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



