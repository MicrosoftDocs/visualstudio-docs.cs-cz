---
title: Zobrazení vlákna GPU v ladicím programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4f4577fc7e1a26481ff4ab5aa94888cf5668adf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825335"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Postupy: Použití okna vláken GPU
V okně vlákna GPU můžete prozkoumat a práce s vlákny, která běží na grafickém procesoru v aplikaci, kterou ladíte. Další informace o aplikacích, které běží na GPU, naleznete v tématu [přehled modelu C++ AMP](/cpp/parallel/amp/cpp-amp-overview).  
  
 Okna vláken GPU obsahuje tabulku, ve kterém každý řádek představuje sadu vlákna GPU, které mají stejné hodnoty ve všech sloupců. Můžete řadit, změnit pořadí, odebrat a seskupit položky, které jsou ve sloupcích. Můžete označit příznakem, odznačit, ukotvit (Pozastavit) a uvolnit vlákna (pokračovat) z okna vláken GPU. Tyto sloupce se zobrazí v okně vlákna GPU:  
  
- Sloupec příznaku, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.  
  
- Aktuální vlákno sloupec, ve kterém žlutá šipka označuje aktuální vlákno.  
  
- **Počet vláken** sloupec, který zobrazuje počet vláken ve stejném umístění.  
  
- **Řádku** sloupec, který zobrazuje řádek kódu, kde je každá skupina vlákna umístěna.  
  
- **Adresu** sloupec, který zobrazuje adresu instrukce, kde je každá skupina vlákna umístěna. Ve výchozím nastavení je tento sloupec skrytý.  
  
- **Umístění** sloupec, který je umístěním ve zdrojovém kódu.  
  
- **Stav** sloupec, který ukazuje, zda vlákno je aktivní, zablokování, není spuštěné nebo dokončení.  
  
- **Dlaždici** sloupec, který zobrazuje indexu dlaždice pro podprocesy v řádku.  
  
  Záhlaví tabulky zobrazí pole a vlákno se zobrazí.  
  
  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Chcete-li zobrazit okna vláken GPU  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.  
  
2.  V **stránky vlastností** okna pro projekt, v části **vlastnosti konfigurace**, zvolte **ladění**.  
  
3.  V **ladicí program ke spuštění** seznamu vyberte **místní ladicí program Windows**. V **typ ladicího programu** seznamu vyberte **pouze GPU**. Musíte zvolit tento ladicí program na přerušení na zarážkách v kódu, který běží na GPU.  
  
4.  Zvolte **OK** tlačítko.  
  
5.  Nastavte zarážku v kódu GPU.  
  
6.  V panelu nabídky zvolte **ladění**, **spustit ladění**. Vyčkat, než aplikace k dosažení zarážky.  
  
7.  Jeden řádek nabídek, zvolte **ladění**, **Windows**, **vlákna GPU**.  
  
### <a name="to-switch-to-a-different-thread"></a>Chcete-li přepnout do jiného vlákna  
  
-   Poklepejte na sloupec. (Klávesnice: Vyberte řádek a zvolte Enter.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Chcete-li zobrazit konkrétní pole a vlákno  
  
1.  Zvolte **rozbalte vlákna přepínání** tlačítka v okně vlákna GPU.  
  
2.  Zadejte hodnoty pole a vlákno v textových polích.  
  
3.  Klikněte na tlačítko se šipkou na něj.  
  
### <a name="to-display-or-hide-a-column"></a>Chcete-li zobrazit nebo skrýt sloupec  
  
-   Otevřete místní nabídku pro okno vlákna GPU, zvolte **sloupce**a pak zvolte sloupec, který chcete zobrazit nebo skrýt.  
  
### <a name="to-sort-by-a-column"></a>Seřadit podle sloupce  
  
-   Vyberte záhlaví sloupce.  
  
### <a name="to-group-threads"></a>Do skupiny vláken  
  
-   Otevřete místní nabídku pro okno vlákna GPU, zvolte **Group**a pak zvolte jeden z názvů sloupců, které jsou zobrazeny. Zvolte **žádný** oddělit vlákna.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Chcete-li zmrazit nebo odblokovat řádek vláken  
  
-   Otevřete místní nabídku pro řádek a zvolte **ukotvit** nebo **uvolnit**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Chcete-li označit nebo zrušit označení příznakem řádek vlákna  
  
-   Vyberte sloupec příznaku pro vlákno, nebo otevřete místní nabídku pro vlákno a zvolte **příznak** nebo **Unflag**.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   Klikněte na tlačítko příznak v okně vlákna GPU.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Návod: Ladění aplikace C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)