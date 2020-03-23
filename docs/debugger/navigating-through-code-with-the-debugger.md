---
title: Navigace v kódu s ladicím programem | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302117"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Procházení kódu pomocí ladicího programu Visual Studia

Ladicí program visual studio vám může pomoci procházet kód, zkontrolovat stav aplikace a zobrazit její tok spuštění. Pomocí klávesových zkratek, ladicích příkazů, zarážek a dalších funkcí se můžete rychle dostat ke kódu, který chcete prozkoumat. Znalost příkazů a zkratek ladicího programu usnadňuje a usnadňuje vyhledání a řešení problémů s aplikacemi.  Pokud je to poprvé, co jste se pokusili ladit kód, můžete si přečíst [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md) a ladění [techniky a nástroje](../debugger/write-better-code-with-visual-studio.md) před procházením tohoto článku.

## <a name="get-into-break-mode"></a>Přepnout se do "break mode"

V *režimu přerušení*je spouštění aplikací pozastaveno, zatímco funkce, proměnné a objekty zůstávají v paměti. Jakmile je ladicí program v režimu přerušení, můžete procházet kódem. Nejběžnější způsoby, jak se rychle dostat do režimu přerušení, je buď:

- Začněte krokování kódu stisknutím **kláves Y10** nebo **F11**. To vám umožní rychle najít vstupní bod aplikace, pak můžete pokračovat stisknutím klávesových příkazů pro navigaci v kódu.

- [Spusťte do určitého umístění nebo funkce](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), například [nastavením zarážky](using-breakpoints.md) a spuštěním aplikace.

   Například z editoru kódu v sadě Visual Studio můžete použít příkaz **Spustit kurzor** ke spuštění aplikace, připojeného ladicího programu a přepnutí do režimu přerušení a potom **f11** k navigaci v kódu.

   ![Spuštění kurzoru a krok do kódu](../debugger/media/navigate-code-code-stepping.gif "Spuštění kurzoru a krok do kódu")

Jakmile v režimu přerušení, můžete použít různé příkazy procházet kód. V režimu přerušení můžete prozkoumat hodnoty proměnných a vyhledat porušení nebo chyby. U některých typů projektů můžete také provést úpravy aplikace v režimu přerušení.

Většina ladicích oken, jako jsou **moduly** a **okna kukátka,** jsou k dispozici pouze v době, kdy je ladicí program připojený k vaší aplikaci. Některé funkce ladicího programu, jako je například zobrazení hodnot proměnných v okně **Locals** nebo vyhodnocení výrazů v okně **Kukátka,** jsou k dispozici pouze v době, kdy je ladicí program pozastaven (to znamená v režimu přerušení).

> [!NOTE]
> Pokud se rozdělíte na kód, který nemá načtené soubory zdroje nebo symbolu (*Pdb),* ladicí program zobrazí **stránku Zdrojové soubory, které nebyly nalezeny,** nebo **stránku Symboly nebyly nalezeny,** která vám pomůže najít a načíst soubory. Viz [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nemůžete načíst symbol nebo zdrojové soubory, můžete stále ladit pokyny sestavení v okně **Demontáž.**

## <a name="step-through-code"></a>Krokovat kódem

Příkazy kroku ladicího programu vám pomůžou zkontrolovat stav aplikace nebo se dozvědět víc o toku jeho spuštění.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Krok do kódu řádek po řádku

Chcete-li zastavit každý příkaz při ladění, použijte **ladění** > **krok do**, nebo stiskněte **klávesu F11**.

Ladicí program prochází příkazy kódu, nikoli fyzické řádky. Například `if` klauzule může být napsána na jednom řádku:

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

Však při krok do tohoto řádku ladicí program považuje podmínku jako jeden krok a důsledkem jako jiný. V předchozím příkladu je podmínka true.

Při volání vnořené funkce **krok do** kroků do nejhlouběji vnořené funkce. Například pokud použijete **Krok do** `Func1(Func2())`na volání, jako je `Func2`, ladicí program kroky do funkce .

>[!TIP]
>Při provádění každého řádku kódu můžete najet nad proměnnými, abyste viděli jejich hodnoty, nebo pomocí oken [Locals](autos-and-locals-windows.md) a [Watch](watch-and-quickwatch-windows.md) sledovat, jak se hodnoty mění. Můžete také vizuálně sledovat [zásobník volání](how-to-use-the-call-stack-window.md) při krokování do funkcí. (Pouze pro Visual Studio Enterprise, naleznete [v tématu Map metody v zásobníku volání při ladění).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Krokovat kódem a přeskočit některé funkce

Při ladění se nemusí starat o funkci nebo víte, že funguje, jako je dobře testovaný kód knihovny. Následující příkazy můžete použít k přeskočení kódu při krokování kódu. Funkce stále spustit, ale ladicí program přeskočí nad nimi.

|Klávesnice, příkaz|Příkaz nabídky ladění|Popis|
|----------------------|------------------|-----------------|
|**F10**|**Krok přes**|Pokud aktuální řádek obsahuje volání funkce, **krok přes** spustí kód, pozastaví spuštění na prvním řádku kódu po volání funkce vrátí.|
|**Posun**+**F11**|**Krok ven**|**Krok ven** pokračuje ve spuštění kódu a pozastaví provádění, když se vrátí aktuální funkce. Ladicí program přeskočí aktuální funkce.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Spuštění do určitého umístění nebo funkce

Můžete raději spustit přímo do určitého umístění nebo funkce, když přesně víte, jaký kód chcete zkontrolovat, nebo víte, kde chcete začít ladění.

### <a name="run-to-a-breakpoint-in-code"></a>Spuštění na zarážku v kódu

Chcete-li nastavit jednoduchou zarážku v kódu, klikněte na zcela levý okraj vedle řádku kódu, kde chcete pozastavit provádění. Můžete také vybrat čáru a stisknout **klávesu F9**, vybrat možnost **Ladění** > **přepínací zarážky nebo**klepnout pravým tlačítkem myši a vybrat**zarážku vložení zarážky** **.** >  Zarážka se zobrazí jako červená tečka v levém okraji vedle řádku kódu. Ladicí program pozastaví spuštění těsně před spuštěním řádku.

![Nastavení zarážky](../debugger/media/dbg_basics_setbreakpoint.png "Nastavení zarážky")

Zarážky v sadě Visual Studio poskytují bohatou sadu dalších funkcí, jako jsou například podmíněné zarážky a stopovací body. Podrobnosti naleznete [v tématu Použití zarážek](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Spustit za zarážku funkce

Ladicí program můžete sdělit spuštění, dokud nedosáhne zadané funkce. Funkci můžete zadat podle názvu nebo ji můžete vybrat ze zásobníku volání.

**Určení zarážky funkce podle názvu**

1. Vybrat **ladění** > **nové zarážky zarážky zarážky** > **Function Breakpoint**

1. V dialogovém okně **Zarážky nové funkce** zadejte název funkce a vyberte její jazyk.

   ![Dialogové okno Zarážky nové funkce](../debugger/media/dbg_execution_newbreakpoint.png "Zarážky nové funkce")

1. Vyberte **OK**.

Pokud je funkce přetížena nebo ve více než jednom oboru názvů, můžete zvolit požadovaný v okně **Zarážky.**

![Přetížené zarážky funkce](../debugger/media/dbg_execution_overloadedbreakpoints.png "Přetížené zarážky funkce")

**Výběr zarážky funkce ze zásobníku volání**

1. Při ladění otevřete okno **Zásobník volání** výběrem **ladění** > **zásobníku volání systému****Windows** > .

1. V okně **Zásobník volání** klepněte pravým tlačítkem myši na funkci a vyberte příkaz **Spustit kurzor**nebo stiskněte **kombinaci kláves Ctrl**+**F10**.

Chcete-li vizuálně sledovat zásobník volání, naleznete [v tématu Map metody v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Spuštění do umístění kurzoru

Chcete-li spustit do umístění kurzoru, vyberte ve zdrojovém kódu nebo v okně **Zásobník volání** řádek, na kterém chcete přerušit, klepněte pravým tlačítkem myši a vyberte **Spustit kurzor**nebo stiskněte **klávesu Ctrl**+**F10**. Výběr **spustit kurzor** je jako nastavení dočasné zarážky.

### <a name="run-to-click"></a>Běžet do kliknutí

Při pozastavení v ladicím programu můžete najet ukazatel na příkaz ve zdrojovém kódu nebo v okně **Demontáž** a vybrat ikonu **Spustit spuštění zde** zelené šipky. Použití **spustit klepnutí** eliminuje potřebu nastavit dočasnou zarážku.

![Běžet do kliknutí](../debugger/media/dbg-run-to-click.png "Běžet do kliknutí")

> [!NOTE]
> **Spustit na tlačítko** je [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]k dispozici od .

### <a name="manually-break-into-code"></a>Ruční rozdělení do kódu

Chcete-li přerušit další dostupný řádek kódu v běžící aplikaci, vyberte **možnost Ladění** > **zalomení všech**nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Přesunutím ukazatele změníte tok spuštění.

Zatímco ladicí program je pozastaven, žlutá šipka v okraji zdrojového kódu nebo **dismontážní** okno označuje umístění další příkaz, který má být proveden. Další příkaz můžete změnit tak, že přesunete tuto šipku. Můžete přeskočit část kódu nebo se vrátit na předchozí řádek. Přesunutí ukazatele je užitečné pro situace, jako je například přeskočení části kódu, který obsahuje známou chybu.

 ![Přesunutí ukazatele](../debugger/media/dbg_basics_example3.gif "Přesunutí ukazatele")

Chcete-li změnit další příkaz provést, ladicí program musí být v režimu přerušení. Ve zdrojovém kódu nebo okně **Demontáž** přetáhněte žlutou šipku na jinou čáru nebo klepněte pravým tlačítkem myši na řádek, který chcete provést jako další, a vyberte **Nastavit další příkaz**.

Čítač programu přeskočí přímo do nového umístění a pokyny mezi starým a novým bodem provádění nebudou provedeny. Pokud však přesunete bod spuštění zpět, nebudou pokyny pro zasahování vrátit zpět.

>[!CAUTION]
>- Přesunutí dalšího příkazu na jinou funkci nebo obor obvykle vede k poškození zásobníku volání, což způsobuje chybu nebo výjimku za běhu. Pokud se pokusíte přesunout další příkaz do jiného oboru, ladicí program otevře dialogové okno s upozorněním a dává vám možnost operaci zrušit.
>- V jazyce Visual Basic nelze přesunout další příkaz do jiného oboru nebo funkce.
>- V nativním jazyce C++, pokud máte povoleny kontroly za běhu, nastavení dalšího příkazu může způsobit, že dojde k vyvolání výjimky, když spuštění dosáhne konce metody.
>- Pokud je povoleno upravit a pokračovat, **funkce Nastavit další příkaz** se nezdaří, pokud jste provedli úpravy, které nelze okamžitě přemapovat. K tomu může dojít, například pokud jste upravili kód uvnitř bloku catch. V takovém případě se zobrazí chybová zpráva, že operace není podporována.
>- Ve spravovaném kódu nelze přesunout další příkaz, pokud:
>   - Další příkaz je v jiné metodě než aktuální příkaz.
>   - Ladění bylo spuštěno laděním Just-In-Time.
>   - Probíhá unwind zásobníku volání.
>   - Byla vyvolána výjimka System.StackOverflowException nebo System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Ladění neuživatelského kódu

Ve výchozím nastavení se ladicí program pokusí ladit pouze kód aplikace povolením nastavení s názvem *Pouze můj kód*. Další podrobnosti o tom, jak tato funkce funguje pro různé typy projektů a jazyky a jak ji můžete přizpůsobit, naleznete [v tématu Pouze můj kód](../debugger/just-my-code.md).

Chcete-li se podívat na kód architektury, kód knihovny jiného výrobce nebo systémová volání při ladění, můžete zakázat pouze můj kód. V **nástrojích** (nebo **ladění)**> **možnosti** > **ladění**zrušte zaškrtnutí políčka **Povolit pouze můj kód.** Pokud je zakázán pouze můj kód, v oknech ladicího programu se zobrazí neuživatelský kód a ladicí program může vstoupit do kódu uživatele, který není uživatelem.

> [!NOTE]
> Pouze můj kód není podporován pro projekty zařízení.

### <a name="debug-system-code"></a>Kód systému ladění

Pokud jste načetli ladicí symboly pro systémový kód společnosti Microsoft a zakázali pouze můj kód, můžete vstoupit do systémového volání stejně jako jakékoli jiné volání.

Informace o načtení symbolů společnosti Microsoft naleznete [v tématu Konfigurace umístění symbolů a možností načítání](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Chcete-li načíst symboly pro určitou součást systému:**

1. Během ladění otevřete okno **Moduly** tak, že vyberete **Ladění** > **modulů****systému Windows** > nebo stisknete **kombinaci kláves Ctrl**+**Alt**+**U**.

1. V okně **Moduly** můžete zjistit, které moduly mají symboly načtené ve sloupci **Stav symbolu.** Klikněte pravým tlačítkem myši na modul, pro který chcete načíst symboly, a vyberte **možnost Načíst symboly**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Krok ovat do vlastností a operátorů ve spravovaném kódu
 Ladicí program kroky přes vlastnosti a operátory ve spravovaném kódu ve výchozím nastavení. Ve většině případů to poskytuje lepší ladění zkušenosti. Chcete-li povolit krokování do vlastností nebo operátorů, zvolte**Možnosti** **ladění** > . Na stránce **Debugging** > **General** zrušte zaškrtnutí políčka Krok **ovat vlastnosti a operátory (pouze spravované).**

## <a name="see-also"></a>Viz také
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
