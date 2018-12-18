---
title: Procházení kódu s ladicím programem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43155bbd4236ea34d67058443e8814f7ccf00b1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750581"
---
# <a name="navigating-through-code-with-the-debugger"></a>Procházení kódu s ladicím programem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seznamte se s příkazy a klávesové zkratky pro navigaci kódu v ladicím programu a, který bude rychlejší a snazší vyhledat a vyřešit problémy ve vaší aplikaci. Při přechodu kódu v ladicím programu můžete [kontrolovat stav vaší aplikace](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) nebo Další informace o jeho spuštění toku.  
  
## <a name="start-debugging"></a>Spustit ladění  
 Často, spuštění ladění pomocí relace **F5** (**ladění** / **spustit ladění**). Tento příkaz spustí vaši aplikaci s připojeným ladícím nástrojem.  
  
 Zelená šipka také spustí ladicí program (stejné jako **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Zahrnují několik způsobů, můžete spustit aplikaci s připojeným ladícím nástrojem **F11** ([krokování s vnořením do kódu](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([krok za kód](#BKMK_Step_over_Step_out)), nebo pomocí **spustit ke kurzoru**.  Na co dělat tyto možnosti najdete v dalších částech tohoto tématu informace o.  
  
 Při ladění, Žlutá čára ukazuje kód, který se spustí další.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Při ladění, můžete přepínat mezi příkazů, jako jsou **F5**, **F11** a používat další funkce popsané v tomto tématu (například zarážky) na kód, který se má podívat se na rychlé.  
  
 Většina funkcí ladicího programu, jako je například zobrazení hodnot proměnných v okně místních hodnot nebo vyhodnocování výrazů v okně kukátka jsou k dispozici pouze tehdy, když je pozastavena ladicím programu (také nazývané *režimu pozastavení*). Když se ladicí program pozastaví, stav vaší aplikace je pozastavený, při funkce a proměnné, a objekty zůstanou v paměti. V režimu pozastavení můžete zkoumat pozice prvků a stavy pro vyhledání porušení nebo chyb. U některých typů projektů lze také provést úpravy aplikace v režimu přerušení.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Krokovat s vnořením kód, řádek po řádku  
 Chcete-li zastavit na každém řádku kódu (každý příkaz) během ladění, použijte **F11** klávesovou zkratku (nebo **ladění** / **Krokovat s vnořením** v nabídce).  
  
> [!TIP]
>  Při spuštění každého řádku kódu, můžete najedete myší proměnných najdete v jejich hodnoty nebo použít [lokální](../debugger/autos-and-locals-windows.md) a [Watch](../debugger/autos-and-locals-windows.md) windows a sledujte jejich hodnoty změnit.  
  
 Tady jsou některé podrobnosti o chování **Krokovat s vnořením**:  
  
- U volání vnořené funkce **Krokovat s vnořením** přejde k nejhlouběji vnořené funkci. Pokud používáte **Krokovat s vnořením** na volání, například `Func1(Func2())`, ladicí program vstoupí do funkce `Func2`.  
  
- Ladicí program ve skutečnosti provede příkazy kódu spíše než fyzické řádky. Například `if` klauzule může být napsána na jednom řádku:  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Když přejdete na tomto řádku, ladicí program zpracuje podmínku jako jeden krok a následek jako jiný (v tomto příkladu je podmínka pravdivá).  
  
  Vizuální trasování zásobníku volání při krokování do funkce, najdete v článku [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Krokovat kód, přeskakuje se funkce  
 Při spouštění kódu v ladicím programu, často se zjistíte, že není nutné zobrazit, co se děje v určitou funkci (nezáleží ji nebo ji znát funguje, jako jsou dobře otestovaný knihovny kódu). Pomocí těchto příkazů můžete přeskočit prostřednictvím kódu (funkce spustit, samozřejmě, ale přeskočí ladicí program přes ně).  
  
|Příkaz klávesnice|Příkaz nabídky|Popis|  
|----------------------|------------------|-----------------|  
|**F10**|**Krok přes**|Pokud aktuální řádek obsahuje volání funkce **Krokovat s přeskočením** spustí kód a pozastaví provádění na prvním řádku kódu po vrácení volané funkce.|  
|**Shift+F11**|**Krokovat s Vystoupením**|**Krokovat s Vystoupením** pokračuje v běhu programu a pozastaví provádění kódu, když aktuální funkce vrátí (přeskočí ladicí program pomocí aktuální funkce).|  
  
> [!TIP]
>  Pokud je potřeba najít vstupní bod ve vaší aplikaci, začněte s **F10** nebo **F11**. Tyto příkazy jsou často užitečné při kontrole stavu vaší aplikace nebo při pokusu o další informace o jeho spuštění toku.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Spuštění do určitého umístění nebo – funkce  
 Preferovanou metodu ladění kódu, tyto metody jsou často užitečné při víte přesně jaký kód, který chcete zkontrolovat nebo alespoň víte, kde chcete spustit ladění.  
  
-   **Nastavte zarážky v kódu**  
  
     Pro nastavení jednoduché zarážky v kódu, otevřete zdrojový soubor v editoru sady Visual Studio. Nastavte kurzor na řádek kódu, ve které chcete pozastavit provádění a klikněte pravým tlačítkem na v okně kódu zobrazit kontextovou nabídku a zvolte **zarážky nebo vložit zarážku** (nebo stiskněte klávesu **F9**). Ladicí program pozastaví provádění doprava, před provedením řádku.  
  
     ![Nastavit zarážku](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Zarážky v sadě Visual Studio poskytují další funkce, jako je například podmíněné zarážky a sledované body. Zobrazit [pomocí zarážek](../debugger/using-breakpoints.md).  
  
-   **Spuštění do umístění kurzoru**  
  
     Ke spuštění do umístění kurzoru, umístěte kurzor na řádek kódu v okně zdroje. V místní nabídce editoru (klikněte pravým tlačítkem v editoru), zvolte **spustit ke kurzoru**. To je jako nastavení dočasné zarážky.  
  
-   **Ručně proniknout do kódu**  
  
     Chcete-li rozdělit na další dostupný řádek kódu ve spuštěné aplikaci, zvolte **ladění**, **přerušit vše** (klávesnice: **Ctrl + Alt + Break**).  
  
     Pokud můžete přerušit provádění kódu bez odpovídajícího zdroje nebo symbolu (.pdb) soubory), ladicí program zobrazí **zdrojové soubory nebyly nalezeny** nebo **symboly nebyly nalezeny** stránky, které vám pomohou najít příslušné soubory. Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nelze získat přístup k podpůrným souborům, budete moci stále ladit instrukce sestavení v okně zpětný překlad.  
  
-   **Spusťte funkci v zásobníku volání**  
  
     V **zásobník volání** okno (dostupný během ladění), vyberte funkci, klepněte pravým tlačítkem myši a zvolte **spustit ke kurzoru**. Vizuální trasování zásobníku volání, viz [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Spusťte funkci zadanou na základě názvu**  
  
     Poznáte, ladicí program ke spuštění vaší aplikace, dokud nedosáhne určenou funkci. Můžete zadat funkce podle názvu nebo je možné ji zvolit ze zásobníku volání.  
  
     Chcete-li zadat funkce podle názvu, zvolte **ladění**, **Nová zarážka**, **zarážku funkce**, zadejte název funkce a identifikovatelné informace.  
  
     ![Dialogové okno nové zarážky](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Pokud funkce je přetížena nebo je ve více oborů názvů, můžete vybrat funkce, které chcete zahrnout **vybrat zarážky** dialogové okno.  
  
     ![Vybrat zarážky – dialogové okno](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Přesuňte ukazatel Změna toku provádění  
 Když ladicí program je pozastavený, můžete přesunout ukazatele na instrukci nastavení dalšího příkazu ke spuštění kódu. Žlutá šipka na okraji zdroje nebo okno zpětného překladu označuje umístění pro další příkaz, který se spustí. Přesunutím této šipky můžete přeskočit část kódu nebo vrátit na dříve provedený řádek. To můžete použít v situacích, jako je například vynechání části kódu, který obsahuje známou chybu.  
  
 ![Priklad2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Nastavení dalšího příkazu ke spuštění, použijte jeden z následujících postupů:  
  
-   V okně zdroje přetáhněte žlutou šipku do umístění, ve které chcete nastavit další příkaz ve stejném zdrojovém souboru  
  
-   V okně zdroje nastavte kurzor na řádek, který chcete spustit jako další, klikněte pravým tlačítkem a zvolte **nastavit další příkaz**.  
  
-   V okně zpětný překlad nastavte kurzor na instrukci sestavení, který chcete spustit jako další, klikněte pravým tlačítkem na a zvolte **nastavit další příkaz**.  
  
> [!CAUTION]
>  Nastavení dalšího příkazu způsobí, že čítač programu můžete přejít přímo do nového umístění. Použijte tento příkaz opatrně:  
> 
> - Pokyny mezi body staré a nové spuštění nebudou provedeny.  
>   -   Pokud přesunete bod spuštění zpět, nebudou intervenující pokyny vráceny vrátit zpět.  
>   -   Přesunutí dalšího příkazu do jiné funkce nebo rozsahu obvykle za následek poškození zásobníku volání, což způsobí runtime chybu nebo výjimku. Při přesunutí dalšího příkazu do jiného oboru, ladicí program otevře dialogové okno s upozorněním a dává vám možnost zrušit operaci. V jazyce Visual Basic nemůžete přesunout do jiného oboru nebo funkce další příkaz.  
>   -   V nativním kódu C++ Pokud máte kontroly za běhu povoleno, nastavení dalšího příkazu může způsobit výjimku, která je vyvolána, když spuštění dosáhne konce metody.  
>   -   Když upravit a pokračovat je povoleno, **nastavit další příkaz** nezdaří, pokud jste provedli změny, které upravit a pokračovat nemůže ihned opětovně mapovat. Tato situace může nastat, například, pokud se po úpravě kódu v bloku catch. Pokud k tomu dojde, zobrazí se vám chybová zpráva s oznámením, že operace není podporována.  
> 
> [!NOTE]
>  Ve spravovaném kódu nelze přesunout další příkaz za následujících podmínek:  
> 
> - Další příkaz je v jiné metody než aktuální příkaz.  
>   -   Ladění bylo zahájeno pomocí Just-In-Time ladění.  
>   -   Probíhá akce callstack unwind.  
>   -   Byla vyvolána výjimka System.StackOverflowException or System.Threading.ThreadAbortException.  
  
 Následující příkaz nelze nastavit, pokud vaše aplikace právě aktivně běží. Pokud chcete nastavit další příkaz, musí být ladicí program v režimu pozastavení.  
  
## <a name="step-into-non-user-code"></a>Krokovat s vnořením kód nepocházející od uživatele  
 Ve výchozím nastavení, ladicí program pokusí zobrazit pouze váš kód aplikace během ladění, která je určená názvem ladicího programu *pouze můj kód*. (Viz [pouze můj kód](../debugger/just-my-code.md) jak to funguje pro různé typy projektů a jazyků a jak může přizpůsobit chování.) Ale někdy při ladění, můžete se podívat na kódu architektury, kód knihovny třetích stran nebo volání do operačního systému (systémová volání).  
  
 Funkce pouze můj kód můžete vypnout tak, že přejdete do **nástroje** / **možnosti** / **ladění** a zrušte **povolit volbu pouze vlastní kód** zaškrtávací políčko.  
  
 Pokud funkce pouze můj kód je zakázán, ladicího programu můžete krokovat s vnořením neuživatelský kód a kód nepatřící uživateli se zobrazí v oknech ladicího programu.  
  
> [!NOTE]
>  Funkce pouze můj kód není podporována pro projekty zařízení.  
  
 **Krokovat přes systémová volání**  
  
 Pokud jste načetli symboly ladění pro kód systému a není povolena funkce pouze můj kód, můžete krokovat s vnořením do volání systému stejně jako u ostatních volání.  
  
 Pro přístup k souborům symbolů společnosti Microsoft, naleznete v tématu [použít servery symbolů k vyhledání souborů symbolů nenainstalovaných v místním počítači](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) v [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tématu.  
  
 Načtení symbolů pro určité součásti systému při ladění:  
  
1.  Otevřete okno moduly (klávesnice: **Ctrl + Alt + U**).  
  
2.  Vyberte modul, který chcete načíst symboly.  
  
     Poznáte, které moduly mají načtené symboly pohledem **Status symbolu** sloupce.  
  
3.  Zvolte **načíst symboly** v místní nabídce.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Krokovat přes vlastnosti a operátory ve spravovaném kódu  
 Ladicí program přes vlastnosti a operátory ve spravovaném kódu ve výchozím nastavení. Ve většině případů to poskytuje lepší možnosti ladění. Chcete-li povolit krokování s vnořením do vlastností nebo operátorů, zvolte **ladění** / **možnosti**. Na **ladění** / **Obecné** zrušte **Krokovat přes vlastnosti a operátory (pouze spravované)** zaškrtávací políčko





