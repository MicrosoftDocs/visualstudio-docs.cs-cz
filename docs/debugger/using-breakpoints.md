---
title: Použití zarážek v ladicím programu | Microsoft Docs
description: Seznamte se se zarážkami, jedním z nejdůležitějších technik ladění. Článek popisuje akce zarážky, trasováním, podmínky a mnoho dalších.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
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
ms.openlocfilehash: c8487482b1d87ba87dfc3a8b1e07be1360227a2f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150441"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Použití zarážek v ladicím programu sady Visual Studio

Zarážky jsou jedním z nejdůležitějších technik ladění v sadě nástrojů pro vývojáře. Zarážky se nastavují všude, kde chcete pozastavit spuštění ladicího programu. Například můžete chtít zobrazit stav proměnných kódu nebo se podívat na zásobník volání na určitou zarážku.  Pokud se snažíte vyřešit upozornění nebo problém při použití zarážek, přečtěte si téma [řešení potíží se zarážkami v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Pokud znáte úlohu nebo problém, který se snažíte vyřešit, ale potřebujete znát, jaký typ zarážky chcete použít, přečtěte si téma [Nejčastější dotazy – Vyhledání funkce ladění](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Nastavení zarážek ve zdrojovém kódu

Zarážku můžete nastavit na jakémkoli řádku spustitelného kódu. Například v následujícím kódu jazyka C# můžete nastavit zarážku na řádku kódu s přiřazením proměnné ( `int testInt = 1` ), `for` smyčkou nebo jakýmkoli kódem uvnitř `for` smyčky. Nemůžete nastavit zarážku pro signatury metod, deklarace pro obor názvů, třídu nebo deklarace proměnných, pokud neexistuje žádné přiřazení a metodu getter/setter.

Chcete-li nastavit zarážku ve zdrojovém kódu, klikněte na levý levý okraj vedle řádku kódu. Můžete také vybrat řádek a stisknout klávesu **F9**, vybrat   >  **přepínač ladit zarážku** nebo kliknout pravým tlačítkem a vybrat **zarážku**  >  **Vložit** zarážku. Zarážka se zobrazuje na levém okraji jako červená tečka.

Pro většinu jazyků, včetně C#, zarážky a aktuální řádky spuštění jsou automaticky zvýrazněny. Pro kód jazyka C++ můžete zapnout zvýraznění zarážky a aktuální řádky výběrem **nástrojů** (nebo **ladění**) > **Možnosti**  >  **ladění**  >   **zvýraznit celý zdrojový řádek pro zarážky a aktuální příkaz (pouze C++)**.

![Nastavení zarážky](../debugger/media/basicbreakpoint.png "Základní zarážka")

Při ladění se spuštění pozastaví na zarážce, než se kód na tomto řádku spustí. Symbol zarážky zobrazuje žlutou šipku.

Na zarážce v následujícím příkladu `testInt` je hodnota stále 1. Proto se hodnota od inicializace proměnné nezměnila (nastavená na hodnotu 1), protože příkaz žlutý nebyl dosud proveden.

![Spuštění zarážky bylo zastaveno.](../debugger/media/breakpointexecution.png "Spuštění zarážky")

Když se ladicí program zastaví na zarážce, můžete se podívat na aktuální stav aplikace, včetně [hodnot proměnných](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) a [zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

Zde je několik obecných pokynů pro práci se zarážkami.

- Zarážka je přepínač. Můžete kliknout na ni, stisknout **F9** nebo pomocí příkazu **ladit**  >  **Přepnout zarážku** odstranit nebo ho znovu vložit.

- Chcete-li zakázat zarážku bez jejich odstranění, najeďte myší na ni nebo klikněte na ni pravým tlačítkem a vyberte možnost **Zakázat zarážku**. Zakázané zarážky se zobrazují jako prázdné tečky v levém okraji nebo v okně **zarážky** . Pokud chcete zarážku znovu povolit, najeďte myší na ni nebo klikněte na ni pravým tlačítkem a vyberte **Povolit zarážku**.

- Nastavte podmínky a akce, přidejte a upravte popisky nebo exportujte zarážku tak, že na ni kliknete pravým tlačítkem myši a vyberete příslušný příkaz nebo když na něj najedete a vyberete ikonu **Nastavení** .

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akce zarážek a trasováním

*Zarážka s trasováním* je zarážka, která vytiskne zprávu do okna **výstup** . Zarážka s trasováním může fungovat jako dočasný příkaz trace v programovacím jazyce a neumožňuje pozastaví provádění kódu. Zarážka s trasováním vytvoříte tak, že v okně **Nastavení zarážky** nastavíte zvláštní akci. Podrobné pokyny najdete v tématu [použití trasováním v ladicím programu sady Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Podmínky zarážky

Můžete určit, kdy a kde se zarážka spustí, nastavením podmínek. Podmínkou může být libovolný platný výraz, který ladicí program rozpozná. Další informace o platných výrazech naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).

**Nastavení podmínky zarážky:**

1. Klikněte pravým tlačítkem na symbol zarážky a vyberte **podmínky**. Nebo najeďte myší na symbol zarážky, vyberte ikonu **Nastavení** a pak v okně **Nastavení zarážky** vyberte **podmínky** .

   V okně **zarážky** můžete také nastavit podmínky tak, že kliknete pravým tlačítkem myši na zarážku a vyberete **Nastavení** a pak vyberete **podmínky**.

   ![Nastavení zarážky](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. V rozevíracím seznamu vyberte **podmíněný výraz**, **Počet volání** nebo **Filtr** a nastavte hodnotu odpovídajícím způsobem.

3. Vyberte **Zavřít** nebo stiskněte **klávesu CTRL** + **ENTER** a zavřete tak okno **Nastavení zarážky** . Nebo v okně **zarážky** kliknutím na **tlačítko OK** zavřete dialogové okno.

Zarážky s nastavenými podmínkami se zobrazí se **+** symbolem v oknech zdrojový kód a **zarážky** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Vytvoření podmíněného výrazu

Když vyberete **podmíněný výraz**, můžete zvolit mezi dvěma podmínkami: **je true** nebo **při změně**. Vyberte **hodnotu true** , pokud chcete přerušit, když je výraz splněn, nebo **když se změní** na přerušit, když se změní hodnota výrazu.

V následujícím příkladu je zarážka dosažena pouze v případě, že hodnota `testInt` je **4**:

![Podmínka zarážky je pravdivá.](../debugger/media/breakpointconditionistrue.png "Zarážka je pravdivá.")

V následujícím příkladu je zarážka dosažena pouze v případě, že se jedná o hodnotu `testInt` změny:

![Zarážka při změně](../debugger/media/breakpointwhenchanged.png "Zarážka při změně")

Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se varovná zpráva. Zadáte-li podmínku zarážky s platnou syntaxí, ale neplatnou sémantikou, zobrazí se při prvním průchodu zarážky zpráva s upozorněním. V obou případech dojde k přerušení ladicího programu, pokud narazí na neplatnou zarážku. Zarážka je přeskočena pouze v případě, že je podmínka platná a je vyhodnocena jako `false` .

>[!NOTE]
> Pro pole **když změněno** , ladicí program nepovažuje první vyhodnocení podmínky za účelem změny, takže neobjeví zarážku při prvním vyhodnocení.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Použití ID objektů v podmíněných výrazech (pouze C# a F #)

 Existují situace, kdy chcete sledovat chování určitého objektu. Například může být vhodné zjistit, proč byl objekt vložen do kolekce více než jednou. V jazyce C# a F # můžete vytvořit ID objektů pro konkrétní instance [odkazových typů](/dotnet/csharp/language-reference/keywords/reference-types)a použít je v podmínkách zarážek. ID objektu je vygenerováno službami ladění modulu CLR (Common Language Runtime) a přidruženy k objektu.

**Vytvoření ID objektu:**

1. Nastavte zarážku v kódu na místo, kde je objekt vytvořen.

2. Spustit ladění a když se spuštění pozastaví na zarážce, vyberte možnost **ladění**  >    >  **místních** oken nebo **ALT** + **4** pro otevření okna **místní** hodnoty.

   V okně **místní** hodnoty Najděte konkrétní instanci objektu, klikněte na ni pravým tlačítkem myši a vyberte **vytvořit ID objektu**.

   **$** V okně **místní** hodnoty by se měla zobrazit znaménko plus. Toto je ID objektu.

3. Přidejte novou zarážku v bodu, který chcete prozkoumat; například při přidání objektu do kolekce. Klikněte pravým tlačítkem na zarážku a vyberte **podmínky**.

4. V poli **podmíněný výraz** použijte ID objektu. Například pokud `item` je proměnná objekt, který má být přidán do kolekce, vyberte **má hodnotu true** a zadejte **Item = = $ \<n>**, kde \<n> je číslo ID objektu.

   Spuštění bude přerušeno v okamžiku, kdy má být objekt přidán do kolekce.

   Chcete-li odstranit ID objektu, klikněte pravým tlačítkem myši na proměnnou v okně **místní** hodnoty a vyberte **Odstranit ID objektu**.

> [!NOTE]
> ID objektů vytvářejí slabé odkazy a nebrání v uvolňování paměti objektu. Jsou platné pouze pro aktuální relaci ladění.

### <a name="set-a-hit-count-condition"></a>Nastavení podmínky počtu přístupů

Pokud máte podezření, že se smyčka v kódu začne chovat po určitém počtu iterací, můžete nastavit zarážku, aby se po tomto počtu přístupů zastavilo provádění, a nemusíte opakovaně stisknout klávesu **F5** , aby se dosáhlo této iterace.

V části **podmínky** v okně **Nastavení zarážky** vyberte **Počet přístupů** a pak zadejte počet iterací. V následujícím příkladu je zarážka nastavená tak, aby se vyčerpala v každé jiné iteraci:

![Počet volání zarážky](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Nastavení podmínky filtru

Zarážku můžete omezit tak, aby se aktivovala jenom na zadaných zařízeních, nebo v zadaných procesech a vláknech.

V **okně** **Nastavení zarážky** vyberte **Filtr** a potom zadejte jeden nebo více následujících výrazů:

- Nazev_pocitace = "Name"
- ProcessId = hodnota
- Název procesu = "Name"
- IDvlákna = hodnota
- Thread = "Name"

Uzavřete řetězcové hodnoty do dvojitých uvozovek. Klauzule lze kombinovat pomocí `&` (a), `||` (nebo), `!` (NOT) a závorek.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Nastavení zarážek funkcí

Můžete přerušit provádění při volání funkce. To je užitečné, například když znáte název funkce, ale ne její umístění. Je také užitečné, pokud máte funkce se stejným názvem a chcete je rozdělit na všechny (například přetížené funkce nebo funkce v různých projektech).

**Nastavení zarážky funkce:**

1. Vyberte **ladit** novou zarážku funkce zarážky  >    >  nebo stiskněte **ALT** + **F9**  >  **CTRL** + **B**.

     >  V okně **zarážky** můžete také vybrat novou **zarážku funkce** .

1. V dialogovém okně **Nová zarážka funkce** zadejte do pole **název funkce** název funkce.

   Zúžení specifikace funkce:

   - Použijte plně kvalifikovaný název funkce.

     Případě  `Namespace1.ClassX.MethodA()`

   - Přidejte typy parametrů přetížené funkce.

     Případě  `MethodA(int, string)`

   - K určení modulu použijte symbol '! '.

     Příklad: `App1.dll!MethodA`

   - Použijte operátor kontextu v nativním jazyce C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Příklad: `{MethodA, , App1.dll}+2`

1. V rozevíracím seznamu **jazyk** vyberte jazyk funkce.

1. Vyberte **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Nastavení zarážky funkce pomocí adresy paměti (pouze nativní C++)
 Můžete použít adresu objektu pro nastavení zarážky funkce pro metodu volanou určitou instancí třídy.  Například vzhledem k adresovatelné objektu typu `my_class` můžete nastavit zarážku funkce na `my_method` metodu, kterou instance volá.

1. Nastavte zarážku někam po vytvoření instance třídy.

2. Vyhledejte adresu instance (například `0xcccccccc` ).

3. Vyberte **ladit** novou zarážku funkce zarážky  >    >  nebo stiskněte **ALT** + **F9**  >  **CTRL** + **B**.

4. Do pole **název funkce** přidejte následující a vyberte jazyk **C++** .

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Nastavení zarážek s daty (.NET Core 3,0 nebo vyšší)

Datové zarážky přeruší provádění při změně vlastnosti určitého objektu.

**Nastavení datové zarážky**

1. V projektu .NET Core spusťte ladění a počkejte na dosažení zarážky.

2. V okně **Automatické** hodnoty, **kukátko** nebo **místních** hodnot klikněte pravým tlačítkem na vlastnost a v místní nabídce vyberte možnost **přerušit při změně hodnoty** .

    ![Spravovaná datová zarážka](../debugger/media/managed-data-breakpoint.png "Spravovaná datová zarážka")

Datové zarážky v .NET Core nebudou fungovat pro:

- Vlastnosti, které se nerozšiřují v popiscích, místních hodnotách, Autoch nebo okno Kukátko
- Statické proměnné
- Třídy s atributem používání DebuggerTypeProxy
- Pole uvnitř struktur

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Nastavení zarážek s daty (jenom nativní C++)

 Datové zarážky přeruší provádění, když se změní hodnota uložená v zadané adrese paměti. Pokud je hodnota čtena, ale nemění se, provádění není přerušeno.

**Nastavení datové zarážky:**

1. V projektu C++ spusťte ladění a počkejte na dosažení zarážky. V nabídce **ladění** vyberte Nová zarážka data **zarážky**  >   .

    Můžete také vybrat možnost **Nová**  >  **zarážka dat** v **okně zarážky** nebo kliknout pravým tlačítkem myši na položku v okně **Automatické** hodnoty, **kukátko** nebo **místních** hodnot a vybrat možnost **přerušit při změně hodnoty** v místní nabídce.

2. Do pole **adresa** zadejte adresu paměti nebo výraz, který se vyhodnotí na adresu paměti. Například zadejte, že `&avar` se má přerušit, když se změní obsah proměnné `avar` .

3. V rozevíracím seznamu **počet bajtů** vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4**, ladicí program bude sledovat čtyři bajty počínaje `&avar` a přerušit, pokud kterákoli z těchto bajtů změní hodnotu.

Datové zarážky nefungují za následujících podmínek:
- Proces, který neladí zápisy do umístění v paměti.
- Umístění v paměti je sdíleno mezi dvěma nebo více procesy.
- Umístění v paměti je aktualizováno v rámci jádra. Například pokud je paměť předána funkci 32 Windows `ReadFile` , bude paměť aktualizována z režimu jádra, takže ladicí program nebude u aktualizace přerušen.
- Kde výraz kukátka je větší než 4 bajty na 32ovém hardwaru a 8 bajtů na 64 bitového hardwaru. Toto je omezení architektury x86.

> [!NOTE]
> - Datové zarážky závisí na konkrétních adresách paměti. Adresa proměnné se mění z jedné relace ladění na další, takže se na konci každé relace ladění automaticky zakážou datové zarážky.
>
> - Pokud nastavíte zarážku dat na lokální proměnné, zarážka zůstane povolena, když funkce skončí, ale adresa paměti již není platná, takže chování zarážky je nepředvídatelné. Pokud nastavíte zarážku dat na lokální proměnné, měli byste před ukončením funkce odstranit nebo zakázat zarážku.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Správa zarážek v okně zarážky

 Okno **zarážky** můžete použít k zobrazení a správě všech zarážek ve vašem řešení. Toto centralizované umístění je zvláště užitečné ve velkých řešeních nebo pro složité scénáře ladění, kde jsou zarážky kritické.

V okně **zarážky** můžete vyhledat, seřadit, filtrovat, povolit nebo zakázat nebo odstranit zarážky. Můžete také nastavit podmínky a akce nebo přidat novou funkci nebo datovou zarážku.

Chcete-li otevřít okno **zarážky** , vyberte možnost **ladění**  >    >  **zarážek** se systémem Windows nebo stiskněte klávesy **ALT** + **F9** nebo **CTRL** + **ALT** + **B**.

![Zarážky – okno](../debugger/media/breakpointswindow.png "Zarážky – okno")

Chcete-li vybrat sloupce, které mají být zobrazeny v okně **zarážky** , vyberte možnost **Zobrazit sloupce**. Vyberte záhlaví sloupce pro seřazení seznamu zarážek podle daného sloupce.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Popisky zarážek
Štítky lze použít k řazení a filtrování seznamu zarážek v okně **zarážky** .

1. Chcete-li přidat popisek ke zarážce, klikněte pravým tlačítkem myši na zarážku v okně zdrojového kódu nebo v okně **zarážky** a pak vyberte **Upravit popisky**. Přidejte nový popisek nebo zvolte existující a pak vyberte **OK**.
2. V okně **zarážky** seřaďte seznam zarážek tak, že vyberete **popisky**, **podmínky** nebo jiná záhlaví sloupců. Výběrem možnosti **Zobrazit sloupce** na panelu nástrojů můžete vybrat sloupce, které chcete zobrazit.

### <a name="export-and-import-breakpoints"></a>Export a import zarážek
 Chcete-li uložit nebo sdílet stav a umístění zarážek, můžete je exportovat nebo importovat.

- Chcete-li exportovat jednu zarážku do souboru XML, klikněte pravým tlačítkem myši na zarážku v okně zdrojového kódu nebo **zarážky** a vyberte **exportovat** nebo **Exportovat vybrané**. Vyberte umístění exportu a pak vyberte **Uložit**. Výchozím umístěním je složka řešení.
- Chcete-li exportovat několik zarážek, zaškrtněte v okně **zarážky** pole vedle zarážek nebo zadejte vyhledávací kritéria do **vyhledávacího** pole. Vyberte **exportovat všechny zarážky, které odpovídají ikoně aktuálního kritéria hledání** , a uložte soubor.
- Chcete-li exportovat všechny zarážky, zrušte výběr všech polí a nechte pole **Hledat** prázdné. Vyberte **exportovat všechny zarážky, které odpovídají ikoně aktuálního kritéria hledání** , a uložte soubor.
- Chcete-li importovat zarážky, vyberte v okně **zarážky** položku **importovat zarážky z ikony souboru** , přejděte do umístění souboru XML a vyberte možnost **otevřít**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Nastavení zarážek z okna ladicího programu

Můžete také nastavit zarážky z okna ladicího programu **zásobníku volání** a **zpětný překlad** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Nastavení zarážky v okně zásobník volání

 Chcete-li přerušit instrukci nebo čáru, na kterou se volání funkce vrátí, můžete nastavit zarážku v okně **zásobník volání** .

**Nastavení zarážky v okně zásobník volání:**

1. Chcete-li otevřít okno **zásobník volání** , je nutné pozastavit během ladění. Vyberte **ladit**  >    >  **zásobník volání** systému Windows nebo stiskněte klávesovou **zkratku CTRL** + **+** + **C**.

2. V okně **zásobník volání** klikněte pravým tlačítkem myši na volání funkce a vyberte **zarážku**  >  **Vložit zarážku** nebo stiskněte klávesu **F9**.

   Symbol zarážky se zobrazí vedle názvu volání funkce na levém okraji zásobníku volání.

Zarážka zásobníku volání se zobrazí v okně **zarážky** jako adresa s umístěním v paměti, které odpovídá další spustitelné instrukci ve funkci.

Ladicí program se v instrukci přerušuje.

Další informace o zásobníku volání naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

Chcete-li vizuálně sledovat zarážky během provádění kódu, viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně zpětný překlad

1. Chcete-li otevřít okno **zpětný překlad** , je nutné pozastavit během ladění. Vyberte **ladit**  >    >  **zpětný překlad** Windows, nebo stiskněte **ALT +** + .

2. V okně **zpětný překlad** klikněte na levý okraj instrukce, na kterou chcete přerušit. Můžete ji také vybrat a stisknout klávesu **F9** nebo kliknout pravým tlačítkem a vybrat **zarážku**  >  **Vložit** zarážku.

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Zápis lepšího kódu v jazyce C# pomocí sady Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Řešení potíží se zarážkami v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md)
