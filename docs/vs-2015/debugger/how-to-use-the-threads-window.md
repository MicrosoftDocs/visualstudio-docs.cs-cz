---
title: 'Postupy: použití okna vláken | Dokumentace Microsoftu'
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
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 925e5ec609c07fa1ca6d703943cf3437f0f9bf84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791693"
---
# <a name="how-to-use-the-threads-window"></a>Postupy: Použití okna vláken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V **vlákna** okna, můžete prozkoumat a pracujte s vlákny v aplikaci, kterou ladíte.  
  
 **Vlákna** okno obsahuje tabulky, kde každý řádek představuje vlákno v aplikaci. Ve výchozím nastavení v tabulce jsou uvedeny všechna vlákna ve vaší aplikaci, ale můžete filtrovat seznam a zobrazit pouze vlákna, které vás zajímají. Každý sloupec obsahuje jiný typ informací. Také můžete skrýt některé sloupce. Pokud zobrazíte všechny sloupce, tyto informace se zobrazí, zleva doprava:  
  
-   Sloupec příznaku, kde lze označit vlákno, ke kterému chcete věnovat zvláštní pozornost. Informace o tom, jak označit vlákno, naleznete v tématu [jak: nastavit příznak a odstranění označení vlákna](../debugger/how-to-flag-and-unflag-threads.md).  
  
-   Aktivní vlákno sloupce, ve kterém žlutá šipka označuje aktivní vlákno. Přehled šipka označuje vlákno, kde se spuštění dostalo do ladicího programu.  
  
-   **ID** sloupec, který obsahuje identifikační číslo pro každé vlákno.  
  
-   **Spravované ID** sloupec, který obsahuje spravované identifikační čísla pro spravované vlákna.  
  
-   **Kategorie** sloupec, který rozděluje vlákna vlákna uživatelského rozhraní, obslužné rutiny volání vzdálené procedury nebo pracovní vlákna. Zvláštní kategorie identifikuje hlavního vlákna aplikace.  
  
-   **Název** sloupec, který identifikovat každé vlákno podle názvu, pokud existuje, nebo jako \<bez názvu >.  
  
-   **Umístění** sloupec, který ukazuje, kde je spuštěn podproces. Můžete rozbalit tohoto umístění zobrazíte úplného zásobníku volání pro vlákno.  
  
-   **Priority** sloupec, který bude obsahovat priority nebo priority, které systém přiřadil pro každé vlákno.  
  
-   **Maska spřažení** sloupec, který je pokročilá sloupec, který je obvykle skryta. Tento sloupec zobrazuje maska přidružení procesoru pro každé vlákno. V systému s více procesory Maska spřažení Určuje, které procesory, ve kterých lze spustit vlákno.  
  
-   **Pozastavený počet** sloupec, který obsahuje pozastavený počet. Tento počet Určuje, zda lze spustit vlákno. Vysvětlení pozastavené počet naleznete v tématu "Zmrazení a uvolnění vlákna" dále v tomto tématu.  
  
-   **Název procesu** sloupec, který obsahuje proces, ke kterému patří každé vlákno. V tomto sloupci může být užitečné při ladění více procesů, ale obvykle je skrytá.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Chcete-li zobrazit okno vlákna v režimu přerušení nebo v režimu spuštění  
  
-   Na **ladění** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **vlákna**.  
  
### <a name="to-display-or-hide-a-column"></a>Chcete-li zobrazit nebo skrýt sloupec  
  
-   Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko **sloupce**, zaškrtněte nebo zrušte název sloupce, který chcete zobrazit nebo skrýt.  
  
### <a name="to-switch-the-active-thread"></a>Chcete-li přepnout aktivní vlákno  
  
-   Proveďte některý z následujících kroků:  
  
    -   Klikněte dvakrát na libovolného vlákna.  
  
    -   Klikněte pravým tlačítkem na vlákno a klikněte na tlačítko **přepnout na vlákno**.  
  
         Žlutá šipka vedle nové aktivní vlákno. Šedé osnovy šipka označuje vlákno, kde se spuštění dostalo do ladicího programu.  
  
## <a name="grouping-and-sorting-threads"></a>Seskupování a řazení vláken  
 Při seskupování vlákna nadpis se zobrazí v tabulce pro každou skupinu. Záhlaví obsahuje popis skupiny, jako je například "Pracovní vlákna" nebo "Vlákna bez příznaku" a ovládacím prvkem strom. Vlákna člena každé skupiny se zobrazí v záhlaví skupiny. Pokud chcete skrýt člena vláken pro skupiny, můžete do ovládacího prvku stromu sbalí skupinu.  
  
 Protože seskupení má přednost před řazení, můžete seskupit podle kategorie, například vlákna a pak je můžete seřadit podle ID v jednotlivých kategoriích.  
  
#### <a name="to-sort-threads"></a>Chcete-li seřadit vláken  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou teď seřazené podle hodnoty ve sloupci.  
  
2.  Pokud chcete změnit směr řazení, klikněte znovu na stejném tlačítko.  
  
     Vlákna, které se zobrazovaly v horní části seznamu, se teď zobrazí v dolní části.  
  
#### <a name="to-group-threads"></a>Do skupiny vláken  
  
-   V **vlákna** panel nástrojů okna, klikněte na tlačítko **Seskupit podle** seznamu a potom klepněte na kritéria, které chcete seskupit vlákna podle.  
  
#### <a name="to-sort-threads-within-groups"></a>Chcete-li seřadit vláken v rámci jednotlivých skupin  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko **Seskupit podle** seznamu a potom klepněte na kritéria, které chcete seskupit vlákna tak.  
  
2.  V **vlákna** okna, klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou teď seřazené podle hodnoty ve sloupci.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Chcete-li rozbalit nebo sbalit všechny skupiny  
  
-   Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko **Rozbalit skupiny** nebo **sbalit skupiny**.  
  
## <a name="searching-for-specific-threads"></a>Vyhledání konkrétního vlákna  
 V [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], můžete vyhledat vlákna, které odpovídají zadaného řetězce. Při hledání vlákna **vlákna** okno, v okně zobrazí všechna vlákna, které odpovídají hledaný řetězec na jakémkoli sloupci. Obsahuje informace o umístění vlákna, která se zobrazí v horní části zásobníku volání v **umístění** sloupce. Ve výchozím nastavení ale úplného zásobníku volání není prohledána.  
  
#### <a name="to-search-for-specific-threads"></a>K vyhledání konkrétního vlákna  
  
-   Na panelu nástrojů v horní části **vlákna** okno, přejděte **hledání** boxu tak buď:  
  
    -   Zadejte hledaný řetězec a stiskněte klávesu ENTER.  
  
         \- nebo –  
  
    -   Klikněte na rozevírací seznam vedle položky **hledání** a vyberte hledaný řetězec předešlých hledání.  
  
-   (Volitelné) Chcete-li do hledání zahrnout úplného zásobníku volání, vyberte **zásobník volání hledání**.  
  
## <a name="freezing-and-thawing-threads"></a>Zmrazení a uvolnění vláken  
 Po ukotvení vlákno se systém nespustí provádění vlákna, i v případě, že prostředky jsou k dispozici.  
  
 V nativním kódu, můžete pozastavit nebo obnovit vlákna voláním funkce Windows `SuspendThread` a `ResumeThread` nebo funkce MFC [CWinThread::SuspendThread](http://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) a [CWinThread::ResumeThread](http://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Při volání `SuspendThread` nebo `ResumeThread`, můžete změnit *pozastavený počet*, který se objevuje v **vlákna** okna. Pokud zmrazit nebo odblokovat nativních vláken, změníte není pozastavený počet. V nativním kódu vlákno nelze spustit, pokud je roztát a má nulový počet pozastavené.  
  
 Zmrazení nebo uvolnění vlákna ve spravovaném kódu mění pozastavený počet. Ve spravovaném kódu zmrazené vlákno je pozastavené počet 1. Zmrazené vlákno v nativním kódu, nemá pozastavený počet 0, pokud vlákna se pozastavilo, tak `SuspendThread` volání.  
  
> [!NOTE]
>  Při ladění volání z nativního kódu pro spravovaný kód spravovaný kód běží ve stejné fyzické vlákno v nativním kódu, která ji zavolala. Pozastavení nebo zmrazení nativních vláken se taky zablokuje spravovaného kódu.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Chcete-li zmrazit nebo odblokovat spuštění vlákna  
  
-   Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko **zablokovat vlákna** nebo **uvolnit vlákna**.  
  
     Tato akce ovlivní pouze vlákna, které jsou vybrány v **vlákna** okna.  
  
## <a name="displaying-flagged-threads"></a>Zobrazení vlákna s příznakem  
 Můžete označit příznakem vlákna, které chcete věnovat zvláštní pozornost označením s ikonou v **vlákna** okna. Další informace najdete v tématu [jak: nastavit příznak a odstranění označení vlákna](../debugger/how-to-flag-and-unflag-threads.md). V okně vlákna můžete zobrazit všechna vlákna, nebo pouze vlákna s příznakem.  
  
#### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   V levém horním rohu klikněte na tlačítko příznak **vlákna** okna.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Zobrazení zásobníků volání vlákna a přepínání mezi snímky  
 Každé vlákno ve vícevláknovém programu, má své vlastní zásobníku volání. **Vlákna** okno poskytuje pohodlný způsob, jak zobrazit tyto balíčky.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Chcete-li zobrazit zásobník volání vlákna  
  
-   V **umístění** sloupce, klikněte na trojúhelník obrácenou vedle umístění vlákna.  
  
     Umístění se rozbalí a zobrazí zásobník volání pro vlákno.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>K zobrazení nebo sbalit zásobníky volání všech vláken  
  
-   Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko **rozbalit zásobníky volání** nebo **sbalit zásobníky volání**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md)



