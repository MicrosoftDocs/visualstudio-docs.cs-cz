---
title: Zobrazit vlákna v ladicím programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/29/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 764eb46fb387e1a007362b02a0f62cf478c771fe
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066220"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window"></a>Zobrazit vlákna v ladicím programu sady Visual Studio pomocí okna vlákna
V **vlákna** okna, můžete prozkoumat a pracujte s vlákny v aplikaci, kterou ladíte. Podrobné pokyny o tom, jak používat **vlákna** okna, naleznete v tématu [návod: ladění pomocí okna vlákna](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Použití okna vláken 
 **Vlákna** okno obsahuje tabulky, kde každý řádek popisuje samostatného vlákna ve vaší aplikaci. Ve výchozím nastavení v tabulce jsou uvedeny všechna vlákna ve vaší aplikaci, ale můžete filtrovat seznam a zobrazit pouze vlákna, které vás zajímají. Každý sloupec popisuje různé typu informací. Také můžete skrýt některé sloupce. Pokud zobrazíte všechny sloupce, tyto sloupce se zobrazí, zleva doprava:  
  
- **Příznak**: V tomto sloupci bez popisku, můžete označit vlákno, ke kterému chcete věnovat zvláštní pozornost. Informace o tom, jak označit vlákno, naleznete v tématu [jak: Příznak a odstranění označení vlákna](../debugger/how-to-flag-and-unflag-threads.md).  
  
- **Aktuální vlákno**: V tomto sloupci bez popisku, žlutá šipka označuje aktuální vlákno. Přehled šipka označuje aktuální kontext ladicího programu pro vlákna je neaktuální.
  
- **ID**: Zobrazí identifikační číslo pro každé vlákno.  
  
- **ID spravovaného**: Zobrazí spravované identifikační čísla pro spravované vlákna.  
  
- **Kategorie**: Zobrazí kategorie vlákna vlákna uživatelského rozhraní, obslužné rutiny volání vzdálené procedury nebo pracovní vlákna. Zvláštní kategorie identifikuje hlavního vlákna aplikace.  
  
- **Název**: identifikuje každý podproces podle názvu, pokud existuje, nebo jako \<bez názvu >.  
  
- **Umístění**: ukazuje, kde je spuštěn podproces. Můžete rozbalit tohoto umístění zobrazíte úplného zásobníku volání pro vlákno.  
  
- **Priorita**: pokročilé sloupce (ve výchozím nastavení skrytá), které zobrazuje priority nebo priority, které systém přiřadil pro každé vlákno.  
  
- **Maska příbuznosti**: pokročilé sloupce (ve výchozím nastavení skrytá), který zobrazuje maska přidružení procesoru pro každé vlákno. V systému s více procesory Maska spřažení Určuje, které procesory, ve kterých lze spustit vlákno.  
  
- **Pozastavený počet**: pokročilé sloupce (ve výchozím nastavení skrytá), která zobrazuje pozastavený počet. Tento počet Určuje, zda lze spustit vlákno. Další informace o pozastavené počty najdete v tématu [zablokovat a odblokovat vlákna](#freeze-and-thaw-threads).  
  
- **Název procesu**: pokročilé sloupce (ve výchozím nastavení skrytá), který zobrazuje proces, ke kterému patří každé vlákno. Data v tomto sloupci může být užitečné při ladění více procesů.  

- **ID procesu**: ID pokročilé sloupce (ve výchozím nastavení skrytá), který zobrazuje proces, ke které patří každé vlákno. 

- **Kandidát spojení**: pokročilé sloupce (ve výchozím nastavení skrytá), který jednoznačně identifikuje počítač, ke kterému je připojený ladicí program. 
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Chcete-li zobrazit okno vlákna v režimu přerušení nebo v režimu spuštění  
  
-   I když jsou Visual Studio v režimu ladění, vyberte **ladění** nabídky, přejděte k **Windows**a pak vyberte **vlákna**.  
  
### <a name="to-display-or-hide-a-column"></a>Chcete-li zobrazit nebo skrýt sloupec  
  
-   Na panelu nástrojů v horní části **vlákna** okně **sloupce**. Zaškrtněte nebo zrušte název sloupce, který chcete zobrazit nebo skrýt.  

## <a name="display-flagged-threads"></a>Zobrazit vlákna s příznakem  
 Můžete označit příznakem vlákna, které chcete věnovat zvláštní pozornost označením s ikonou v **vlákna** okna. Další informace najdete v tématu [postupy: označení a odstranění označení vlákna](../debugger/how-to-flag-and-unflag-threads.md). V **vlákna** okna, můžete také zobrazit všechna vlákna, nebo pouze vlákna s příznakem.  
  
### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
-   Zvolte **zobrazit vlákna pouze s příznakem** na panelu nástrojů v horní části **vlákna** okna. (Pokud je neaktivní, musíte nejprve označit, že některá vlákna.) 

## <a name="freeze-and-thaw-threads"></a>Zablokovat a odblokovat vlákna  
 Po ukotvení vlákno se systém nespustí provádění vlákna, i v případě, že prostředky jsou k dispozici.  
  
 V nativním kódu, můžete pozastavit nebo obnovit vlákna voláním funkce Windows `SuspendThread` a `ResumeThread`. Nebo volat funkce knihovny MFC [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) a [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Při volání `SuspendThread` nebo `ResumeThread`, *pozastavený počet* ukazuje **vlákna** okno se změní. Pozastavený počet nezmění, pokud zmrazit nebo odblokovat nativních vláken. Vlákno nelze spustit v nativním kódu, pokud je roztát a má nulový počet pozastavené.  
  
 Pozastavený počet ve spravovaném kódu změní při zmrazit nebo odblokovat vlákna. Je-li ukotvit vlákna ve spravovaném kódu, jeho pozastavený počet je 1. Při zablokování vlákna v nativním kódu, jeho pozastavený počet je 0, pokud jste použili `SuspendThread` volání.  
  
> [!NOTE]
>  Při ladění volání z nativního kódu pro spravovaný kód spravovaný kód běží ve stejné fyzické vlákno v nativním kódu, která ji zavolala. Pozastavení nebo zmrazení nativních vláken se taky zablokuje spravovaného kódu.  
  
### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Chcete-li zmrazit nebo odblokovat spuštění vlákna  
  
-   Na panelu nástrojů v horní části **vlákna** okně **zablokovat vlákna** nebo **uvolnit vlákna**.  
  
     Tato akce ovlivní pouze vlákna, které jsou vybrány v **vlákna** okna. 

### <a name="switch-to-another-thread"></a>Přepnutí na jiné vlákno 

Žlutá šipka označuje aktuální vlákno (a umístění spuštění ukazatele). Zelená šipka s vlnitým ocáskem označuje, že není aktuální vlákno má aktuální kontext ladicího programu.

#### <a name="to-switch-to-another-thread"></a>Chcete-li přepnout do jiného vlákna  
  
-   Použijte jednu z následujících kroků:  
  
    -   Klikněte dvakrát na libovolného vlákna.  
  
    -   Klikněte pravým tlačítkem na vlákno a vyberte **přepnout na vlákno**.

## <a name="group-and-sort-threads"></a>Skupiny a řadit vlákna  
 Při seskupování vlákna nadpis se zobrazí v tabulce pro každou skupinu. Záhlaví obsahuje popis skupiny, jako například **pracovní vlákna** nebo **vlákna bez příznaku**a ovládacím prvkem strom. Vlákna člena každé skupiny se zobrazí v záhlaví skupiny. Pokud chcete skrýt člena vláken pro skupiny, pomocí ovládacího prvku stromu sbalit skupiny.  
  
 Protože seskupení má přednost před řazení, můžete seskupit podle kategorie, například vlákna a pak je můžete seřadit podle ID v jednotlivých kategoriích.  
  
### <a name="to-sort-threads"></a>Chcete-li seřadit vláken  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou teď seřazené podle hodnoty ve sloupci.  
  
2.  Pokud chcete změnit směr řazení, znovu vyberte tlačítko stejné.  
  
     Vlákna, které se zobrazovaly v horní části seznamu, se teď zobrazí v dolní části.  
  
### <a name="to-group-threads"></a>Do skupiny vláken  
  
-   V **vlákna** nástrojů okna, vyberte **Seskupit podle** seznamu a potom vyberte kritéria, které chcete seskupit vlákna tak.  
  
### <a name="to-sort-threads-within-groups"></a>Chcete-li seřadit vláken v rámci jednotlivých skupin  
  
1.  Na panelu nástrojů v horní části **vlákna** okna, vyberte **Seskupit podle** seznamu a potom vyberte kritéria, které chcete seskupit vlákna tak.  
  
2.  V **vlákna** okna, klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou teď seřazené podle hodnoty ve sloupci.  
  
### <a name="to-expand-or-collapse-all-groups"></a>Chcete-li rozbalit nebo sbalit všechny skupiny  
  
-   Na panelu nástrojů v horní části **vlákna** okně **Rozbalit skupiny** nebo **sbalit skupiny**.  
  
## <a name="search-for-specific-threads"></a>Vyhledejte konkrétní vláken  
 Můžete vyhledat vlákna, které odpovídají zadaného řetězce v **vlákna** okna. Při hledání vlákna, v okně zobrazí všechna vlákna odpovídající hledaný řetězec na jakémkoli sloupci. Tyto informace zahrnují umístění vlákna, která se zobrazí v horní části zásobníku volání v **umístění** sloupce. Ve výchozím nastavení není prohledána úplného zásobníku volání.  
  
### <a name="to-search-for-specific-threads"></a>K vyhledání konkrétního vlákna  
  
1. Na panelu nástrojů v horní části **vlákna** okno, přejděte **hledání** boxu tak buď:  

     - Zadejte hledaný řetězec a stiskněte klávesu **Enter**.  
  
     \- nebo –  
  
     - Vyberte rozevírací seznam vedle **hledání** a vyberte hledaný řetězec předešlých hledání.  
  
2. (Volitelné) Chcete-li do hledání zahrnout úplného zásobníku volání, vyberte **zásobník volání hledání**.   
  
## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Zobrazit zásobníky volání vlákna a přepínat mezi snímky  
Každé vlákno ve vícevláknovém programu, má své vlastní zásobníku volání. **Vlákna** okno poskytuje pohodlný způsob, jak zobrazit tyto balíčky.

> [!TIP]
> Vizuální znázornění zásobník volání pro každé vlákno, použijte [paralelní zásobníky](../debugger/get-started-debugging-multithreaded-apps.md) okna.
  
### <a name="to-view-the-call-stack-of-a-thread"></a>Chcete-li zobrazit zásobník volání vlákna  
  
-   V **umístění** sloupce, vyberte obrácenou trojúhelníku vedle umístění vlákna.  
  
     Umístění se rozbalí a zobrazí zásobník volání pro vlákno.  
  
### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>K zobrazení nebo sbalit zásobníky volání všech vláken  
  
-   Na panelu nástrojů v horní části **vlákna** okně **rozbalit zásobníky volání** nebo **sbalit zásobníky volání**.  
  
## <a name="see-also"></a>Viz také:  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)