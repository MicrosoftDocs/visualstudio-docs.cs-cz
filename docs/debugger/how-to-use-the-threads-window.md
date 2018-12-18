---
title: Ladění vícevláknových aplikací
description: Ladění pomocí okna vláken a panelu nástrojů umístění ladění v sadě Visual Studio
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd66d7f9d8f214e8e7166a77162553b694e20cc5
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389400"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window"></a>Návod: Ladění vícevláknové aplikace pomocí okna vlákna

Několik prvků uživatelského rozhraní sady Visual Studio můžete ladit aplikace s více vlákny. Tento článek představuje vícevláknové ladění funkcí v okně editoru kódu **umístění ladění** nástrojů a **vlákna** okna. Informace o ostatních nástrojích pro ladění vícevláknových aplikací najdete v tématu [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md). 
  
Dokončení tohoto kurzu trvá jenom pár minut a vás seznámí se základními funkcemi ladění vícevláknových aplikací.

## <a name="create-a-multithreaded-app-project"></a>Vytvořte projekt aplikace s více podprocesy  

Vytvořte následující projekt aplikace s více podprocesy pro použití v tomto kurzu: 
  
1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**.  
   
1. V **nový projekt** dialogové okno:
   - Pro C# aplikaci, vyberte **Visual C#**    >  **Konzolová aplikace (.NET Framework)**.  
   - Aplikace s C++, vyberte **Visual C++** > **Konzolová aplikace Windows**.
   
1. Název aplikace MyThreadWalkthroughApp a potom vyberte **OK**.  
   
   Nový projekt se zobrazí v **Průzkumníka řešení**, zdrojový soubor s názvem *Program.cs* nebo *MyThreadWalkthroughApp.cpp* se otevře v okně zdrojového kódu.  
   
1. Nahraďte kód ve zdrojovém souboru se C# nebo C++ ukázkový kód z [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md).  
   
1. Vyberte **souboru** > **Uložit vše**.  
  
## <a name="start-debugging"></a>Spustit ladění 

1. Ve zdrojovém kódu vyhledejte následující řádky:  
   
   ```csharp  
   Thread.Sleep(3000); 
   Console.WriteLine();
   ```  
   
   ```C++ 
   Thread::Sleep(3000); 
   Console.WriteLine(); 
   ```
   
1. Nastavit zarážku na `Console.WriteLine();` řádku klepnutím na tlačítko v levém hřbetu, nebo výběrem řádku a stisknutím klávesy **F9**.  
   
   Zarážka se zobrazí jako červená tečka v levém hřbetu vedle řádku kódu.  
   
1. Vyberte **ladění** > **spustit ladění**, nebo stiskněte klávesu **F5**.  
   
   Aplikace se spustí v režimu ladění a pozastavení na zarážce.  
   
1. V režimu přerušení, otevřete **vlákna** okna tak, že vyberete **ladění** > **Windows** > **vlákna**. Musí být v relaci ladění k otevření nebo najdete v článku **vlákna** a dalších oknech ladění. 
   
## <a name="examine-thread-markers"></a>Prozkoumejte značky vlákna

1. Ve zdrojovém kódu vyhledejte `Console.WriteLine();` řádku. 
   
   1. Klikněte pravým tlačítkem **vlákna** okna a vyberte **zobrazit vlákna ve zdroji** ![zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") z nabídky.
   
   Nyní zobrazuje řádek mřížky vedle zdrojový kód *značky vlákna* ikonu ![značky vlákna](../debugger/media/dbg-thread-marker.png "značky vlákna"). Značky vlákna označuje, že je vlákno zastavené v tomto umístění. Pokud existuje více než jedno vlákno zastavené v místě, ![více vláken](../debugger/media/dbg-multithreaded-show-threads.png "více vláken") ikona.
   
1. Ukazatel myši značky vlákna. Zobrazí se DataTip zobrazuje název a vlákna identifikační číslo pro zastavené vlákno nebo vláken. Názvy vláken může být `<No Name>`.  

   >[!TIP]
   >K identifikaci nameless vlákna, je možné je v přejmenovat **vlákna** okna. Klikněte pravým tlačítkem na vlákno a vyberte **přejmenovat**.
  
1. Klikněte pravým tlačítkem na značky vlákna ve zdrojovém kódu, zobrazí se dostupné možnosti v místní nabídce. 

## <a name="flag-and-unflag-threads"></a>Označení a odstranění označení vlákna 

Můžete označit příznakem vlákna ke sledování vláken, kterému chcete věnovat zvláštní pozornost. 

Označení a odstranění označení vlákna z editoru zdrojového kódu nebo **vlákna** okna. Vyberte, jestli chcete zobrazit pouze příznakem vlákna nebo všechna vlákna z **umístění ladění** nebo **vlákna** panely nástrojů. Výběrech z libovolného místa ovlivňují všechna umístění. 

### <a name="flag-and-unflag-threads-in-source-code"></a>Označení a odstranění označení vlákna ve zdrojovém kódu 

1. Otevřít **umístění ladění** nástrojů tak, že vyberete **zobrazení** > **panely nástrojů** > **umístění ladění**. Můžete také v oblasti panelu nástrojů klikněte pravým tlačítkem a vybrat **umístění ladění**. 
   
1. **Umístění ladění** nástrojů má tři pole: **procesu**, **vlákna**, a **rámec zásobníku**. Rozevírací seznam **vlákna** seznamu a Všimněte si, kolik vlákna existuje. V **vlákno** seznamu aktuálně spuštěné vlákno je označena **>** symbol. 
   
1. V okně zdrojového kódu najeďte myší na ikonu značky vlákna na ovládací prvek a vyberte ikonu příznaku (nebo jednu z ikon prázdný příznak) v DataTip. Červenou ikonu vlajky. 
   
   Můžete také kliknout pravým tlačítkem na ikonu značky vlákna, přejděte na **příznak**a pak vyberte vlákno označit, že z místní nabídky.  
   
1. Na **umístění ladění** nástrojů, vyberte **zobrazit pouze s příznakem vlákna** ikonu ![zobrazit vlákna s příznakem](../debugger/media/dbg-threads-show-flagged.png "zobrazit vlákna s příznakem")do vpravo **vlákna** pole. Ikona je zobrazena šedě Pokud jeden nebo více vláken jsou označeny příznakem.  
   
   Pouze vlákno s příznakem se teď zobrazí v **vlákno** rozevíracího seznamu na panelu nástrojů. Chcete-li znovu zobrazit všechna vlákna, vyberte **zobrazit pouze s příznakem vlákna** znovu na ikonu.
   
   >[!TIP]
   >Po označené příznakem některá vlákna, můžete umístit kurzor v editoru kódu, klikněte pravým tlačítkem a vyberte **spustit vlákna s příznakem do pozice kurzoru**. Nezapomeňte vybrat, že kód, že všechna vlákna příznakem dosáhne. **Spustit vlákna s příznakem do pozice kurzoru** pozastaví vláken na vybraný řádek kódu, které usnadňují určit pořadí provedení [zmrazení a uvolnění vláken](#bkmk_freeze).
   
1. Chcete-li přepnout stav aktuálně spuštěné vlákno s příznakem nebo bez příznaku, vyberte jeden příznak **přepnout aktuální vlákno příznakem stavu** tlačítko panelu nástrojů na levé straně **zobrazit pouze s příznakem vlákna** tlačítko. Nastavení příznaku aktuální vlákno je užitečné pro nalezení aktuálního vlákna, když se zobrazují pouze vlákna s příznakem. 
   
1. Chcete-li zrušit označení vlákna, najeďte myší značky vlákna ve zdrojovém kódu a výběrem ikony zaškrtnutí políčka zrušte, nebo klikněte pravým tlačítkem na značky vlákna a vyberte červený praporek **Unflag**.  

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Označení a odstranění označení vlákna v okně vlákna 

V **vlákna** okně s příznakem nemá red příznak ikony vedle sebe, při vlákna bez příznaku, zda se zobrazí, mít prázdný ikony.

![Vlákna okna](../debugger/media/dbg-threads-window.png "vlákna okna")  
  
Vyberte ikonu příznaku, chcete-li změnit stav vlákna s příznakem nebo bez příznaku, v závislosti na jejím aktuálním stavu. 

Můžete také klikněte pravým tlačítkem na řádek a vybrat **příznak**, **Unflag**, nebo **odznačit všechna vlákna** z místní nabídky. 

**Vlákna** okna nástrojů má také **zobrazit vlákna pouze s příznakem** tlačítko, které je righthand jednu z ikon dvou příznak. Funguje stejně jako tlačítko na **umístění ladění** nástrojů a buď tlačítko ovládací prvky zobrazení v obou umístěních. 

### <a name="other-threads-window-features"></a>Další funkce okna vláken

V **vlákna** okna, vyberte záhlaví libovolného sloupce řadit vlákna podle sloupce. Znovu vyberte pořadí řazení. Pokud se zobrazují všechna vlákna, výběrem sloupce ikonu příznaku vlákna seřadí podle stavu s příznakem nebo bez příznaku. 

Druhý sloupec **vlákna** okna (žádné záhlaví) je **aktuální vlákno** sloupce. V tomto sloupci žlutá šipka označuje aktuální bod provádění. 

**Umístění** sloupec zobrazuje, kde se zobrazí každý podproces ve zdrojovém kódu. Vybráním šipky rozbalte vedle **umístění** položka nebo podržte ukazatel myši nad položku, chcete-li zobrazit zásobník volání částečné pro toto vlákno. 

>[!TIP]
>Grafické zobrazení zásobníky volání pro vlákna, použijte [paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md) okna. Chcete-li otevřít okno, během ladění, vyberte **ladění**> **Windows** > **paralelní zásobníky**.  

Kromě **příznak**, **Unflag**, a **odznačit všechna vlákna**, klikněte pravým tlačítkem na místní nabídku pro **vlákna** má okno položky:

- **Zobrazit vlákna ve zdroji** tlačítko.
- **Hexadecimální zobrazení**, jaké změny **ID vlákna**ve **vlákna** okna z desítkové do šestnáctkovém formátu. 
- [Přepnout na vlákno](#switch-to-another-thread), která okamžitě přepne spuštění pro toto vlákno. 
- **Přejmenovat**, která umožňuje změnit název vlákna. 
- [Zablokovat a Odblokovat](#bkmk_freeze) příkazy.

## <a name="bkmk_freeze"></a> Zablokovat a odblokovat vlákna provádění 

Můžete ukotvit a uvolnit, nebo pozastavit a obnovit, určit pořadí, ve kterém provádění vlákna pracovních vláken. Zmrazení a uvolnění vlákna mohou pomoci vyřešit problémy se souběžností, jako je například zablokování a konflikty časování.

> [!TIP]
> Postupujte podle jednoho vlákna bez zmrazení ostatní vlákna, což je také běžným scénářem, ladění, naleznete v tématu [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
**Ukotvit a uvolnit vlákna:**  
  
1. V **vlákna** okna, klikněte pravým tlačítkem na libovolného vlákna a pak vyberte **ukotvit**. A **pozastavení** ikonu **aktuální vlákno** sloupec označuje, že vlákno je zmrazen.  
   
1. Vyberte **sloupce** v **vlákna** panel nástrojů okna a pak vyberte **pozastavený počet** zobrazíte **pozastavený počet** sloupce. Pozastavený počet zmrazené vlákno hodnotu **1**.  
   
1. Klikněte pravým tlačítkem na zmrazené vlákno a vyberte **uvolnit**.  
  
   **Pozastavení** ikona zmizí a **pozastavený počet** hodnotu **0**. 
  
## <a name="switch-to-another-thread"></a>Přepnutí na jiné vlákno 

Může se zobrazit **aplikace je v režimu pozastavení** okno při pokusu o přepnutí na jiné vlákno. Toto okno říká, že vlákno nemá žádný kód, který aktuální ladicí program může zobrazit. Například může být ladění spravovaného kódu, ale vlákno je nativní kód. V okně nabízí návrhy pro vyřešení problému. 
  
**Chcete-li přepnout do jiného vlákna:**

1. V **vlákna** okno, poznamenejte aktuální ID vlákna, což je na vlákno se žlutou šipku v **aktuální vlákno** sloupce. Budete chtít přepnout zpět na toto vlákno pokračujte vaší aplikace. 
   
1. Klikněte pravým tlačítkem na jiném vlákně a vyberte **přepnout na vlákno** v místní nabídce.  
   
1. Podívejte se, že se změní umístění žlutá šipka v **vlákna** okna. Původní aktuální vlákno značky taky zůstane, osnovy. 
   
   Podívejte se na popis tlačítka na značky vlákna v editoru zdrojového kódu a v seznamu **vlákno** rozevírací seznam pro **umístění ladění** nástrojů. Podívejte se, že aktuální vlákno také změnil existuje. 
   
1. Na **umístění ladění** nástrojů vyberte jiném podprocesu než **vlákno** seznamu. Všimněte si, že ve dvou umístěních také změní aktuální vlákno. 
   
1. V editoru zdrojového kódu klikněte pravým tlačítkem na značky vlákna, přejděte na **přepnout na vlákno**a vyberte jiné vlákno ze seznamu. Podívejte se, že se změní aktuální vlákno ve všech třech umístěních.  
   
Pomocí značky vlákna ve zdrojovém kódu můžete přepnout pouze do vlákna, která se zastaví na tomto místě. S použitím **vlákna** okno a **umístění ladění** nástrojů, můžete přepnout na libovolného vlákna.   

Teď když jste se naučili základy ladění vícevláknových aplikací. Můžete sledovat, příznak a odstranění označení a zablokovat a uvolnit vlákna s použitím **vlákna** okně **vlákno** v seznamu **umístění ladění** nástrojů nebo značky vlákna ve editor zdrojového kódu.
  
## <a name="see-also"></a>Viz také:  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)
