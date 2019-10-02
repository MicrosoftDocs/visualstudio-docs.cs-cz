---
title: Používání zarážek v ladicím programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 10/15/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b40c18c4b85b39e118ac59b97649253d27324854
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814362"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Používání zarážek v ladicím programu sady Visual Studio
Zarážky jsou jedním z nejdůležitějších technik ladění mezi nástroji pro vývojáře sady nástrojů. Můžete nastavit zarážky, bez ohledu na to chcete provést pozastavení spuštění ladicího programu. Můžete například zobrazit stav proměnných kódu se také podívat na zásobník volání na určité zarážce. Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md) před provedením tohoto článku.

## <a name="BKMK_Overview"></a> Nastavení zarážek ve zdrojovém kódu
 Můžete nastavit zarážku na kterýkoli řádek spustitelného kódu. Například v následujícím kódu C#, můžete nastavit zarážku na deklaraci proměnné `for` smyčku, nebo žádný kód uvnitř `for` smyčky. Deklarace oboru názvů nebo třídy, nebo v podpisu metody nelze nastavit zarážku.

 Pokud chcete nastavit zarážku ve zdrojovém kódu, klikněte v levém okraji vedle řádku kódu. Můžete také vybrat řádku a stisknutím klávesy **F9**vyberte **ladění** > **Přepnout zarážku**, nebo klikněte pravým tlačítkem a vyberte **zarážku**  >  **Vložit zarážku**. Zarážka se zobrazí jako červená tečka na levém okraji.

V C# automaticky zvýrazněný kód, zarážky a aktuální provádění řádky. Pro kód C++ můžete zapnout zvýraznění zarážky a aktuální řádky tak, že vyberete **nástroje** (nebo **ladění**) > **možnosti**  >   **Ladění** >  **zvýraznit celý řádek zdrojového kódu pro zarážky a aktuální příkaz (pouze C++)** .

 ![Nastavit zarážku](../debugger/media/basicbreakpoint.png "základní zarážku")

 Při ladění, spouštění pozastavení na zarážce, před provedením kódu na daném řádku. Žlutá šipka se zobrazí symbol zarážky.

 Na zarážce v následujícím příkladu, hodnota `testInt` je stále 1.

 ![Zastavit provádění zarážku](../debugger/media/breakpointexecution.png "provádění zarážku")

 Pokud ladicí program se zastaví na zarážce, můžete si prohlédnout aktuální stav aplikace, včetně hodnot proměnných a zásobníku volání. Další informace o zásobníku volání naleznete v tématu [How do: Použijte okno zásobníku volání @ no__t-0.

- Zarážka je přepínací tlačítko. Můžete na ni klikněte, stiskněte klávesu **F9**, nebo použijte **ladění** > **Přepnout zarážku** odstranění nebo vložením.

- Zakázat zarážku, aniž by byl, najeďte myší nebo pravým tlačítkem myši a vyberte **zakázat zarážku**. Zakázané zarážky se zobrazí jako prázdný tečky na levém okraji nebo **zarážky** okna. Opětovné povolení zarážku, najeďte myší nebo pravým tlačítkem myši a vyberte **povolit zarážku**.

- Nastavení podmínek a akcí, přidat a upravit štítky nebo exportujte zarážky tak, že pravým tlačítkem myši a vyberete příslušný příkaz, nebo je ukazatel myši a vyberete **nastavení** ikonu.

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Nastavit body přerušení z ladicího programu systému windows

Můžete také nastavit zarážky z **zásobník volání** a **zpětný překlad** ladicího programu systému windows.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Nastavení zarážky v okně zásobník volání

 Přerušení na pokynu nebo řádku, který funkce volání vrací, můžete nastavit zarážku **zásobník volání** okna.

**Chcete-li nastavit zarážku v okně zásobník volání:**

1. Chcete-li otevřít **zásobník volání** okna, je nutné pozastavit během ladění. Vyberte **ladění** > **Windows** > **zásobník volání**, nebo stiskněte klávesu **Ctrl** + **Alt**+**C**.

2. V **zásobník volání** okna, klikněte pravým tlačítkem na volající funkci a vyberte **zarážku** > **vložit zarážku**, nebo stiskněte klávesu **F9**.

   Vedle názvu volání funkce v zásobníku volání na levém okraji se zobrazí symbol zarážky.

Zarážky zásobníku volání se zobrazí v **zarážky** okno jako adresy s oblastí paměti, která odpovídá další spustitelné instrukci ve funkci.

Ladicí program přeruší podle instrukce.

Další informace o zásobníku volání naleznete v tématu [How do: Použijte okno zásobníku volání @ no__t-0.

Vizuálně sledovat zarážky během provádění kódu, naleznete v tématu [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně zpětný překlad

1. Chcete-li otevřít **zpětný překlad** okna, je nutné pozastavit během ladění. Vyberte **ladění** > **Windows** > **zpětný překlad**, nebo stiskněte klávesu **Alt** + **8**.

2. V **zpětný překlad** okna, klikněte na levý okraj podle pokynů, které chcete provést přerušení. Můžete také vybrat ji a stiskněte klávesu **F9**, nebo klikněte pravým tlačítkem a vyberte **zarážku** > **vložit zarážku**.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Nastavení zarážek – funkce

  Můžete přerušit běh při volání funkce.

**Chcete-li nastavit zarážku funkce:**

1. Vyberte **ladění** > **Nová zarážka** > **zarážky funkce**, nebo stiskněte klávesu **Alt** + **F9** > **Ctrl**+**B**.

   Můžete také vybrat **nový** > **zarážky funkce** v **zarážky** okna.

1. V **Nová zarážka funkce** dialogové okno, zadejte název do funkce **název funkce** pole.

   Chcete-li zúžit specifikaci funkce:

   - Pomocí funkce plně kvalifikovaného názvu.

     Příklad:  `Namespace1.ClassX.MethodA()`

   - Přidejte typy parametrů přetížené funkce.

     Příklad:  `MethodA(int, string)`

   - Používá "!" symbolů k určení modulu.

     Příklad: `App1.dll!MethodA`

   - Použijte operátor kontextu v nativním kódu C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Příklad: `{MethodA, , App1.dll}+2`

1. V **jazyk** rozevíracím seznamu vyberte jazyk funkce.

1. Vyberte **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Nastavení zarážky funkce pomocí adresy paměti (pouze nativní C++)
 Chcete-li nastavit zarážku funkce v metodě volané konkrétní instanci třídy můžete adresu objektu.  Mějme například adresovatelný objekt typu `my_class`, můžete nastavit zarážku funkce na `my_method` metodu, která instance volání.

1. Nastavte zarážku někde, jakmile je vytvořena instance třídy.

2. Najít adresu instance (například `0xcccccccc`).

3. Vyberte **ladění** > **Nová zarážka** > **zarážky funkce**, nebo stiskněte klávesu **Alt** + **F9** > **Ctrl**+**B**.

4. Přidejte následující text do **název funkce** a vyberte **C++** jazyka.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Nastavení zarážek s daty (.NET Core 3,0 nebo vyšší)

Datové zarážky přeruší provádění při změně vlastnosti určitého objektu.

**Nastavení datové zarážky**

1. V projektu .NET Core spusťte ladění a počkejte na dosažení zarážky.

2. V okně **Automatické**hodnoty, **kukátko**nebo **místních** hodnot klikněte pravým tlačítkem na vlastnost a v místní nabídce vyberte možnost **přerušit při změně hodnoty** .

    (../debugger/media/managed-data-breakpoint.png "Zarážka spravované datové") ![zarážky spravovaného data]

Datové zarážky v .NET Core nebudou fungovat pro:

- Vlastnosti, které se nerozšiřují v popiscích, místních hodnotách, Autoch nebo okno Kukátko
- Statické proměnné
- Třídy s atributem používání DebuggerTypeProxy
- Pole uvnitř struktur

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Nastavení datové zarážky (pouze nativní C++)

 Body zarážek přeruší provádění když hodnota uložená v paměti zadaná adresa změní. Pokud hodnota je číst, ale nebyl změněn, spuštění nebude přerušeno.

**Chcete-li nastavit zarážku dat:**

1. V projektu jazyka C++ spustit ladění a počkejte, dokud není dosaženo zarážky. Na **ladění** nabídce zvolte **Nová zarážka** > **datová zarážka**

    Můžete také vybrat možnost **Nová** **zarážka dat**  >  v okně **zarážky** nebo kliknout pravým tlačítkem myši na položku v okně **Automatické**hodnoty, **kukátko**nebo **místních** hodnot a vybrat možnost **přerušit při změně hodnoty** v místní nabídce.

2. V **adresu** zadejte adresu paměti nebo výraz, který vyhodnocuje adresu paměti. Zadejte například `&avar` pro přerušení, když obsah proměnné `avar` změny.

3. V **počet bajtů** rozevíracím seznamu vyberte počet bajtů, které chcete ladicí program sledoval. Pokud vyberete třeba **4**, ladicí program bude sledovat čtyři bajty počínaje `&avar` a přerušit, pokud některý z těchto bajtů změní hodnotu.

Zarážky data nefungují za těchto podmínek:
- Proces, který se neladí se zapíše do umístění v paměti.
- Umístění v paměti jsou sdílena mezi dvěma nebo více procesy.
- Umístění v paměti je aktualizováno v rámci jádra. Například, pokud je paměť předána 32bitové Windows `ReadFile` funkce, paměť se budou aktualizovat z režimu jádra, aby ladicí program nebudou porušovat na aktualizaci.
- Kde výraz kukátka je větší než 4 bajty na 32ovém hardwaru a 8 bajtů na 64 bitového hardwaru. Toto je omezení architektury x86.

> [!NOTE]
> - Datové zarážky, závisí na konkrétní paměťové adresy. Adresa proměnné změny z jedné relace ladění na další, abyste na konci každé relace ladění jsou automaticky zakázány datové zarážky.
>
> - Pokud nastavíte zarážku dat na lokální proměnné, zarážka zůstane povolena po skončení funkce, ale adresa paměti není nadále vhodné, takže nepředvídatelné chování zarážky. Pokud nastavíte zarážku dat na lokální proměnné, musíte odstranit nebo zakázat zarážku před ukončením funkce.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Spravovat zarážky v okně zarážek

 Můžete použít **zarážky** okno zobrazit a spravovat všechny zarážky ve vašem řešení. Toto centralizované umístění je zvláště užitečné v na velkých projektech nebo pro komplexní scénáře ladění, kde jsou zarážky nezbytné.

V **zarážky** okna, můžete hledat, řadit, filtrovat, povolit nebo zakázat nebo odstranit zarážky. Můžete také nastavit podmínky a akce nebo přidat nové funkce nebo datová zarážka.

Otevřete **zarážky** okně **ladění** > **Windows** > **zarážky**, nebo stiskněte klávesu  **ALT**+**F9** nebo **Ctrl**+**Alt**+**B**.

![Okno zarážek](../debugger/media/breakpointswindow.png "zarážky – okno")

Chcete-li vybrat sloupce, které chcete zobrazit v **zarážky** okně **zobrazit sloupce**. Vyberte záhlaví sloupce řazení podle sloupce v seznamu zarážek.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Štítky zarážek
Popisky můžete použít k řazení a filtrováni seznamu zarážek v **zarážky** okna.

1. Chcete-li přidat popisek k zarážce, klikněte pravým tlačítkem na zarážku ve zdrojovém kódu nebo **zarážky** okna a pak vyberte **upravit štítky**. Přidat nový popisek nebo vyberte existující a pak vyberte **OK**.
2. Seřadit seznam zarážku **zarážky** okna tak, že vyberete **popisky**, **podmínky**, nebo jiné záhlaví sloupců. Můžete vybrat sloupce, které chcete zobrazit výběrem **zobrazit sloupce** na panelu nástrojů.

### <a name="export-and-import-breakpoints"></a>Zarážky exportu a importu
 Pokud chcete uložit nebo sdílet stav a umístění vašich zarážek, můžete exportovat nebo importovat.

- Export jediné zarážku do souboru XML, klikněte pravým tlačítkem na zarážku ve zdrojovém kódu nebo **zarážky** okna a vyberte **exportovat** nebo **exportovat vybrané**. Vyberte umístění exportu a pak vyberte **Uložit**. Výchozí umístění je složky řešení.
- Exportovat několik zarážky v **zarážky** okna, zaškrtněte políčka vedle zarážek nebo zadejte kritéria vyhledávání v **hledání** pole. Vyberte **exportuje všechny zarážky vyhovující kritériím hledání** ikony a soubor uložte.
- Pokud chcete exportovat všechny zarážky, zrušte výběr všech polí a nechat **hledání** prázdné pole. Vyberte **exportuje všechny zarážky vyhovující kritériím hledání** ikony a soubor uložte.
- Importovat zarážky, v **zarážky** okna, vyberte **importuje zarážky ze souboru** ikonu, přejděte do umístění souboru XML a vyberte **otevřít**.

## <a name="breakpoint-conditions"></a>Podmínky zarážky
 Můžete řídit, kdy a kde se zarážky spouštějí nastavením podmínky. Podmínka může být libovolný platný výraz, který ladicí program rozpozná. Další informace o zobrazení platných výrazů naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).

**Chcete-li nastavit podmínku zarážky:**

1. Klikněte pravým tlačítkem na symbol zarážky a vyberte **podmínky**. Nebo podržte ukazatel myši nad symbol zarážky, vyberte **nastavení** ikonu a pak vyberte **podmínky** v **nastavení zarážek** okna.

   Můžete také nastavit podmínky **zarážky** okna tak, že kliknete pravým tlačítkem na zarážku a vyberete **nastavení**a pak vyberete **podmínky**.

   ![Nastavení zarážek](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. V rozevíracím seznamu vyberte **podmíněný výraz**, **počet volání**, nebo **filtr**a odpovídajícím způsobem nastavit hodnotu.

3. Vyberte **zavřete** nebo stiskněte klávesu **Ctrl**+**Enter** zavřete **nastavení zarážek** okna. Nebo z **zarážky** okně **OK** zavřete dialogové okno.

Zarážek s stanovené podmínky, zobrazí se **+** symbol ve zdrojovém kódu a **zarážky** systému windows.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Podmíněný výraz

Když vyberete **podmíněný výraz**, můžete si vybrat ze dvou podmínek: **Je true** nebo **při změně**. Zvolte **platí** přerušit, když je splněna výrazu, nebo **při změně** k rozdělení se při změně hodnoty výrazu.

 V následujícím příkladu, zarážka se projeví pouze tehdy, když hodnota `testInt` je **4**:

 ![Při splnění podmínky zarážky](../debugger/media/breakpointconditionistrue.png "zarážka je nastavena na možnost PRAVDA")

 V následujícím příkladu, zarážka se projeví pouze tehdy, když hodnota `testInt` změny:

 ![Zarážky při změně](../debugger/media/breakpointwhenchanged.png "zarážky při změně")

 Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se zpráva s upozorněním. Pokud zadáte podmínku zarážky s platnou syntaxi ale s neplatnou sémantikou, zobrazí se upozornění při prvním dosažení zarážky. V obou případech ladicí program přeruší při volání zarážky neplatné. Zarážka je vynechána pouze v případě, že podmínka platí a je vyhodnocena jako `false`.

 >[!NOTE]
 >Chování **při změně** pole je pro různé programovací jazyky.
 >- Pro nativní kód ladicí program nezahrne hodnocení první podmínku, která má být změněna, takže nebude zarážce při prvním hodnocení.
 >- Pro spravovaný kód, ladicí program narazí na zarážku při prvním hodnocení po **při změně** zaškrtnuto.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Pomocí ID objektů v podmíněných výrazech (C# a F# jenom)
 Existují situace, kdy budete chtít sledovat chování s určitým objektem. Můžete třeba chtít zjistit, proč objekt byl vložen do kolekce více než jednou. V C# a F#, můžete vytvořit objekt ID pro určité instance [referenční typy](/dotnet/csharp/language-reference/keywords/reference-types)a jejich použití v podmínky zarážky. ID objektu je generována modulem common language runtime (CLR) ladění služeb a přidružená k objektu.

**Chcete-li vytvořit ID objektu:**

1. Nastavte zarážku v kódu některém místě po vytvoření objektu.

2. Spustit ladění a při spuštění, pozastavení na zarážce, vyberte **ladění** > **Windows** > **lokální** nebo **Alt** + **4** otevřít **lokální** okna.

   V okně **místní** hodnoty Najděte konkrétní instanci objektu, klikněte na ni pravým tlačítkem myši a vyberte **vytvořit ID objektu**.

   Měli byste vidět **$** plus číslo v **místní hodnoty** okna. To je ID objektu.

3. Přidat novou zarážku v okamžiku, kdy chcete prozkoumat; například když je přidán do kolekce. Klikněte pravým tlačítkem myši zarážka a vyberte **podmínky**.

4. Použití atributu ID objektu **podmíněný výraz** pole. Například pokud proměnnou `item` je objekt, který má být přidána do kolekce, vyberte **platí** a typ **položky == $\<n >** , kde \<n > je číslo ID objektu .

   Spuštění se přeruší v okamžiku, když je přidán do kolekce.

   Pokud chcete odstranit ID objektu, klikněte pravým tlačítkem na proměnnou v **lokální** okna a vyberte **odstranit ID objektu**.

>[!NOTE]
>ID objektů vytvořit slabé odkazy a nezabrání objektu je uvolněna z paměti. Jsou platné pouze pro aktuální relaci ladění.

### <a name="hit-count"></a>Počet přístupů
 Pokud máte podezření, že smyčka v kódu se začíná chovat neplatně po určitém počtu iterací, můžete nastavit zarážku pro zastavení provádění po tomto počtu přístupů, namísto nutnosti opakovaně stiskněte **F5** k dosažení této iterace.

 V části **podmínky** v **nastavení zarážek** okně **počet volání**a pak zadejte počet iterací. V následujícím příkladu je nastavena zarážka narazí při každé iteraci:

 ![Počet průchodů zarážky](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="filter"></a>Filtr
Můžete omezit zarážku, chcete-li vyvolat pouze na zadané zařízení nebo v konkrétních procesů a vláken.

V části **podmínky** v **nastavení zarážek** okně **filtr**a pak zadejte jednu nebo více z těchto výrazů:

- MachineName = "name"
- ProcessId = hodnota
- ProcessName = "name"
- ThreadId = hodnota
- ThreadName = "name"

Řetězcové hodnoty uzavřete do dvojitých uvozovek. Můžete kombinovat klauzule pomocí `&` (a), `||` (nebo), `!` (NOT) a závorkami.

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akce zarážek a zarážky s trasováním
 A *zarážka s trasováním* je zarážka, která vytiskne zprávu do **výstup** okna. Trasování může sloužit jako dočasný příkaz trasování v programovacím jazyce.

**Chcete-li nastavit zarážku s trasováním:**

1. Klikněte pravým tlačítkem na zarážku a vyberte **akce**. Nebo v **nastavení zarážek** období, najeďte myší na zarážku, vyberte **nastavení** ikonu a pak vyberte **akce**.

1. Zadejte zprávu v **zapsat zprávu do okna výstup** pole. Zpráva může zahrnovat obecné textové řetězce, hodnoty proměnných a výrazů uzavřený do složených závorek a specifikátory formátu ([jazyka C#](../debugger/format-specifiers-in-csharp.md) a [C++](../debugger/format-specifiers-in-cpp.md)) pro hodnoty.

   Můžete také použít následující speciální klíčová slova ve zprávě:

   - **$ADDRESS** -aktuální instrukce
   - **$CALLER** -název funkce volání
   - **$CALLSTACK** – zásobník volání
   - **$FUNCTION** -název aktuální funkce
   - **$PID** – id procesu
   - **$PNAME** -název procesu
   - **$TID** – id vlákna
   - **$TNAME** -název vlákna
   - **$TICK** – počet směrování (z Windows `GetTickCount`)

1. Vytisknout zprávu, která se **výstup** okno bez přerušení, vyberte **pokračovat v provádění** zaškrtávací políčko. Chcete-li vytisknout zprávu a pozastavení provádění na zarážku s trasováním, zrušte zaškrtnutí políčka.

Zarážky s trasováním zobrazují jako červené kosočtverce na levém okraji zdrojového kódu a **zarážky** systému windows.

## <a name="see-also"></a>Viz také:

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Psali lepší C# kódu pomocí sady Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Řešení potíží s body přerušení v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md)
