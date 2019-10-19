---
title: Navigace v kódu pomocí ladicího programu | Microsoft Docs
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
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "70222651"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Procházení kódu pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio vám může pomáhat s procházením kódu pro kontrolu stavu aplikace a zobrazení toku provádění. Pomocí klávesových zkratek, příkazů ladění, zarážek a dalších funkcí můžete rychle získat kód, který chcete prošetřit. Znalost navigačních příkazů a zástupců ladicího programu usnadňuje a usnadňuje hledání a řešení problémů s aplikacemi.  Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="basic-debugging"></a>Základní ladění

Chcete-li spustit aplikaci pomocí připojeného ladicího programu, stiskněte klávesu **F5**, vyberte možnost **ladění**  > **Spustit ladění**nebo vyberte zelenou šipku na panelu nástrojů sady Visual Studio.

 ![Základní&#95;informace&#95;o&#95;DBG Start ladění](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Během ladění zobrazuje žlutý zvýraznění řádek kódu, který se spustí jako další.

 ![Režim&#95;přerušení&#95;&#95;základy dbg](../debugger/media/dbg_basics_break_mode.png "Režim přerušení")

Většina oken ladicího programu, jako jsou **moduly** a **sledovací** okna, jsou k dispozici pouze v době, kdy je spuštěn ladicí program. Některé funkce ladicího programu, například zobrazení hodnot proměnných v okně **místních** hodnot nebo vyhodnocování výrazů v okně **kukátka** jsou k dispozici pouze v případě, že ladicí program je pozastaven na zarážce, označovaný také jako *režim přerušení*.

V režimu pozastavení je spuštění aplikace pozastaveno, zatímco funkce, proměnné a objekty zůstávají v paměti. Můžete zkontrolovat umístění a stavy prvků a vyhledat porušení nebo chyby. U některých typů projektů můžete také provádět úpravy aplikace v režimu pozastavení. Video znázorňující tyto funkce naleznete v tématu [Začínáme s ladicím programem](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Pokud přerušíte kód, který nemá načítat zdrojové soubory nebo soubory symbolů (*PDB*), ladicí program zobrazí stránku **nenalezené zdrojové soubory** nebo **symboly nebyly nalezeny** , které vám pomohou najít a načíst soubory. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nemůžete načíst symbol nebo zdrojové soubory, můžete přesto ladit pokyny sestavení v okně zpětného **překladu** .

Nemusíte vždy spouštět ladění spuštěním aplikace na začátku. Můžete také stisknutím klávesy **F11** přejít ke [kódu](#BKMK_Step_into__over__or_out_of_the_code), stisknout klávesu **F10** a [krokovat kód](#BKMK_Step_over_Step_out)nebo [spustit do konkrétního umístění nebo funkce](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Krokovat kód

Příkazy kroku ladicího programu vám pomůžou zkontrolovat stav aplikace nebo zjistit další informace o jeho toku provádění.

Pokud potřebujete najít vstupní bod v aplikaci, začněte nástrojem **F10** nebo **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Krokovat s kódem řádek po řádku

Chcete-li zastavit na každém řádku kódu nebo příkazu během ladění, použijte  > **Krok** **ladění** do nebo stiskněte klávesu **F11**.

Ladicí program provede kroky kódu, ne fyzických řádků. Například klauzuli `if` lze zapsat na jeden řádek:

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

Nicméně když na tento řádek zadáte krok, ladicí program považuje podmínku za jeden krok a jako další. V předchozím příkladu je podmínka pravdivá.

U vnořeného volání funkce **Krok do** nejhlouběji vnořené funkce. Například pokud použijete **Krok do** pro volání, jako je `Func1(Func2())`, ladicí program kroky do funkce `Func2`.

>[!TIP]
>Při provádění jednotlivých řádků kódu můžete umístit ukazatele myši nad proměnné, abyste viděli jejich hodnoty, nebo použít [místní](autos-and-locals-windows.md) okna a [kukátka](watch-and-quickwatch-windows.md) ke sledování změn hodnot. Můžete také vizuálně sledovat zásobník volání při krokování do funkcí. Viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a>Krokovat kód a přeskočit některé funkce

Při ladění nemůžete zajímat funkci, nebo víte, že funguje, jako dobře testovaný kód knihovny. Pomocí následujících příkazů můžete přeskočit kód. Funkce se pořád spustí, ale ladicí program je přeskočí.

|Příkaz klávesnice|Příkaz nabídky Ladit|Popis|
|----------------------|------------------|-----------------|
|**F10**|**Krokovat**|Pokud aktuální řádek obsahuje volání funkce, **Krok over** spustí kód a poté pozastaví provádění na prvním řádku kódu po návratu volané funkce.|
|**Shift** +**F11**|**Krok ven**|**Krok ven** pokračuje v běhu kódu a pozastaví provádění, když se vrátí aktuální funkce. Ladicí program přeskočí aktuální funkci.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Spustit do konkrétního umístění nebo funkce

Můžete chtít spustit přímo na konkrétní umístění nebo funkci, pokud přesně víte, jaký kód chcete zkontrolovat, nebo víte, kde chcete spustit ladění.

### <a name="run-to-a-breakpoint-in-code"></a>Spustit na zarážku v kódu

Chcete-li v kódu nastavit jednoduchou zarážku, klikněte na levý levý okraj vedle řádku kódu, kde chcete pozastavit provádění. Můžete také vybrat řádek a stisknout klávesu **F9**, vybrat položku **ladění**  > **Přepnout zarážku**, nebo kliknout pravým tlačítkem a vybrat **zarážku**  > **Vložit zarážku**. Zarážka se zobrazí jako červená tečka v levém okraji vedle řádku kódu. Ladicí program pozastaví provádění těsně před spuštěním řádku.

![Nastavit zarážku](../debugger/media/dbg_basics_setbreakpoint.png "Nastavení zarážky")

Zarážky v sadě Visual Studio poskytují bohatou sadu dalších funkcí, jako jsou například podmíněné zarážky a trasováním. Podrobnosti najdete v tématu [použití zarážek](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Spustit na zarážku funkce

Ladicímu programu můžete sdělit, aby běžel, dokud nedosáhne zadané funkce. Můžete zadat funkci podle názvu nebo si ji můžete vybrat ze zásobníku volání.

**Určení zarážky funkce podle názvu**

1. Vyberte možnost **ladění**  > **novou** zarážku  > **zarážku funkce** .

1. V dialogovém okně **Nová zarážka funkce** zadejte název funkce a vyberte její jazyk.

   ![Nové zarážky funkce – dialogové okno](../debugger/media/dbg_execution_newbreakpoint.png "Nová zarážka funkce")

1. Vyberte **OK**.

Pokud je funkce přetížena nebo ve více než jednom oboru názvů, můžete zvolit, který chcete v okně **zarážky** .

![Přetížené zarážky funkcí](../debugger/media/dbg_execution_overloadedbreakpoints.png "Přetížené zarážky funkcí")

**Výběr zarážky funkce ze zásobníku volání**

1. Při ladění otevřete okno **zásobník volání** výběrem možnosti **ladění**  > **Windows**  > **zásobník volání**.

1. V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci a vyberte možnost **Spustit ke kurzoru**nebo stiskněte klávesovou **zkratku CTRL** +**F10**.

Vizuální trasování zásobníku volání naleznete v tématu [metody mapy v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Spustit do umístění kurzoru

Chcete-li spustit do umístění kurzoru, v okně zdrojový kód nebo **zásobník volání** vyberte řádek, u kterého chcete provést přerušení, klikněte pravým tlačítkem myši a vyberte možnost **Spustit ke kurzoru**nebo stiskněte klávesovou **zkratku CTRL** +**F10**. Výběr možnosti **Spustit na kurzor** je jako nastavení dočasné zarážky.

### <a name="run-to-click"></a>Běžet do kliknutí

Při pozastavení v ladicím programu můžete umístit ukazatel myši na příkaz ve zdrojovém kódu nebo v okně zpětného **překladu** a vybrat ikonu **spustit do sem** zelená ikona šipky. Když **kliknete na tlačítko Spustit,** eliminuje nutnost nastavit dočasnou zarážku.

![Spustit kliknutím](../debugger/media/dbg-run-to-click.png "Běžet do kliknutí")

> [!NOTE]
> **Možnost spustit do** je k dispozici od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Ručně přerušit do kódu

Chcete-li přerušit následující dostupný řádek kódu ve spuštěné aplikaci, vyberte možnost **ladění**  > **rozdělit vše**nebo stiskněte klávesu **CTRL** +**ALT** +**Break**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Přesunutím ukazatele myši změníte tok provádění.

I když je ladicí program pozastaven, žlutá šipka na okraji okna zdrojového kódu nebo **zpětný překlad** označuje umístění dalšího příkazu, který má být proveden. Další příkaz, který se má provést, můžete změnit přesunutím této šipky. Můžete přeskočit část kódu nebo se vrátit na předchozí řádek. Přesunutí ukazatele je užitečné v situacích, jako je například přeskočení oddílu kódu, který obsahuje známou chybu.

 ![Přesunout ukazatel](../debugger/media/dbg_basics_example3.gif "Přesunout ukazatel")

Chcete-li změnit další příkaz, který má být spuštěn, ladicí program musí být v režimu pozastavení. V okně zdrojový kód nebo **zpětný překlad** přetáhněte žlutou šipku na jiný řádek, nebo klikněte pravým tlačítkem na řádek, který chcete spustit, a vyberte **nastavit další příkaz**.

Čítač programu přejde přímo k novému umístění a pokyny mezi starými a novými body spuštění nejsou spuštěny. Pokud však přesunete bod provádění zpět, příslušné pokyny nejsou vráceny zpět.

>[!CAUTION]
>- Přesunutí dalšího příkazu do jiné funkce nebo oboru obvykle způsobí poškození zásobníku volání, což způsobuje chybu za běhu nebo výjimku. Pokud se pokusíte přesunout další příkaz do jiného oboru, ladicí program otevře dialogové okno s upozorněním a nabídne možnost zrušit operaci.
>- V Visual Basic nemůžete přesunout další příkaz do jiného oboru nebo funkce.
>- V nativním C++případě, pokud máte povolené kontroly za běhu, může nastavení dalšího příkazu způsobit vyvolání výjimky, pokud provádění dosáhne konce metody.
>- Pokud je povolená možnost upravit a pokračovat, **nastavení dalšího příkazu** se nepovede, pokud jste provedli úpravy, které upravit a pokračovat nemůže okamžitě přemapovat. K tomu může dojít například v případě, že jste upravovali kód v bloku catch. V takovém případě se zobrazí chybová zpráva s informacemi o tom, že operace není podporována.
>- Ve spravovaném kódu nelze přesunout další příkaz, pokud:
>   - Následující příkaz je v jiné metodě než aktuální příkaz.
>   - Ladění bylo zahájeno laděním za běhu.
>   - Probíhá unwind zásobníku volání.
>   - Byla vyvolána výjimka System. StackOverflowException nebo System. Threading. ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Ladit neuživatelský kód

Ve výchozím nastavení se ladicí program pokusí ladit pouze kód vaší aplikace povolením nastavení s názvem *pouze můj kód*. Další podrobnosti o tom, jak tato funkce funguje pro různé typy projektů a jazyky a jak je můžete přizpůsobit, najdete v tématu [pouze můj kód](../debugger/just-my-code.md).

Chcete-li se podívat na kód architektury, kód knihovny třetí strany nebo systémové volání během ladění, můžete zakázat Pouze můj kód. V **nabídce nástroje** (nebo **ladění**) > **Možnosti**  > **ladění**zrušte zaškrtnutí políčka **Povolit pouze můj kód** . Pokud je Pouze můj kód zakázaný, zobrazí se neuživatelský kód v oknech ladicího programu a ladicí program může Krokovat s neuživatelským kódem.

> [!NOTE]
> Pouze můj kód není pro projekty zařízení podporováno.

### <a name="debug-system-code"></a>Ladit systémový kód

Pokud jste načetli symboly ladění pro kód systému Microsoft a zakázané Pouze můj kód, můžete krokovat se systémovým voláním stejně jako jakékoli jiné volání.

Chcete-li načíst symboly společnosti Microsoft, přečtěte si téma [Konfigurace umístění symbolů a možnosti načítání](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Načtení symbolů pro konkrétní systémovou komponentu:**

1. Když ladíte, otevřete okno **moduly** výběrem možnosti **ladit**  > **moduly** > **Windows** nebo stisknutím klávesy **CTRL** +**ALT** +**U**.

1. V okně **moduly** můžete určit, které moduly mají ve sloupci **stav symbolu** načtené symboly. Klikněte pravým tlačítkem na modul, pro který chcete načíst symboly, a vyberte **načíst symboly**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Krok do vlastností a operátorů ve spravovaném kódu
 Ladicí program ve výchozím nastavení přesměruje vlastnosti a operátory ve spravovaném kódu. Ve většině případů to poskytuje lepší možnosti ladění. Chcete-li povolit krokování do vlastností nebo operátorů, vyberte možnost **ladění**  > **Možnosti**. Na stránce **ladění**  > **Obecné** zrušte zaškrtnutí políčka **Krokovat přes vlastnosti a operátory (pouze spravované)** .

## <a name="see-also"></a>Viz také:
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
