---
title: Vyhledání kódu s ladicím programem | Dokumentace Microsoftu
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
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "70222651"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Procházení kódu s ladicím programu sady Visual Studio

Ladicí program sady Visual Studio můžete procházet kód pro kontrolu stavu aplikace a zobrazit jeho spuštění toku. Klávesové zkratky, příkazy ladění, zarážky a další funkce můžete rychle dostali k kód, který chcete prověřit. Seznámení se s navigačními příkazy ladicího programu a zkratky umožňuje rychlejší a snazší najít a řešení potíží v aplikacích.  Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="basic-debugging"></a>Základní ladění

Chcete-li aplikaci spustit s připojeným ladícím nástrojem, stiskněte **F5**vyberte **ladění** > **spustit ladění**, nebo vyberte zelenou šipku na panelu nástrojů sady Visual Studio.

 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Při ladění, zobrazí žlutý zvýraznění řádek kódu, který provede další.

 ![DBG&#95;Základy&#95;přerušit&#95;režimu](../debugger/media/dbg_basics_break_mode.png "režimu pozastavení")

Většina okna ladicího programu, jako je třeba **moduly** a **Watch** okna, jsou k dispozici pouze ladicí program je spuštěn. Některé funkce, jako je například zobrazení hodnot proměnných v ladicího programu **místní hodnoty** okno nebo vyhodnocování výrazů v **Watch** okna, jsou k dispozici pouze tehdy, když ladicí program je pozastaven na zarážce, také nazývané *režimu pozastavení*.

V režimu přerušení je spuštění aplikace pozastavené při funkce a proměnné, a objekty zůstanou v paměti. Můžete zkoumat pozice prvků a stavy pro vyhledání porušení nebo chyb. U některých typů projektů lze také provést úpravy aplikace v režimu přerušení. Na video zobrazující těchto funkcí naleznete v tématu [Začínáme s ladicím programem](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Pokud rozdělíte v kódu, který nemá zdroje nebo symbolu (*PDB*) souborů načtených, ladicí program zobrazí **zdrojové soubory nebyly nalezeny** nebo **symboly nebyly nalezeny** stránka, která vám může pomoct Najít a načíst soubory. Zobrazit [zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nelze načíst symbol nebo zdrojové soubory, budete moci stále ladit instrukce sestavení v **zpětný překlad** okna.

Není vždy nutné pro spuštění ladění pomocí spuštění aplikace na začátku. Můžete také stisknout klávesu **F11** k [krokování s vnořením do kódu](#BKMK_Step_into__over__or_out_of_the_code), stiskněte klávesu **F10** k [krok za kód](#BKMK_Step_over_Step_out), nebo [spuštění do určitého umístění nebo funkce](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Krokovat kód

Krok příkazy ladicího programu můžete zkontrolovat stav vaší aplikace nebo si přečtěte Další informace o jeho spuštění toku.

Pokud je potřeba najít vstupní bod ve vaší aplikaci, začněte s **F10** nebo **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> S vnořením do kódu řádek po řádku

Chcete-li zastavit na každém řádku kódu nebo příkazu při ladění, použijte **ladění** > **Krokovat s vnořením**, nebo stiskněte klávesu **F11**.

Ladicí program vás provede příkazy kódu, nikoli fyzické řádky. Například `if` klauzule může být napsána na jednom řádku:

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

Ale při krokování s vnořením tohoto řádku, ladicí program zpracuje podmínku jako jeden krok a následek jako jiný. V předchozím příkladu je podmínka pravdivá.

U volání vnořené funkce **Krokovat s vnořením** přejde k nejhlouběji vnořené funkci. Například, pokud používáte **Krokovat s vnořením** na volání, například `Func1(Func2())`, ladicí program vstoupí do funkce `Func2`.

>[!TIP]
>Při spuštění každého řádku kódu, můžete najedete myší proměnných najdete v jejich hodnoty nebo použít [lokální](autos-and-locals-windows.md) a [Watch](watch-and-quickwatch-windows.md) windows ke sledování hodnoty změnit. Můžete také vizuální trasování zásobníku volání při krokování do funkce. Zobrazit [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a> Krokovat kód a přeskočit některé funkce

Funkce nemusí záleží při ladění nebo ho znáte funguje, jako jsou dobře otestovaný knihovny kódu. Chcete-li přeskočit prostřednictvím kódu můžete použít následující příkazy. Funkce spustit, ale je přeskočen ladicí program.

|Příkaz klávesnice|Příkaz nabídky ladění|Popis|
|----------------------|------------------|-----------------|
|**F10**|**Krok přes**|Pokud aktuální řádek obsahuje volání funkce **Krokovat s přeskočením** spouští kód, pak po volané funkci vrátí pozastaví provádění na prvním řádku kódu.|
|**SHIFT**+**F11**|**Krokovat s Vystoupením**|**Krokovat s Vystoupením** pokračuje v běhu programu a pozastaví provádění kódu po návratu aktuální funkce. Ladicí program přeskočí prostřednictvím aktuální funkce.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Spuštění do určitého umístění nebo – funkce

Můžete chtít spustit přímo do určitého umístění nebo funkce, když víte přesně jaký kód, který chcete zkontrolovat nebo víte, kde chcete spustit ladění.

### <a name="run-to-a-breakpoint-in-code"></a>Spusťte zarážku v kódu

Chcete-li nastavení jednoduché zarážky v kódu, klikněte na levém okraji vedle řádku kódu, ve které chcete pozastavit provádění. Můžete také vybrat řádku a stisknutím klávesy **F9**vyberte **ladění** > **Přepnout zarážku**, nebo klikněte pravým tlačítkem a vyberte **zarážku**  >  **Vložit zarážku**. Zarážka se zobrazí jako červená tečka na levém okraji vedle řádku kódu. Ladicí program přeruší provádění, stačí před provedením řádku.

![Nastavit zarážku](../debugger/media/dbg_basics_setbreakpoint.png "nastavte zarážku")

Zarážky v sadě Visual Studio poskytují další funkce, jako je například podmíněné zarážky a sledované body. Podrobnosti najdete v tématu [pomocí zarážek](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Spusťte zarážku funkce

Poznáte, ladicí program ke spuštění, dokud nedosáhne určenou funkci. Můžete zadat funkce podle názvu nebo je možné ji zvolit ze zásobníku volání.

**Chcete-li určit zarážku funkce podle názvu**

1. Vyberte **ladění** > **Nová zarážka** > **funkce zarážky**

1. V **Nová zarážka funkce** dialogové okno, zadejte název funkce a vyberte svůj jazyk.

   ![Dialogové okno nové zarážky funkce](../debugger/media/dbg_execution_newbreakpoint.png "Nová zarážka funkce")

1. Vyberte **OK**.

Pokud je funkce přetížena nebo ve víc než jeden obor názvů, můžete zvolit ten, který chcete v **zarážky** okna.

![Přetížené funkce zarážky](../debugger/media/dbg_execution_overloadedbreakpoints.png "přetížené funkce zarážky")

**Vyberte zarážku funkce ze zásobníku volání**

1. Při ladění, otevřete **zásobník volání** okna tak, že vyberete **ladění** > **Windows** > **zásobník volání**.

1. V **zásobník volání** okna, klikněte pravým tlačítkem na funkci a vyberte **provést do pozice kurzoru**, nebo stiskněte klávesu **Ctrl**+**F10**.

Vizuální trasování zásobníku volání, viz [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Spuštění do umístění kurzoru

Ke spuštění do umístění kurzoru, ve zdrojovém kódu nebo **zásobník volání** okna, vyberte řádek, který má na zarážku, klikněte pravým tlačítkem a vyberte **provést do pozice kurzoru**, nebo stiskněte klávesu **Ctrl** + **F10**. Výběr **provést do pozice kurzoru** je stejná jako nastavení dočasné zarážky.

### <a name="run-to-click"></a>Běžet do kliknutí

Během pozastavení v ladicím programu, můžete najedete myší příkaz ve zdrojovém kódu nebo **zpětný překlad** okna a vyberte **běžet do tohoto místa** ikonou zelené šipky. Pomocí **běžet do kliknutí** eliminuje nutnost nastavení dočasné zarážky.

![Běžet do kliknutí](../debugger/media/dbg-run-to-click.png "běžet do kliknutí")

> [!NOTE]
> **Možnost spustit pro** je dostupná od začátku [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]v.

### <a name="manually-break-into-code"></a>Ručně proniknout do kódu

Pro přerušení v další dostupný řádek kódu ve spuštěné aplikaci vyberte **ladění** > **přerušit vše**, nebo stiskněte klávesu **Ctrl**+**Alt**  + **Přerušit**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a> Přesuňte ukazatel Změna toku provádění

Když ladicí program je pozastavený, žlutá šipka na okraji zdrojový kód nebo **zpětný překlad** okno označuje umístění pro další příkaz, který se spustí. Můžete změnit dalšího příkazu ke spuštění přesunutím této šipky. Můžete přeskočit část kódu nebo vrátit na předchozí řádek. Ukazatele je užitečné v situacích, jako je například vynechání části kódu, který obsahuje známou chybu.

 ![Přesuňte ukazatel](../debugger/media/dbg_basics_example3.gif "přesuňte ukazatel myši")

Chcete-li změnit dalšího příkazu ke spuštění, musí být ladicí program v režimu pozastavení. Ve zdrojovém kódu nebo **zpětný překlad** okna, přetáhněte žlutou šipku na jiný řádek, nebo klikněte pravým tlačítkem na řádku, které chcete spustit jako další a vyberte **nastavit další příkaz**.

Čítač programu přejde přímo na nové umístění a pokyny mezi staré a nové spuštění nebudou provedeny body. Nicméně pokud přesunete bod spuštění zpět, intervenující pokyny se vrátit zpět.

>[!CAUTION]
>- Přesunutí dalšího příkazu do jiné funkce nebo rozsahu obvykle za následek poškození zásobníku volání, což způsobí runtime chybu nebo výjimku. Při přesunutí dalšího příkazu do jiného oboru, ladicí program otevře dialogové okno s upozorněním a dává vám možnost zrušit operaci.
>- V jazyce Visual Basic nemůžete přesunout do jiného oboru nebo funkce další příkaz.
>- V nativním kódu C++ Pokud máte kontroly za běhu povoleno, nastavení dalšího příkazu může způsobit výjimku, která je vyvolána, když spuštění dosáhne konce metody.
>- Když upravit a pokračovat je povoleno, **nastavit další příkaz** nezdaří, pokud jste provedli změny, které upravit a pokračovat nemůže ihned opětovně mapovat. Tato situace může nastat, například, pokud se po úpravě kódu v bloku catch. Pokud k tomu dojde, chybová zpráva zjistíte, že operace není podporována.
>- Ve spravovaném kódu nelze přesunout další příkaz, pokud:
>   - Další příkaz je v jiné metody než aktuální příkaz.
>   - Ladění bylo zahájeno Just-In-Time ladění.
>   - Probíhá uvolnění zásobníku volání.
>   - Byla vyvolána výjimka System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Ladění kódu nepocházejícího od uživatele

Ve výchozím nastavení, ladicí program pokusí ladit jenom kód vaší aplikace tím, že nastavení nazývá *pouze můj kód*. Další podrobnosti o tom, jak tato funkce funguje pro různé typy projektů a jazyků a jak si můžete přizpůsobit, najdete v části [pouze můj kód](../debugger/just-my-code.md).

Podívat se na kód rozhraní framework, kód knihovny třetích stran nebo systémových volání při ladění, můžete zakázat pouze můj kód. V **nástroje** (nebo **ladění**) > **možnosti** > **ladění**, zrušte zaškrtnutí políčka **povolit volbu pouze vlastní kód** zaškrtávací políčko. Pokud funkce pouze můj kód je zakázán, neuživatelském kódu se zobrazí v oknech ladicího programu a ladicího programu můžete krokovat s vnořením neuživatelský kód.

> [!NOTE]
> Funkce pouze můj kód není podporována pro projekty zařízení.

### <a name="debug-system-code"></a>Ladění kódu systému

Pokud máte načíst symboly ladění pro kód systému Microsoft a zakázané funkce pouze můj kód, můžete krokovat s vnořením do volání systému stejně jako u ostatních volání.

Načtení symbolů společnosti Microsoft, naleznete v tématu [konfigurovat umístění symbolu a načítání](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Načtení symbolů pro určité součásti systému:**

1. Při ladění, otevřete **moduly** okna tak, že vyberete **ladění** > **Windows** > **moduly**, nebo stisknutím klávesy **Ctrl**+**Alt**+**U**.

1. V **moduly** okna, poznáte, které moduly mají symboly načteny v **Status symbolu** sloupce. Klikněte pravým tlačítkem na modul, který chcete načíst symboly pro a vyberte **načíst symboly**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Krokovat přes vlastnosti a operátory ve spravovaném kódu
 Ladicí program přes vlastnosti a operátory ve spravovaném kódu ve výchozím nastavení. Ve většině případů to poskytuje lepší možnosti ladění. Chcete-li povolit krokování s vnořením do vlastností nebo operátorů, zvolte **ladění** > **možnosti**. Na **ladění** > **Obecné** zrušte **Krokovat přes vlastnosti a operátory (pouze spravované)** zaškrtávací políčko.

## <a name="see-also"></a>Viz také:
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
