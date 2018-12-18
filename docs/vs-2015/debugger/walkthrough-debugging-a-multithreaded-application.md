---
title: 'Návod: Ladění vícevláknové aplikace | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multithreaded debugging, walkthrough
- walkthroughs, multithreaded debugging
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5dd742411710698cb2dd626e211cb0e73b8379e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798626"
---
# <a name="walkthrough-debugging-a-multithreaded-application"></a>Návod: Ladění vícevláknové aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] poskytuje zdokonalené **vlákna** okno a jinými uživateli rozhraní vylepšení usnadňují ladění vícevláknových aplikací. Tento názorný postup trvá jenom několik minut, ale jeho dokončení se můžete seznámit s novými funkcemi rozhraní pro ladění aplikací s více vlákny.  
  
 Pokud chcete začít tento návod, potřebujete projekt aplikace s více vlákny. Postupujte podle kroků uvedených zde k vytvoření tohoto projektu.  
  
#### <a name="to-create-the-walkthrough-project"></a>Vytvoření projektu průvodce  
  
1.  Na **souboru** nabídce zvolte **nový** a potom klikněte na tlačítko **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V **typu projektu**s poli, klikněte na jazyk podle vašeho výběru: **jazyka Visual Basic**, **Visual C#**, nebo **Visual C++**.  
  
3.  V **šablony** zvolte **konzolovou aplikaci** nebo **Konzolová aplikace CLR**.  
  
4.  V **název** pole, zadejte název MyThreadWalkthroughApp.  
  
5.  Klikněte na tlačítko **OK**.  
  
     Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor. V závislosti na jazyku, kterou jste zvolili může volat zdrojový soubor Module1.vb, Program.cs nebo MyThreadWalkthroughApp.cpp  
  
6.  Odstranit kód, který se zobrazí ve zdrojovém souboru a nahraďte ji metodou ukázkový kód, který se zobrazí v části "Vytvoření vlákna" v tématu [vytváření vláken a předávání dat v době spuštění](http://msdn.microsoft.com/library/52b32222-e185-4f42-91a7-eaca65c0ab6d).  
  
7.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.  
  
#### <a name="to-begin-the-walkthrough"></a>Chcete-li začít návodu  
  
-   V okně zdroje vyhledejte následující kód:  
  
    ```vb  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
```csharp  
Thread.Sleep(3000);  
Console.WriteLine();  
```  
  
```cpp  
Thread::Sleep(3000);  
Console.WriteLine();  
```  
  
#### <a name="to-start-debugging"></a>Pro spuštění ladění  
  
1.  Klikněte pravým tlačítkem `Console.WriteLine` prohlášení, přejděte na **zarážky** a potom klikněte na **vložit zarážku**.  
  
     Na levé straně okna zdroje na ovládací prvek se zobrazí červený koule. To znamená, že na tomto místě je nyní nastaveno zarážku.  
  
2.  Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.  
  
     Zahájením ladění, vaše aplikace spustí konzolu ke spuštění a pak zastaví na zarážce.  
  
3.  Okno aplikace konzoly v tomto okamžiku má fokus, klikněte na tlačítko v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno a vraťte se na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  V okně zdroje vyhledejte řádek, který obsahuje následující kód:  
  
    ```vb  
    Thread.Sleep(5000)   
    ```  
  
```csharp  
Thread.Sleep(3000);  
```  
  
```cpp  
Thread::Sleep(3000);  
```  
  
1.  
  
#### <a name="to-discover-the-thread-marker"></a>Ke zjištění značky vlákna  
  
1. Klikněte pravým tlačítkem **vlákna** okna, klikněte na **zobrazit vlákna ve zdroji**.  
  
2. Podívejte se na ovládací prvek na levé straně okna. Na tomto řádku zobrazí se ikona, která se podobá dvěma vlákny látky. Jedno vlákno je červený a druhý je modrá. Značky vlákna označuje, že je vlákno zastavené v tomto umístění. Případně je vlákno zastavené v tomto umístění.  
  
3. Ukazatel myši značky vlákna. Datového tipu, který se zobrazí. DataTip zjistíte číslo ID názvu a vlákna pro každé vlákno zastavené. V tomto případě existuje pouze jedno vlákno, jehož název je pravděpodobně `<noname>`.  
  
4. Klikněte pravým tlačítkem na značky vlákna. Poznámka: možnosti v místní nabídce.  
  
   Tato ikona je *značky vlákna*:  
  
   ![Značka podprocesu](../debugger/media/threadmarker.gif "ThreadMarker")  
  
## <a name="flagging-and-unflagging-threads"></a>Označení a Unflagging vlákna  
 V [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)], můžete označit příznakem vlákna, která chcete věnovat zvláštní pozornost. Příznakem vlákna je dobrým způsobem, jak udržovat přehled o důležitých vláken a ignorovat vláken, která vás nezajímají.  
  
#### <a name="to-flag-threads"></a>Označit vlákna  
  
1.  Na **zobrazení** nabídky, přejděte k **panely nástrojů**.  
  
     Ujistěte se, že **umístění ladění** vybrán panel nástrojů.  
  
2.  Přejděte **umístění ladění** nástrojů a klikněte na tlačítko **vlákna** seznamu.  
  
    > [!NOTE]
    >  Tento panel nástrojů můžete rozpoznat podle tři viditelného seznamy: **procesu**, **vlákna**, a **rámec zásobníku**.  
  
3.  Všimněte si, kolik vlákna se zobrazují v seznamu.  
  
4.  Přejděte zpět do okna zdroje a kliknutí pravým tlačítkem myši **vlákna** značky znovu.  
  
5.  V místní nabídce, přejděte na **příznak**a potom klikněte na název vlákna a identifikační číslo.  
  
6.  Přejděte zpět na **umístění ladění** nástrojů a klikněte na tlačítko **vlákna** znovu.  
  
     Pouze vlákno s příznakem se zobrazí v seznamu nyní. Tlačítko příznak, který je právě napravo od **vlákna** seznamu. Příznak ikony na tlačítku byla aktivní před. Nyní je plná, jasně red.  
  
7.  Ukazatel myši na ikonu příznaku.  
  
     Se zobrazí automaticky otevírané okno. Toto automaticky otevírané okno se dozvíte, jaké režim **vlákna** seznamu je v: **zobrazit pouze s příznakem vlákna**.  
  
8.  Klikněte na tlačítko příznak přepnete zpět do **zobrazit všechna vlákna** režimu.  
  
9. Klikněte na tlačítko **vlákna** znovu a ověřte, že nyní je vidět všechna vlákna znovu.  
  
10. Klikněte na tlačítko příznak přepnete zpět do **zobrazit pouze s příznakem vlákna**.  
  
11. Na **ladění** nabídky, přejděte k **Windows** a potom klikněte na tlačítko **vlákna**.  
  
     **Vlákna** zobrazí se okno. Jedno vlákno má ikonu viditelného příznak k němu připojená.  
  
12. V okně zdroje klikněte pravým tlačítkem na značky vlákna znovu.  
  
     Všimněte si, jaké možnosti jsou teď dostupné v místní nabídce. Místo **příznak**, teď se vám **Unflag**. Neklikejte na **Unflag**.  
  
13. Přejděte k dalšímu postupu o tom, jak odstranění označení vlákna.  
  
#### <a name="to-unflag-threads"></a>K odstranění označení vlákna  
  
1.  Na **vlákna** okna, klikněte pravým tlačítkem na řádek odpovídající vlákno s příznakem.  
  
     Zobrazí se místní nabídka. Obsahuje možnosti pro **Unflag** a **odznačit všechna**.  
  
2.  Odznačit vlákno, klikněte na tlačítko **Unflag**.  
  
3.  Klikněte na ikonu Červený praporek.  
  
4.  Podívejte se na **umístění ladění** nástrojů znovu. Tlačítko příznak aktivní znovu. Je odebrán příznak pouze vlákno s příznakem. Vzhledem k tomu, že neexistují žádná vlákna s příznakem, panelu nástrojů náramků RFID zpět do **zobrazit všechna vlákna** režimu. Klikněte na tlačítko **vlákna** seznam a ověřte, zda se zobrazí všechna vlákna.  
  
5.  Přejděte zpět **vlákna** okno a zkontrolovat informace o sloupci.  
  
     Většina tlačítek v horní části každého sloupce, mají názvy, které identifikují sloupci. První sloupec na levé straně, ale nemá žádný název. Místo toho má ikonu, což je osnovy příznak. Můžete si všimnout stejné obrysu v jednotlivých řádcích seznamu vláken. Přehled znamená, že je vlákna bez příznaku.  
  
6.  Klikněte na příznak jsou podrobněji popsány dále dvěma vlákny, druhý a třetí v dolní části seznamu.  
  
     Ikony příznaků stát solid červené, namísto prázdný jsou podrobněji popsány dále.  
  
7.  Klikněte na tlačítko v horní části sloupce Příznak.  
  
     Pořadí seznamu vláken změnit, pokud jste klikli na tlačítko. Seznam vláken je teď seřazené s příznakem vlákna v horní části.  
  
8.  Znovu klikněte na tlačítko v horní části sloupce Příznak.  
  
     Pořadí řazení změnit znovu.  
  
## <a name="more-about-the-threads-window"></a>Další informace o okna vláken  
  
#### <a name="to-learn-more-about-the-threads-window"></a>Další informace o okna vláken  
  
1.  V **vlákna** okna, zkontrolujte třetí sloupec z levé strany. V horní části tohoto sloupce na tlačítku zobrazeno **ID**.  
  
2.  Klikněte na tlačítko **ID**.  
  
     Seznam vláken je teď seřazené podle číslo ID vlákna.  
  
3.  Klikněte pravým tlačítkem na jakékoli vlákno v seznamu. V místní nabídce klikněte na tlačítko **hexadecimální zobrazení**.  
  
     Formát čísla ID vlákna je změnit.  
  
4.  Umístěte ukazatel myši nad libovolného vlákna v seznamu.  
  
     Momentální zpožděním zobrazí se DataTip. Zobrazuje částečné volání zásobníku pro vlákno.  
  
5.  Podívejte se na čtvrtém sloupci zleva, který je označen **kategorie**. Vlákna jsou rozdělit do kategorií.  
  
     První vlákno v procesu vytvoří se označuje jako hlavní vlákno. Vyhledejte ho v seznamu vláken.  
  
6.  Klikněte pravým tlačítkem na hlavním vlákně a pak klikněte na tlačítko **přepnout na vlákno**.  
  
     Zobrazí se dialogové okno upozornění. Ta vám zjistí, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nemůže zobrazit zdrojový kód pro hlavní vlákno.  
  
     Klikněte na tlačítko **OK**.  
  
7.  Podívejte se na **zásobník volání** okno a **umístění ladění** nástrojů.  
  
     Obsah **zásobník volání** okno změnily.  
  
## <a name="switching-the-active-thread"></a>Přepnout aktivní vlákno  
  
#### <a name="to-switch-threads"></a>Chcete-li přepnout vlákna  
  
1.  V **vlákna** okna, zkontrolujte druhý sloupec z levé strany. Tlačítko v horní části v tomto sloupci nemá žádný text nebo ikonu. Tento sloupec se nachází **aktivní vlákna** sloupce.  
  
2.  Podívejte se na **aktivní vlákno** sloupce a Všimněte si, že má jedno vlákno žlutá šipka. Toto je *indikátor aktivní vlákna*.  
  
3.  Si poznamenejte číslo ID vlákna kde je umístěn ukazatel aktivní vlákno. Indikátor aktivní vlákna se přesune do jiného vlákna, ale budete muset vložit ho po dokončení obnovení.  
  
4.  Klikněte pravým tlačítkem na jiné vlákno a poté klikněte na tlačítko **přepnout na vlákno**.  
  
5.  Podívejte se na **zásobník volání** okna v okně zdroje. Obsah se změnil.  
  
6.  Podívejte se na **umístění ladění** nástrojů. Aktivní vlákno se změnila, příliš.  
  
7.  Přejděte **umístění ladění** nástrojů. Klikněte na tlačítko **vlákno** a z rozevíracího seznamu vyberte jiné vlákno.  
  
8.  Podívejte se na **vlákna** okna. Indikátor aktivní vlákna se změnila.  
  
9. V okně zdroje klikněte pravým tlačítkem na značky vlákna. V místní nabídce, přejděte na **přepnout na** a klikněte na číslo název nebo ID vlákna.  
  
     Nyní jste viděli tři způsoby, jak změnit aktivní vlákno: pomocí **vlákna** okně **vlákno** pole **umístění ladění** nástrojů a indikátor vlákna v okno zdroje.  
  
     S indikátor vlákna můžete přepnout pouze do vlákna, která se zastaví v tomto konkrétním umístění. S použitím **vlákna** okno a **umístění ladění** nástrojů, můžete přepnout na libovolného vlákna.  
  
## <a name="freezing-and-thawing-thread-execution"></a>Zmrazení a uvolnění provádění vlákna  
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Ukotvit a uvolnit vlákna  
  
1.  V **vlákna** okna, klikněte pravým tlačítkem na libovolného vlákna a pak klikněte na **ukotvit**.  
  
2.  Podívejte se na aktivní vlákno sloupce. Pár svislé pruhy teď budou zobrazovat existuje. Tyto dva modré pruhy znamenat, že vlákno je zmrazen.  
  
3.  Podívejte se na **pozastavit** sloupce. Počet pozastavení pro vlákno je nyní 1.  
  
4.  Klikněte pravým tlačítkem na zmrazené vlákno a potom klikněte na tlačítko **uvolnit**.  
  
     Aktivní vlákno sloupce a **pozastavit** změny sloupců.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)



