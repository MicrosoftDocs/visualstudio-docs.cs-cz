---
title: Používání zarážek v ladicím programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/28/2019
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
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409239"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Používání zarážek v ladicím programu sady Visual Studio

Zarážky jsou jedním z nejdůležitějších technik ladění mezi nástroji pro vývojáře sady nástrojů. Můžete nastavit zarážky, bez ohledu na to chcete provést pozastavení spuštění ladicího programu. Můžete například zobrazit stav proměnných kódu se také podívat na zásobník volání na určité zarážce.  Pokud se snažíte vyřešit upozornění nebo problém při použití zarážek, přečtěte si téma [řešení potíží se zarážkami v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Pokud znáte úlohu nebo problém, který se snažíte vyřešit, ale potřebujete znát, jaký typ zarážky chcete použít, přečtěte si téma [vyhledání úlohy ladění](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="BKMK_Overview"></a>Nastavení zarážek ve zdrojovém kódu

Můžete nastavit zarážku na kterýkoli řádek spustitelného kódu. Například v následujícím C# kódu můžete nastavit zarážku na deklaraci proměnné, `for` smyčku nebo jakýkoli kód uvnitř smyčky `for`. Deklarace oboru názvů nebo třídy, nebo v podpisu metody nelze nastavit zarážku.

Pokud chcete nastavit zarážku ve zdrojovém kódu, klikněte v levém okraji vedle řádku kódu. Můžete také vybrat řádek a stisknout klávesu **F9**, vybrat položku **ladění** > **Přepnout zarážku**, nebo kliknout pravým tlačítkem a vybrat **zarážku** > **Vložit zarážku**. Zarážka se zobrazí jako červená tečka na levém okraji.

Pro většinu jazyků, C#včetně, zarážky a aktuální řádky spuštění jsou automaticky zvýrazněny. Pro C++ kód můžete zapnout zvýraznění zarážky a aktuální řádky výběrem **nástrojů** (nebo **ladění**) > **možností** > **ladění** >  **zvýraznit celý zdrojový řádek pro zarážky a aktuální příkaz (C++ pouze)** .

![Nastavit zarážku](../debugger/media/basicbreakpoint.png "Základní zarážka")

Při ladění, spouštění pozastavení na zarážce, před provedením kódu na daném řádku. Žlutá šipka se zobrazí symbol zarážky.

Na zarážce v následujícím příkladu je hodnota `testInt` stále 1. Proto se hodnota od inicializace proměnné nezměnila (nastavená na hodnotu 1), protože příkaz žlutý nebyl dosud proveden.

![Spuštění zarážky bylo zastaveno.](../debugger/media/breakpointexecution.png "Spuštění zarážky")

Když se ladicí program zastaví na zarážce, můžete se podívat na aktuální stav aplikace, včetně [hodnot proměnných](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) a [zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

Zde je několik obecných pokynů pro práci se zarážkami.

- Zarážka je přepínací tlačítko. Můžete na ni kliknout, stisknout klávesu **F9**nebo použít **ladění** > **přepínací zarážku** , aby ji bylo možné odstranit nebo znovu vložit.

- Chcete-li zakázat zarážku bez jejich odstranění, najeďte myší na ni nebo klikněte na ni pravým tlačítkem a vyberte možnost **Zakázat zarážku**. Zakázané zarážky se zobrazují jako prázdné tečky v levém okraji nebo v okně **zarážky** . Pokud chcete zarážku znovu povolit, najeďte myší na ni nebo klikněte na ni pravým tlačítkem a vyberte **Povolit zarážku**.

- Nastavte podmínky a akce, přidejte a upravte popisky nebo exportujte zarážku tak, že na ni kliknete pravým tlačítkem myši a vyberete příslušný příkaz nebo když na něj najedete a vyberete ikonu **Nastavení** .

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akce zarážek a trasováním

*Zarážka s trasováním* je zarážka, která vytiskne zprávu do okna **výstup** . Zarážka s trasováním může fungovat jako dočasný příkaz trace v programovacím jazyce a neumožňuje pozastaví provádění kódu. Zarážka s trasováním vytvoříte tak, že v okně **Nastavení zarážky** nastavíte zvláštní akci. Podrobné pokyny najdete v tématu [použití trasováním v ladicím programu sady Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Podmínky zarážky

Můžete řídit, kdy a kde se zarážky spouštějí nastavením podmínky. Podmínka může být libovolný platný výraz, který ladicí program rozpozná. Další informace o platných výrazech naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).

**Nastavení podmínky zarážky:**

1. Klikněte pravým tlačítkem na symbol zarážky a vyberte **podmínky**. Nebo najeďte myší na symbol zarážky, vyberte ikonu **Nastavení** a pak v okně **Nastavení zarážky** vyberte **podmínky** .

   V okně **zarážky** můžete také nastavit podmínky tak, že kliknete pravým tlačítkem myši na zarážku a vyberete **Nastavení**a pak vyberete **podmínky**.

   ![Nastavení zarážky](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. V rozevíracím seznamu vyberte **podmíněný výraz**, **Počet volání**nebo **Filtr**a nastavte hodnotu odpovídajícím způsobem.

3. Kliknutím na tlačítko **Zavřít** nebo stisknutím klávesy **CTRL**+**ENTER** zavřete okno **Nastavení zarážky** . Nebo v okně **zarážky** kliknutím na **tlačítko OK** zavřete dialogové okno.

Zarážky s nastavenými podmínkami se zobrazí se symbolem **+** v oknech zdrojový kód a **zarážky** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Vytvoření podmíněného výrazu

Když vyberete **podmíněný výraz**, můžete zvolit mezi dvěma podmínkami: **je true** nebo **při změně**. Vyberte **hodnotu true** , pokud chcete přerušit, když je výraz splněn, nebo **když se změní** na přerušit, když se změní hodnota výrazu.

V následujícím příkladu je zarážka volána pouze v případě, že hodnota `testInt` je **4**:

![Podmínka zarážky je pravdivá.](../debugger/media/breakpointconditionistrue.png "Zarážka je pravdivá.")

V následujícím příkladu je zarážka volána pouze v případě, že se změní hodnota `testInt`:

![Zarážka při změně](../debugger/media/breakpointwhenchanged.png "Zarážka při změně")

Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se zpráva s upozorněním. Pokud zadáte podmínku zarážky s platnou syntaxi ale s neplatnou sémantikou, zobrazí se upozornění při prvním dosažení zarážky. V obou případech ladicí program přeruší při volání zarážky neplatné. Zarážka je přeskočena pouze v případě, že je podmínka platná a je vyhodnocena jako `false`.

>[!NOTE]
>Chování pole když se **změnilo** v různých programovacích jazycích.
>- Pro nativní kód ladicí program nezahrne hodnocení první podmínku, která má být změněna, takže nebude zarážce při prvním hodnocení.
>- Pro spravovaný kód ladicí program po zvolení **změny** vyhledá zarážku na prvním vyhodnocení.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Použití ID objektů v podmíněnýchC# výrazech (a F# pouze)

 Existují situace, kdy budete chtít sledovat chování s určitým objektem. Můžete třeba chtít zjistit, proč objekt byl vložen do kolekce více než jednou. V C# a F#můžete vytvořit ID objektů pro konkrétní instance [odkazových typů](/dotnet/csharp/language-reference/keywords/reference-types)a použít je v podmínkách zarážek. ID objektu je generována modulem common language runtime (CLR) ladění služeb a přidružená k objektu.

**Vytvoření ID objektu:**

1. Nastavte zarážku v kódu některém místě po vytvoření objektu.

2. Spustit ladění a když se spuštění pozastaví na zarážce, vyberte **ladit** > **Windows** > **Locals** nebo **ALT**+**4** pro otevření okna **místní** hodnoty.

   V okně **místní** hodnoty Najděte konkrétní instanci objektu, klikněte na ni pravým tlačítkem myši a vyberte **vytvořit ID objektu**.

   V okně **místní** hodnoty by se měla zobrazit **$** plus číslo. To je ID objektu.

3. Přidat novou zarážku v okamžiku, kdy chcete prozkoumat; například když je přidán do kolekce. Klikněte pravým tlačítkem na zarážku a vyberte **podmínky**.

4. V poli **podmíněný výraz** použijte ID objektu. Pokud je například proměnná `item` objekt, který má být přidán do kolekce, vyberte **má hodnotu true** a zadejte **Item = = $\<n >** , kde \<n > je číslo ID objektu.

   Spuštění se přeruší v okamžiku, když je přidán do kolekce.

   Chcete-li odstranit ID objektu, klikněte pravým tlačítkem myši na proměnnou v okně **místní** hodnoty a vyberte **Odstranit ID objektu**.

> [!NOTE]
> ID objektů vytvořit slabé odkazy a nezabrání objektu je uvolněna z paměti. Jsou platné pouze pro aktuální relaci ladění.

### <a name="set-a-hit-count-condition"></a>Nastavení podmínky počtu přístupů

Pokud máte podezření, že se smyčka v kódu začne chovat po určitém počtu iterací, můžete nastavit zarážku, aby se po tomto počtu přístupů zastavilo provádění, a nemusíte opakovaně stisknout klávesu **F5** , aby se dosáhlo této iterace.

V části **podmínky** v okně **Nastavení zarážky** vyberte **Počet přístupů**a pak zadejte počet iterací. V následujícím příkladu je nastavena zarážka narazí při každé iteraci:

![Počet volání zarážky](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Nastavení podmínky filtru

Můžete omezit zarážku, chcete-li vyvolat pouze na zadané zařízení nebo v konkrétních procesů a vláken.

V **okně** **Nastavení zarážky** vyberte **Filtr**a potom zadejte jeden nebo více následujících výrazů:

- MachineName = "name"
- ProcessId = hodnota
- ProcessName = "name"
- ThreadId = hodnota
- ThreadName = "name"

Řetězcové hodnoty uzavřete do dvojitých uvozovek. Klauzule lze kombinovat pomocí `&` (a), `||` (nebo), `!` (NOT) a závorek.

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Nastavení zarážek funkcí

Můžete přerušit běh při volání funkce. To je užitečné, například když znáte název funkce, ale ne její umístění. Je také užitečné, pokud máte funkce se stejným názvem a chcete je rozdělit na všechny (například přetížené funkce nebo funkce v různých projektech).

**Nastavení zarážky funkce:**

1. Vyberte možnost **ladění** > **novou** zarážku > **zarážku funkce**nebo stiskněte klávesu **ALT**+**F9** > **CTRL**+**B**.

   V okně **zarážky** můžete také vybrat **Nový** > **zarážku funkce** .

1. V dialogovém okně **Nová zarážka funkce** zadejte do pole **název funkce** název funkce.

   Chcete-li zúžit specifikaci funkce:

   - Pomocí funkce plně kvalifikovaného názvu.

     Příklad: `Namespace1.ClassX.MethodA()`

   - Přidejte typy parametrů přetížené funkce.

     Příklad: `MethodA(int, string)`

   - Používá "!" symbolů k určení modulu.

     Příklad: `App1.dll!MethodA`

   - Použijte operátor kontextu v nativním kódu C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Příklad: `{MethodA, , App1.dll}+2`

1. V rozevíracím seznamu **jazyk** vyberte jazyk funkce.

1. Vyberte **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Nastavení zarážky funkce pomocí adresy paměti (pouze nativní C++)
 Chcete-li nastavit zarážku funkce v metodě volané konkrétní instanci třídy můžete adresu objektu.  Například vzhledem k adresovatelné objektu typu `my_class`můžete nastavit zarážku funkce v metodě `my_method`, kterou instance volá.

1. Nastavte zarážku někde, jakmile je vytvořena instance třídy.

2. Vyhledejte adresu instance (například `0xcccccccc`).

3. Vyberte možnost **ladění** > **novou** zarážku > **zarážku funkce**nebo stiskněte klávesu **ALT**+**F9** > **CTRL**+**B**.

4. Do pole **název funkce** přidejte následující a vyberte **C++** jazyk.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>Nastavení zarážek s daty (.NET Core 3,0 nebo vyšší)

Datové zarážky přeruší provádění při změně vlastnosti určitého objektu.

**Nastavení datové zarážky**

1. V projektu .NET Core spusťte ladění a počkejte na dosažení zarážky.

2. V okně **Automatické**hodnoty, **kukátko**nebo **místních** hodnot klikněte pravým tlačítkem na vlastnost a v místní nabídce vyberte možnost **přerušit při změně hodnoty** .

    ![Spravovaná datová zarážka](../debugger/media/managed-data-breakpoint.png "Spravovaná datová zarážka")

Datové zarážky v .NET Core nebudou fungovat pro:

- Vlastnosti, které se nerozšiřují v popiscích, místních hodnotách, Autoch nebo okno Kukátko
- Statické proměnné
- Třídy s atributem používání DebuggerTypeProxy
- Pole uvnitř struktur

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Nastavit zarážky dat (pouze C++ nativní)

 Body zarážek přeruší provádění když hodnota uložená v paměti zadaná adresa změní. Pokud hodnota je číst, ale nebyl změněn, spuštění nebude přerušeno.

**Nastavení datové zarážky:**

1. V projektu jazyka C++ spustit ladění a počkejte, dokud není dosaženo zarážky. V nabídce **ladění** vyberte možnost **nová zarážka** > **datové zarážky** .

    V okně **zarážky** můžete také vybrat **Nový** > **datové zarážky** nebo kliknout pravým tlačítkem myši na položku v okně **Automatické**hodnoty, **kukátko**nebo **místních** hodnot a vybrat možnost **přerušit při změně hodnoty** v místní nabídce.

2. Do pole **adresa** zadejte adresu paměti nebo výraz, který se vyhodnotí na adresu paměti. Zadejte například `&avar` pro přerušení, když se obsah proměnné `avar` změní.

3. V rozevíracím seznamu **počet bajtů** vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4**, ladicí program bude sledovat čtyři bajty počínaje `&avar` a přerušit, pokud kterákoli z těchto bajtů změní hodnotu.

Zarážky data nefungují za těchto podmínek:
- Proces, který se neladí se zapíše do umístění v paměti.
- Umístění v paměti jsou sdílena mezi dvěma nebo více procesy.
- Umístění v paměti je aktualizováno v rámci jádra. Například pokud je paměť předána funkci 32 Windows `ReadFile`, paměť bude aktualizována z režimu jádra, takže ladicí program nebude u aktualizace přerušen.
- Kde výraz kukátka je větší než 4 bajty na 32ovém hardwaru a 8 bajtů na 64 bitového hardwaru. Toto je omezení architektury x86.

> [!NOTE]
> - Datové zarážky, závisí na konkrétní paměťové adresy. Adresa proměnné změny z jedné relace ladění na další, abyste na konci každé relace ladění jsou automaticky zakázány datové zarážky.
>
> - Pokud nastavíte zarážku dat na lokální proměnné, zarážka zůstane povolena po skončení funkce, ale adresa paměti není nadále vhodné, takže nepředvídatelné chování zarážky. Pokud nastavíte zarážku dat na lokální proměnné, musíte odstranit nebo zakázat zarážku před ukončením funkce.

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Správa zarážek v okně zarážky

 Okno **zarážky** můžete použít k zobrazení a správě všech zarážek ve vašem řešení. Toto centralizované umístění je zvláště užitečné v na velkých projektech nebo pro komplexní scénáře ladění, kde jsou zarážky nezbytné.

V okně **zarážky** můžete vyhledat, seřadit, filtrovat, povolit nebo zakázat nebo odstranit zarážky. Můžete také nastavit podmínky a akce nebo přidat nové funkce nebo datová zarážka.

Chcete-li otevřít okno **zarážky** , vyberte možnost **ladění** > **Windows** > **zarážky**nebo stiskněte klávesy **ALT**+**F9** nebo **CTRL**+**ALT**+**B**.

![Okno zarážek](../debugger/media/breakpointswindow.png "Zarážky – okno")

Chcete-li vybrat sloupce, které mají být zobrazeny v okně **zarážky** , vyberte možnost **Zobrazit sloupce**. Vyberte záhlaví sloupce řazení podle sloupce v seznamu zarážek.

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Popisky zarážek
Štítky lze použít k řazení a filtrování seznamu zarážek v okně **zarážky** .

1. Chcete-li přidat popisek ke zarážce, klikněte pravým tlačítkem myši na zarážku v okně zdrojového kódu nebo v okně **zarážky** a pak vyberte **Upravit popisky**. Přidejte nový popisek nebo zvolte existující a pak vyberte **OK**.
2. V okně **zarážky** seřaďte seznam zarážek tak, že vyberete **popisky**, **podmínky**nebo jiná záhlaví sloupců. Výběrem možnosti **Zobrazit sloupce** na panelu nástrojů můžete vybrat sloupce, které chcete zobrazit.

### <a name="export-and-import-breakpoints"></a>Zarážky exportu a importu
 Pokud chcete uložit nebo sdílet stav a umístění vašich zarážek, můžete exportovat nebo importovat.

- Chcete-li exportovat jednu zarážku do souboru XML, klikněte pravým tlačítkem myši na zarážku v okně zdrojového kódu nebo **zarážky** a vyberte **exportovat** nebo **Exportovat vybrané**. Vyberte umístění exportu a pak vyberte **Uložit**. Výchozí umístění je složky řešení.
- Chcete-li exportovat několik zarážek, zaškrtněte v okně **zarážky** pole vedle zarážek nebo zadejte vyhledávací kritéria do **vyhledávacího** pole. Vyberte **exportovat všechny zarážky, které odpovídají ikoně aktuálního kritéria hledání** , a uložte soubor.
- Chcete-li exportovat všechny zarážky, zrušte výběr všech polí a nechte pole **Hledat** prázdné. Vyberte **exportovat všechny zarážky, které odpovídají ikoně aktuálního kritéria hledání** , a uložte soubor.
- Chcete-li importovat zarážky, vyberte v okně **zarážky** položku **importovat zarážky z ikony souboru** , přejděte do umístění souboru XML a vyberte možnost **otevřít**.

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Nastavení zarážek z okna ladicího programu

Můžete také nastavit zarážky z okna ladicího programu **zásobníku volání** a **zpětný překlad** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Nastavení zarážky v okně zásobník volání

 Chcete-li přerušit instrukci nebo čáru, na kterou se volání funkce vrátí, můžete nastavit zarážku v okně **zásobník volání** .

**Nastavení zarážky v okně zásobník volání:**

1. Chcete-li otevřít okno **zásobník volání** , je nutné pozastavit během ladění. Vyberte možnost **ladění** > **Windows** > **zásobník volání**nebo stiskněte klávesu **CTRL**+**ALT**+**C**.

2. V okně **zásobník volání** klikněte pravým tlačítkem myši na volání funkce a vyberte **zarážku** > **Vložit zarážku**nebo stiskněte **F9**.

   Vedle názvu volání funkce v zásobníku volání na levém okraji se zobrazí symbol zarážky.

Zarážka zásobníku volání se zobrazí v okně **zarážky** jako adresa s umístěním v paměti, které odpovídá další spustitelné instrukci ve funkci.

Ladicí program přeruší podle instrukce.

Další informace o zásobníku volání naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

Chcete-li vizuálně sledovat zarážky během provádění kódu, viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně zpětný překlad

1. Chcete-li otevřít okno **zpětný překlad** , je nutné pozastavit během ladění. Vyberte **ladění** > **Windows** > **zpětný překlad**nebo stiskněte **ALT**+**8**.

2. V okně **zpětný překlad** klikněte na levý okraj instrukce, na kterou chcete přerušit. Můžete ji také vybrat a stisknout klávesu **F9**nebo kliknout pravým tlačítkem a vybrat **zarážku** > **Vložit zarážku**.

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Psaní lepšího C# kódu pomocí sady Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Řešení potíží se zarážkami v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md)
