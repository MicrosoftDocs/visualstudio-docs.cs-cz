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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0865c71d2893203ca3af925da1d76946d882c4c4
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798580"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Použití zarážek v ladicím programu sady Visual Studio

Zarážky jsou jedním z nejdůležitějších technik ladění v sadě nástrojů pro vývojáře. Zarážky se nastavují všude, kde chcete pozastavit spuštění ladicího programu. Například můžete chtít zobrazit stav proměnných kódu nebo se podívat na zásobník volání na určitou zarážku.  Pokud se snažíte vyřešit upozornění nebo problém při použití zarážek, přečtěte si téma [řešení potíží se zarážkami v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Pokud znáte úlohu nebo problém, který se snažíte vyřešit, ale potřebujete znát, jaký typ zarážky chcete použít, přečtěte si téma [Nejčastější dotazy – Vyhledání funkce ladění](../debugger/find-your-debugging-task.yml#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Nastavení zarážek ve zdrojovém kódu

Zarážku můžete nastavit na jakémkoli řádku spustitelného kódu. Například v následujícím kódu jazyka C# můžete nastavit zarážku na řádku kódu s přiřazením proměnné ( `int testInt = 1` ), `for` smyčkou nebo jakýmkoli kódem uvnitř `for` smyčky. Nemůžete nastavit zarážku pro signatury metod, deklarace pro obor názvů, třídu nebo deklarace proměnných, pokud neexistuje žádné přiřazení a metodu getter/setter.

Chcete-li nastavit zarážku ve zdrojovém kódu, klikněte na levý levý okraj vedle řádku kódu. Můžete také vybrat řádek a stisknout klávesu **F9**, vybrat   >  **přepínač ladit zarážku** nebo kliknout pravým tlačítkem a vybrat **zarážku**  >  **Vložit** zarážku. Zarážka se zobrazuje na levém okraji jako červená tečka.

Pro většinu jazyků, včetně C#, zarážky a aktuální řádky spuštění jsou automaticky zvýrazněny. Pro kód jazyka C++ můžete zapnout zvýraznění zarážky a aktuální řádky výběrem **nástrojů** (nebo **ladění**) > **Možnosti**  >  **ladění**  >   **zvýraznit celý zdrojový řádek pro zarážky a aktuální příkaz (pouze C++)**.

![Nastavení zarážky](../debugger/media/basicbreakpoint.png "Základní zarážka")

Při ladění se provádění pozastaví na zarážce před provedením kódu na tomto řádku. Symbol zarážky zobrazuje žlutou šipku.

Na zarážce v následujícím příkladu je hodnota stále `testInt` 1. Hodnota se proto od inicializace proměnné (nastavená na hodnotu 1) nezměnila, protože příkaz žlutá ještě neprošla.

![Zastavené provádění zarážek](../debugger/media/breakpointexecution.png "Spuštění zarážky")

Když se ladicí program zastaví na zarážce, můžete se podívat [](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) na aktuální stav aplikace, včetně hodnot proměnných a [zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

Tady je několik obecných pokynů pro práci se zarážkami.

- Zarážka je přepínač. Můžete na něj kliknout, stisknout **klávesu F9** nebo ji odstranit nebo znovu vložit pomocí přepínače   >   ladění zarážky.

- Pokud chcete zarážku zakázat, aniž byste ji odstranili, najeďte myší nebo na něj klikněte pravým tlačítkem a vyberte **Zakázat zarážku**. Zakázané zarážky se zobrazují jako prázdné tečky na levém okraji nebo v **okně Breakpoints** (Zarážky). Pokud chcete zarážku znovu povolit, najeďte myší na zarážku nebo na ní klikněte pravým tlačítkem a vyberte **Povolit zarážku**.

- Nastavte podmínky a akce, přidejte a upravte popisky nebo exportujte zarážku tak, že na něj kliknete pravým tlačítkem a vyberete příslušný příkaz nebo na něj najedete myší a vyberete **ikonu** Nastavení.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akce zarážek a tracepointy

Tracepoint *je* zarážka, která vytiskne zprávu do **okna** Výstup. Trasovací bod může v programovacím jazyce fungovat jako dočasný příkaz trasování a nepozastaví provádění kódu. Trasovací bod vytvoříte nastavením speciální akce v **okně Nastavení zarážky.** Podrobné pokyny najdete v tématu [Použití trasovacích bodů v Visual Studio ladicím programu.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Podmínky zarážek

Nastavením podmínek můžete řídit, kdy a kde se zarážka provádí. Podmínkou může být libovolný platný výraz, který ladicí program rozpozná. Další informace o platných výrazech naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).

**Nastavení podmínky zarážky:**

1. Klikněte pravým tlačítkem myši na symbol zarážky a vyberte **podmínky** (nebo stiskněte **ALT**  +  **F9**, **C**). Nebo najeďte myší na symbol zarážky, vyberte ikonu **Nastavení** a pak v okně **Nastavení zarážky** vyberte **podmínky** .

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

Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se varovná zpráva. Zadáte-li podmínku zarážky s platnou syntaxí, ale neplatnou sémantikou, zobrazí se při prvním průchodu zarážky zpráva s upozorněním. V obou případech se ladicí program při použití neplatné zarážky přeruší. Zarážka se přeskočí jenom v případě, že je podmínka platná a vyhodnotí se jako `false` .

>[!NOTE]
> Pro **pole Při** změně ladicí program nepřizná první vyhodnocení podmínky za změnu, takže se při prvním vyhodnocení nenarazí na zarážku.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Použití ID objektů v podmíněných výrazech (pouze C# a F#)

 Existují případy, kdy chcete sledovat chování konkrétního objektu. Můžete například chtít zjistit, proč byl objekt vložen do kolekce více než jednou. V jazyce C# a F# můžete vytvořit ID [](/dotnet/csharp/language-reference/keywords/reference-types)objektů pro konkrétní instance odkazových typů a použít je v podmínkách zarážky. ID objektu je generováno ladicími službami modulu CLR (Common Language Runtime) a přidruženo k objektu .

**Vytvoření ID objektu:**

1. Po vytvoření objektu nastavte zarážku v kódu na nějaké místo.

2. Spusťte ladění a když se provádění na zarážce pozastaví, vyberte Ladit místní hodnoty Systému Windows (nebo stisknutím  >    >   **kláves Ctrl**  +  **Alt**  +  **V**, **L**) otevřete **okno Místní** hodnoty.

   Vyhledejte konkrétní instanci objektu v okně **Místní** hodnoty, klikněte na něj pravým tlačítkem a vyberte **Vytvořit ID objektu**.

   V okně Místní hodnoty by se mělo zobrazit plus **$** číslo.  Toto je ID objektu.

3. Do bodu, který chcete prozkoumat, přidejte novou zarážku. Například když má být objekt přidán do kolekce. Klikněte pravým tlačítkem na zarážku a vyberte **Podmínky**.

4. V poli Podmíněný výraz **použijte** ID objektu. Pokud je proměnná například objekt, který se má přidat do kolekce, vyberte Je true a zadejte `item` **item == $ \<n>**, kde je číslo ID  \<n> objektu.

   Provádění se přeruší v okamžiku, kdy má být tento objekt přidán do kolekce.

   Pokud chcete odstranit ID objektu, klikněte pravým tlačítkem na proměnnou v **okně Místní hodnoty** a vyberte Odstranit ID **objektu**.

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

1. Vyberte   >  **Ladit novou**  >  **zarážku funkce zarážky** nebo stiskněte **Ctrl**  +  **K**, **B**.

   Zarážku **nové funkce** můžete  >  **vybrat** také v **okně Zarážky.**

1. V **dialogovém okně Nová zarážka** funkce zadejte název funkce do **pole Název** funkce.

   Zúžení specifikace funkce:

   - Použijte plně kvalifikovaný název funkce.

     Příklad:  `Namespace1.ClassX.MethodA()`

   - Přidejte typy parametrů přetížené funkce.

     Příklad:  `MethodA(int, string)`

   - K určení modulu použijte symbol !.

     Příklad: `App1.dll!MethodA`

   - Použití operátoru kontextu v nativním jazyce C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Příklad: `{MethodA, , App1.dll}+2`

1. V **rozevíracím** seznamu Jazyk zvolte jazyk funkce.

1. Vyberte **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Nastavení zarážky funkce pomocí adresy paměti (pouze nativní jazyk C++)
 Adresu objektu můžete použít k nastavení zarážky funkce na metodě s názvem konkrétní instancí třídy.  Například na základě adresovatelného objektu typu můžete nastavit zarážku funkce na `my_class` `my_method` metodě, kterou instance volá.

1. Nastavte zarážku někde po vytvoření instance třídy.

2. Vyhledejte adresu instance (například `0xcccccccc` ).

3. Vyberte   >  **Ladit novou**  >  **zarážku funkce zarážky** nebo stiskněte **Ctrl**  +  **K**, **B**.

4. Do pole Název funkce přidejte **následující** kód a vyberte **Jazyk C++.**

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

1. V projektu C++ spusťte ladění a počkejte na dosažení zarážky. V nabídce **ladění** vyberte možnost Nová zarážka dat **zarážky**  >  .

    Můžete také vybrat možnost **Nová**  >  **zarážka dat** v **okně zarážky** nebo kliknout pravým tlačítkem myši na položku v okně **Automatické** hodnoty, **kukátko** nebo **místních** hodnot a vybrat možnost **přerušit při změně hodnoty** v místní nabídce.

2. Do pole **adresa** zadejte adresu paměti nebo výraz, který se vyhodnotí na adresu paměti. Například zadejte, že `&avar` se má přerušit, když se změní obsah proměnné `avar` .

3. V **rozevíracím seznamu Počet** bajtů vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4,** ladicí program bude sledovat čtyři bajty začínající na a přerušit, pokud některý `&avar` z těchto bajtů změní hodnotu.

Datové zarážky nefungují za následujících podmínek:
- Proces, který se neladit, zapisuje do umístění v paměti.
- Umístění paměti se sdílí mezi dvěma nebo více procesy.
- Umístění paměti se aktualizuje v rámci jádra. Pokud je například paměť předána 32bitové funkci Windows, paměť se aktualizuje z režimu jádra, takže ladicí program se při aktualizaci `ReadFile` nepřeruší.
- Kde je výraz watch větší než 4 bajty na 32bitovém hardwaru a 8 bajtů na 64bitovém hardwaru. Jedná se o omezení architektury x86.

> [!NOTE]
> - Datové zarážky závisí na konkrétních adresách paměti. Adresa proměnné se změní z jedné ladicí relace na další, takže datové zarážky jsou na konci každé ladicí relace automaticky zakázané.
>
> - Pokud nastavíte datovou zarážku v místní proměnné, zarážka zůstane po ukončení funkce povolená, ale adresa paměti už není použitelná, takže chování zarážky je nepředvídatelné. Pokud nastavíte datovou zarážku na místní proměnnou, měli byste ji před ukončením funkce odstranit nebo zakázat.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Správa zarážek v okně Breakpoints (Zarážky)

 K zobrazení a správě všech zarážek ve vašem řešení můžete použít okno **Breakpoints** (Zarážky). Toto centralizované umístění je zvlášť užitečné pro velké řešení nebo pro složité scénáře ladění, kde jsou kritické zarážky.

V okně **Breakpoints** (Zarážky) můžete hledat, řadit, filtrovat, zapnout/zakázat nebo odstranit zarážky. Můžete také nastavit podmínky a akce nebo přidat novou funkci nebo datovou zarážku.

Pokud chcete otevřít **okno Breakpoints** (Zarážky), vyberte **Debug** Windows  >    >  **Breakpoints**(Ladit zarážky windows) nebo stiskněte **Ctrl** + **Alt** + **B.**

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

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Nastavení zarážky v okně Zásobník volání

 Pokud chcete přerušit instrukci nebo řádek, na který se volající funkce vrací, můžete nastavit zarážku v **okně Zásobník** volání.

**Nastavení zarážky v okně Zásobník volání:**

1. Pokud chcete otevřít **okno Zásobník volání,** musíte být během ladění pozastaveni. Vyberte   >  **Ladit zásobník** volání systému Windows nebo stiskněte  >   **Ctrl** + **Alt** + **C.**

2. V okně **Zásobník volání klikněte** pravým tlačítkem na volající funkci a vyberte Breakpoint Insert **Breakpoint**(Zarážka vložení zarážky) nebo stiskněte klávesu  >   **F9**.

   Symbol zarážky se zobrazí vedle názvu volání funkce v levém okraji zásobníku volání.

Zarážka zásobníku volání se zobrazí v okně **Breakpoints** (Zarážky) jako adresa s umístěním v paměti, které odpovídá další spustitelné instrukci ve funkci .

Ladicí program se na pokyn přeruší.

Další informace o zásobníku volání najdete v tématu [Postupy: Použití okna Zásobník volání.](../debugger/how-to-use-the-call-stack-window.md)

Pokud chcete vizuálně trasovat zarážky během provádění kódu, podívejte se na mapování metod [v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně Zpětný překlad

1. Chcete-li **otevřít okno Zpětný** překlad, musíte být během ladění pozastaveni. Vyberte **Debug** Windows  >    >  **Disassembly (Ladit** zpětný překlad systému Windows) nebo stiskněte **Ctrl** + **Alt** + **D.**

2. V okně **Zpětný překlad** klikněte na levý okraj instrukce, u které chcete příkaz přerušit. Můžete ji také vybrat a stisknout **klávesu F9** nebo kliknout pravým tlačítkem a vybrat **Breakpoint** Insert Breakpoint (Zarážka  >  **vložit zarážku).**

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Psaní lepšího kódu C# pomocí Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Řešení potíží se zarážkami v Visual Studio ladicím programu](../debugger/troubleshooting-breakpoints.md)
