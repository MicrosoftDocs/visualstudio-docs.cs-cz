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
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409316"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Procházení kódu s ladicím programu sady Visual Studio

Ladicí program sady Visual Studio můžete procházet kód pro kontrolu stavu aplikace a zobrazit jeho spuštění toku. Klávesové zkratky, příkazy ladění, zarážky a další funkce můžete rychle dostali k kód, který chcete prověřit. Seznámení se s navigačními příkazy ladicího programu a zkratky umožňuje rychlejší a snazší najít a řešení potíží v aplikacích.  Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="get-into-break-mode"></a>Přejít do režimu přerušení

V *režimu pozastavení*je spuštění aplikace pozastaveno, zatímco funkce, proměnné a objekty zůstávají v paměti. Jakmile je ladicí program v režimu pozastavení, můžete procházet kód. Nejběžnější způsoby, jak rychle získat režim přerušení, je:

- Zahajte krokování kódu stisknutím klávesy **F10** nebo **F11**. To vám umožní rychle najít vstupní bod vaší aplikace, a pak můžete pokračovat stisknutím příkazů Step pro procházení kódu.

- [Spustit do konkrétního umístění nebo funkce](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), například [nastavením zarážky](using-breakpoints.md) a spuštěním vaší aplikace.

   Například z editoru kódu v aplikaci Visual Studio můžete pomocí příkazu **Spustit ke kurzoru** spustit aplikaci, připojit ladicí program a získat režim přerušení a potom klávesu **F11** přejít ke kódu.

   ![Spustit ke kurzoru a krokovat kód](../debugger/media/navigate-code-code-stepping.gif "Spustit ke kurzoru a krokovat kód")

Jednou v režimu pozastavení můžete použít celou řadu příkazů k procházení kódu. V režimu pozastavení můžete zkontrolovat hodnoty proměnných a vyhledat porušení nebo chyby. U některých typů projektů lze také provést úpravy aplikace v režimu přerušení.

Většina oken ladicího programu, jako jsou **moduly** a **sledovací** okna, jsou k dispozici pouze tehdy, když je ladicí program připojen k vaší aplikaci. Některé funkce ladicího programu, jako je například zobrazení hodnot proměnných v okně **místních** hodnot nebo vyhodnocování výrazů v okně **kukátka** , jsou k dispozici pouze v případě, že ladicí program je pozastaven (tj. v režimu pozastavení).

> [!NOTE]
> Pokud přerušíte kód, který nemá načítat zdrojové soubory nebo soubory symbolů (*PDB*), ladicí program zobrazí stránku **nenalezené zdrojové soubory** nebo **symboly nebyly nalezeny** , které vám pomohou najít a načíst soubory. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nemůžete načíst symbol nebo zdrojové soubory, můžete přesto ladit pokyny sestavení v okně zpětného **překladu** .

## <a name="step-through-code"></a>Krokovat kód

Krok příkazy ladicího programu můžete zkontrolovat stav vaší aplikace nebo si přečtěte Další informace o jeho spuštění toku.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Krokovat s kódem řádek po řádku

Chcete-li zastavit u každého příkazu během ladění, použijte **Krok** **ladění** > do nebo stiskněte klávesu **F11**.

Ladicí program vás provede příkazy kódu, nikoli fyzické řádky. Například klauzuli `if` lze zapsat na jeden řádek:

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

U vnořeného volání funkce **Krok do** nejhlouběji vnořené funkce. Například pokud použijete **Krok do** pro volání, jako je `Func1(Func2())`, ladicí program kroky do funkce `Func2`.

>[!TIP]
>Při provádění jednotlivých řádků kódu můžete umístit ukazatele myši nad proměnné, abyste viděli jejich hodnoty, nebo použít [místní](autos-and-locals-windows.md) okna a [kukátka](watch-and-quickwatch-windows.md) ke sledování změn hodnot. Můžete také vizuálně sledovat [zásobník volání](how-to-use-the-call-stack-window.md) při krokování do funkcí. (Pouze pro Visual Studio Enterprise, viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="BKMK_Step_over_Step_out"></a>Krokovat kód a přeskočit některé funkce

Funkce nemusí záleží při ladění nebo ho znáte funguje, jako jsou dobře otestovaný knihovny kódu. Pomocí následujících příkazů můžete přeskočit kód při krokování kódu. Funkce spustit, ale je přeskočen ladicí program.

|Příkaz klávesnice|Příkaz nabídky ladění|Popis|
|----------------------|------------------|-----------------|
|**F10**|**Krokovat**|Pokud aktuální řádek obsahuje volání funkce, **Krok over** spustí kód a poté pozastaví provádění na prvním řádku kódu po návratu volané funkce.|
|**Shift**+**F11**|**Krok ven**|**Krok ven** pokračuje v běhu kódu a pozastaví provádění, když se vrátí aktuální funkce. Ladicí program přeskočí prostřednictvím aktuální funkce.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Spustit do konkrétního umístění nebo funkce

Můžete chtít spustit přímo do určitého umístění nebo funkce, když víte přesně jaký kód, který chcete zkontrolovat nebo víte, kde chcete spustit ladění.

### <a name="run-to-a-breakpoint-in-code"></a>Spusťte zarážku v kódu

Chcete-li nastavení jednoduché zarážky v kódu, klikněte na levém okraji vedle řádku kódu, ve které chcete pozastavit provádění. Můžete také vybrat řádek a stisknout klávesu **F9**, vybrat položku **ladění** > **Přepnout zarážku**, nebo kliknout pravým tlačítkem a vybrat **zarážku** > **Vložit zarážku**. Zarážka se zobrazí jako červená tečka na levém okraji vedle řádku kódu. Ladicí program přeruší provádění, stačí před provedením řádku.

![Nastavit zarážku](../debugger/media/dbg_basics_setbreakpoint.png "Nastavení zarážky")

Zarážky v sadě Visual Studio poskytují další funkce, jako je například podmíněné zarážky a sledované body. Podrobnosti najdete v tématu [použití zarážek](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Spusťte zarážku funkce

Poznáte, ladicí program ke spuštění, dokud nedosáhne určenou funkci. Můžete zadat funkce podle názvu nebo je možné ji zvolit ze zásobníku volání.

**Určení zarážky funkce podle názvu**

1. Vyberte možnost **ladění** > **novou** zarážku > **zarážku funkce** .

1. V dialogovém okně **Nová zarážka funkce** zadejte název funkce a vyberte její jazyk.

   ![Nové zarážky funkce – dialogové okno](../debugger/media/dbg_execution_newbreakpoint.png "Nová zarážka funkce")

1. Vyberte **OK**.

Pokud je funkce přetížena nebo ve více než jednom oboru názvů, můžete zvolit, který chcete v okně **zarážky** .

![Přetížené zarážky funkcí](../debugger/media/dbg_execution_overloadedbreakpoints.png "Přetížené zarážky funkcí")

**Výběr zarážky funkce ze zásobníku volání**

1. Při ladění otevřete okno **zásobník volání** výběrem možnosti **ladění** > **Windows** > **zásobník volání**.

1. V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci a vyberte možnost **Spustit ke kurzoru**nebo stiskněte klávesovou **zkratku CTRL**+**F10**.

Vizuální trasování zásobníku volání naleznete v tématu [metody mapy v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Spuštění do umístění kurzoru

Chcete-li spustit do umístění kurzoru, v okně zdrojový kód nebo **zásobník volání** vyberte řádek, u kterého chcete provést přerušení, klikněte pravým tlačítkem myši a vyberte možnost **Spustit ke kurzoru**nebo stiskněte klávesovou **zkratku CTRL**+**F10**. Výběr možnosti **Spustit na kurzor** je jako nastavení dočasné zarážky.

### <a name="run-to-click"></a>Běžet do kliknutí

Při pozastavení v ladicím programu můžete umístit ukazatel myši na příkaz ve zdrojovém kódu nebo v okně zpětného **překladu** a vybrat ikonu **spustit do sem** zelená ikona šipky. Když **kliknete na tlačítko Spustit,** eliminuje nutnost nastavit dočasnou zarážku.

![Spustit kliknutím](../debugger/media/dbg-run-to-click.png "Běžet do kliknutí")

> [!NOTE]
> **Možnost spustit do** je k dispozici od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Ručně proniknout do kódu

Chcete-li přerušit následující dostupný řádek kódu ve spuštěné aplikaci, vyberte možnost **ladění** > **rozdělit vše**nebo stiskněte klávesu **CTRL**+**ALT**+**Break**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Přesunutím ukazatele myši změníte tok provádění.

I když je ladicí program pozastaven, žlutá šipka na okraji okna zdrojového kódu nebo **zpětný překlad** označuje umístění dalšího příkazu, který má být proveden. Můžete změnit dalšího příkazu ke spuštění přesunutím této šipky. Můžete přeskočit část kódu nebo vrátit na předchozí řádek. Ukazatele je užitečné v situacích, jako je například vynechání části kódu, který obsahuje známou chybu.

 ![Přesunout ukazatel](../debugger/media/dbg_basics_example3.gif "Přesunout ukazatel")

Chcete-li změnit dalšího příkazu ke spuštění, musí být ladicí program v režimu pozastavení. V okně zdrojový kód nebo **zpětný překlad** přetáhněte žlutou šipku na jiný řádek, nebo klikněte pravým tlačítkem na řádek, který chcete spustit, a vyberte **nastavit další příkaz**.

Čítač programu přejde přímo na nové umístění a pokyny mezi staré a nové spuštění nebudou provedeny body. Nicméně pokud přesunete bod spuštění zpět, intervenující pokyny se vrátit zpět.

>[!CAUTION]
>- Přesunutí dalšího příkazu do jiné funkce nebo rozsahu obvykle za následek poškození zásobníku volání, což způsobí runtime chybu nebo výjimku. Při přesunutí dalšího příkazu do jiného oboru, ladicí program otevře dialogové okno s upozorněním a dává vám možnost zrušit operaci.
>- V jazyce Visual Basic nemůžete přesunout do jiného oboru nebo funkce další příkaz.
>- V nativním kódu C++ Pokud máte kontroly za běhu povoleno, nastavení dalšího příkazu může způsobit výjimku, která je vyvolána, když spuštění dosáhne konce metody.
>- Pokud je povolená možnost upravit a pokračovat, **nastavení dalšího příkazu** se nepovede, pokud jste provedli úpravy, které upravit a pokračovat nemůže okamžitě přemapovat. Tato situace může nastat, například, pokud se po úpravě kódu v bloku catch. Pokud k tomu dojde, chybová zpráva zjistíte, že operace není podporována.
>- Ve spravovaném kódu nelze přesunout další příkaz, pokud:
>   - Další příkaz je v jiné metody než aktuální příkaz.
>   - Ladění bylo zahájeno Just-In-Time ladění.
>   - Probíhá uvolnění zásobníku volání.
>   - Byla vyvolána výjimka System.StackOverflowException or System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Ladit neuživatelský kód

Ve výchozím nastavení se ladicí program pokusí ladit pouze kód vaší aplikace povolením nastavení s názvem *pouze můj kód*. Další podrobnosti o tom, jak tato funkce funguje pro různé typy projektů a jazyky a jak je můžete přizpůsobit, najdete v tématu [pouze můj kód](../debugger/just-my-code.md).

Podívat se na kód rozhraní framework, kód knihovny třetích stran nebo systémových volání při ladění, můžete zakázat pouze můj kód. V **nabídce nástroje** (nebo **ladění**) > **Možnosti** > **ladění**zrušte zaškrtnutí políčka **Povolit pouze můj kód** . Pokud funkce pouze můj kód je zakázán, neuživatelském kódu se zobrazí v oknech ladicího programu a ladicího programu můžete krokovat s vnořením neuživatelský kód.

> [!NOTE]
> Funkce pouze můj kód není podporována pro projekty zařízení.

### <a name="debug-system-code"></a>Ladění kódu systému

Pokud máte načíst symboly ladění pro kód systému Microsoft a zakázané funkce pouze můj kód, můžete krokovat s vnořením do volání systému stejně jako u ostatních volání.

Chcete-li načíst symboly společnosti Microsoft, přečtěte si téma [Konfigurace umístění symbolů a možnosti načítání](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Načtení symbolů pro konkrétní systémovou komponentu:**

1. Když ladíte, otevřete okno **moduly** výběrem možnosti **ladit** > **moduly** > **Windows** nebo stisknutím klávesy **CTRL**+**ALT**+**U**.

1. V okně **moduly** můžete určit, které moduly mají ve sloupci **stav symbolu** načtené symboly. Klikněte pravým tlačítkem na modul, pro který chcete načíst symboly, a vyberte **načíst symboly**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Krok do vlastností a operátorů ve spravovaném kódu
 Ladicí program přes vlastnosti a operátory ve spravovaném kódu ve výchozím nastavení. Ve většině případů to poskytuje lepší možnosti ladění. Chcete-li povolit krokování do vlastností nebo operátorů, vyberte možnost **ladění** > **Možnosti**. Na stránce **ladění** > **Obecné** zrušte zaškrtnutí políčka **Krokovat přes vlastnosti a operátory (pouze spravované)** .

## <a name="see-also"></a>Viz také
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
