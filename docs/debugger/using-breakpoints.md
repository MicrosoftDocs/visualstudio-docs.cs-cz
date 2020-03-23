---
title: Použití zarážek v ladicím programu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302033"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Použití zarážek v ladicím programu sady Visual Studio

Zarážky jsou jedním z nejdůležitějších ladicích technik v sadě nástrojů vývojáře. Zarážky nastavit všude, kde chcete pozastavit spuštění ladicího programu. Můžete například chtít zobrazit stav proměnných kódu nebo se podívat na zásobník volání v určité zarážky.  Pokud se pokoušíte vyřešit upozornění nebo problém při používání zarážek, [přečtěte si téma Poradce při potížích s zarážky mise v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Pokud znáte úkol nebo problém, který se pokoušíte vyřešit, ale potřebujete vědět, jaký druh zarážky použít, přečtěte si informace [o úloze ladění](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Nastavení zarážek ve zdrojovém kódu

Zarážku můžete nastavit na libovolném řádku spustitelného kódu. Například v následujícím kódu Jazyka C# můžete nastavit zarážku `for` na deklaraci proměnné, smyčky nebo libovolného `for` kódu uvnitř smyčky. Nelze nastavit zarážku na obor názvů nebo deklarace třídy nebo na podpis metody.

Chcete-li nastavit zarážku ve zdrojovém kódu, klepněte na zcela levý okraj vedle řádku kódu. Můžete také vybrat čáru a stisknout **klávesu F9**, vybrat možnost **Ladění** > **přepínací zarážky**nebo klepnout pravým tlačítkem myši a vybrat**zarážku Vložení zarážky** **zarážky** > . Zarážka se zobrazí jako červená tečka v levém okraji.

Pro většinu jazyků, včetně C#, zarážka a aktuální spuštění řádky jsou automaticky zvýrazněny. Pro kód C++ můžete zapnout zvýraznění zarážky a aktuálnířádky výběrem **nástroje** (nebo **ladění)**> **možnosti** > **ladění zvýraznit** >  **zvýraznit celý zdrojový řádek pro zarážky a aktuální příkaz (pouze C++).**

![Nastavení zarážky](../debugger/media/basicbreakpoint.png "Základní zarážka")

Při ladění, spuštění pozastaví na zarážky, před kód na tomto řádku je spuštěn. Symbol zarážky zobrazuje žlutou šipku.

Na zarážku v následujícím `testInt` příkladu hodnota je stále 1. Hodnota se tedy od inicializování proměnné (nastavená na hodnotu 1) nezměnila, protože příkaz ve žluté barvě ještě nebyl proveden.

![Spuštění zarážky bylo zastaveno.](../debugger/media/breakpointexecution.png "Spuštění zarážky")

Když se ladicí program zastaví na zarážky, můžete se podívat na aktuální stav aplikace, včetně [hodnot proměnných](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) a [zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

Zde je několik obecných pokynů pro práci s zarážky.

- Zarážka je přepínač. Můžete na něj klepnout, stisknout **klávesu F9**nebo ji odstranit nebo znovu vložit pomocí funkce **Ladění** > **přepnout.**

- Chcete-li zakázat zarážku bez odstranění, najeďte na ni nebo na ni klepněte pravým tlačítkem myši a vyberte **Zakázat zarážku**. Zakázané zarážky se zobrazí jako prázdné tečky v levém okraji nebo v okně **Zarážky.** Chcete-li zarážku znovu povolit, najeďte na ni nebo na ni klepněte pravým tlačítkem myši a vyberte **Povolit zarážku**.

- Nastavte podmínky a akce, přidejte a upravte popisky nebo exportujte zarážku tak, že na ni kliknete pravým tlačítkem myši a vyberete příslušný příkaz nebo na něj najedete myší a vyberete ikonu **Nastavení.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akce zarážky a stopovací body

Trasovací *bod* je zarážka, která vytiskne zprávu do okna **Výstup.** Trasovací bod může fungovat jako dočasný příkaz trasování v programovacím jazyce a nepozastaví provádění kódu. Trasovací bod vytvoříte nastavením speciální akce v okně **Nastavení zarážky.** Podrobné pokyny naleznete [v tématu Použití trasovacích bodů v ladicím programu sady Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Podmínky zarážky

Nastavením podmínek můžete určit, kdy a kde se zarážka spustí. Podmínkou může být libovolný platný výraz, který ladicí program rozpozná. Další informace o platných výrazech naleznete [v tématu Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).

**Nastavení podmínky zarážky:**

1. Klepněte pravým tlačítkem myši na symbol zarážky a vyberte **možnost Podmínky**. Nebo najeďte na symbol zarážky, vyberte ikonu **Nastavení** a pak v okně **Nastavení zarážky** vyberte **Podmínky.**

   Podmínky můžete také nastavit v okně **Zarážky** tak, že klepnete pravým tlačítkem myši na zarážku a vyberete **Nastavení**a pak vyberete **Podmínky**.

   ![Nastavení zarážky](../debugger/media/breakpointsettings.png "Nastavení zarážky")

2. V rozevíracím seznamu vyberte **podmíněný výraz**, **počet přístupů**nebo **filtr**a odpovídajícím způsobem nastavte hodnotu.

3. Vyberte **Zavřít** nebo stisknutím **klávesy Ctrl**+**Enter** zavřete okno **Nastavení zarážky.** Nebo z okna **Zarážky** vyberte **OK,** chcete-li dialogové okno zavřít.

Zarážky s nastavenými **+** podmínkami se zobrazí se symbolem ve zdrojovém kódu a **oknech zarážek.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Vytvoření podmíněného výrazu

Když vyberete **Podmíněný výraz**, můžete si vybrat mezi dvěma podmínkami: **Je true** nebo Při **změně**. Zvolte **Je pravda,** aby se přetrhla, když je výraz splněn, nebo **Při změně** na přerušení při změně hodnoty výrazu.

V následujícím příkladu je zarážka `testInt` přístupů pouze v případě, že hodnota je **4**:

![Podmínka zarážky je pravdivá](../debugger/media/breakpointconditionistrue.png "Zarážka je pravdivá")

V následujícím příkladu je zarážka `testInt` přístupů pouze v případě, že hodnota změny:

![Zarážka Při změně](../debugger/media/breakpointwhenchanged.png "Zarážka Při změně")

Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se varovná zpráva. Pokud zadáte podmínku zarážky s platnou syntaxí, ale neplatnou sémantikou, zobrazí se při prvním zásahu zarážky varovná zpráva. V obou případech ladicí program se přeruší, když narazí na neplatnou zarážku. Zarážka je přeskočena pouze v `false`případě, že je podmínka platná a vyhodnocuje se .

>[!NOTE]
>Chování pole **Při změně** se liší pro různé programovací jazyky.
>- Pro nativní kód ladicí program nepovažuje první vyhodnocení podmínky za změnu, takže nenarazí na zarážku v prvním hodnocení.
>- Pro spravovaný kód ladicí program narazí na zarážku při prvním vyhodnocení po **Při změně** je vybrána.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Použití ID objektů v podmíněných výrazech (pouze C# a F#)

 Jsou chvíle, kdy chcete sledovat chování určitého objektu. Můžete například chtít zjistit, proč byl objekt vložen do kolekce více než jednou. V C# a F# můžete vytvořit ID objektů pro určité instance [typů odkazů](/dotnet/csharp/language-reference/keywords/reference-types)a použít je v podmínkách zarážky. ID objektu je generováno služby ladění clr (COMMON Language runtime) a je přidruženo k objektu.

**Vytvoření ID objektu:**

1. Nastavte zarážku v kódu na místě po vytvoření objektu.

2. Spusťte ladění a při pozastavení provádění na zarážky, vyberte **ladění** > **Windows** > **Locals** nebo **Alt**+**4** otevřít místní okno. **Locals**

   Najděte konkrétní instanci objektu v okně **Locals,** klepněte na ni pravým tlačítkem myši a vyberte **Příkaz Vytvořit ID objektu**.

   V okně **$** **Locals** byste měli vidět plus číslo. Toto je ID objektu.

3. Přidejte novou zarážku v bodě, který chcete prozkoumat; například když má být objekt přidán do kolekce. Klepněte pravým tlačítkem myši na zarážku a vyberte příkaz **Podmínky**.

4. V poli **Podmíněný výraz** použijte ID objektu. Například `item` pokud proměnná je objekt, který má být přidán do kolekce, vyberte Je **true** a typ **položky == $\<n>**, kde \<n> je číslo ID objektu.

   Spuštění bude přerušit v okamžiku, kdy má být tento objekt přidán do kolekce.

   Chcete-li ID objektu odstranit, klepněte pravým tlačítkem myši na proměnnou v okně **Locals** a vyberte **příkaz Odstranit ID objektu**.

> [!NOTE]
> ID objektů vytvořit slabé odkazy a nebrání objektu jsou uvolněny. Jsou platné pouze pro aktuální relaci ladění.

### <a name="set-a-hit-count-condition"></a>Nastavení podmínky počtu přístupů

Pokud máte podezření, že smyčka v kódu začne nechová po určitý počet iterací, můžete nastavit zarážku zastavit provádění po tomto počtu přístupů, spíše než muset opakovaně stiskněte **klávesu F5** k dosažení této iterace.

V **části Podmínky** v okně Nastavení **zarážky** vyberte **počet přístupů**a zadejte počet iterací. V následujícím příkladu je zarážka nastavena na přístup na každou další iteraci:

![Počet přístupů zarážky](../debugger/media/breakpointhitcount.png "Počet zásahů zarážky")

### <a name="set-a-filter-condition"></a>Nastavení podmínky filtru

Zarážku můžete omezit na spálení pouze na určených zařízeních nebo v určených procesech a vláknech.

V **části Podmínky** v okně Nastavení **zarážky** vyberte **Filtr**a zadejte jeden nebo více z následujících výrazů:

- Název_počítače = "název"
- ProcessId = hodnota
- Název_procesu = "název"
- ThreadId = hodnota
- Název_vlákna = "název"

Uzavřete hodnoty řetězce do dvojitých uvozovek. Můžete kombinovat klauzule `&` pomocí `||` (AND), `!` (OR), (NOT) a závorek.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Nastavení zarážek funkce

Spuštění můžete přerušit, když je volána funkce. To je užitečné, například když znáte název funkce, ale ne její umístění. Je také užitečné, pokud máte funkce se stejným názvem a chcete přerušit na všechny (například přetížené funkce nebo funkce v různých projektech).

**Nastavení zarážky funkce:**

1. Vyberte **ladit** > **novou zarážky zarážky zarážky zarážky** > **Function Breakpoint**nebo stiskněte **alt**+**F9** > **Ctrl**+**B**.

   V okně **New** >  **Zarážky** můžete také vybrat**zarážky nové funkce.**

1. V dialogovém okně **Zarážky nové funkce** zadejte název funkce do pole **Název funkce.**

   Chcete-li zúžit specifikaci funkce:

   - Použijte plně kvalifikovaný název funkce.

     Příklad:`Namespace1.ClassX.MethodA()`

   - Přidejte typy parametrů přetížené funkce.

     Příklad:`MethodA(int, string)`

   - Modul můžete zadat pomocí symbolu '!'.

     Příklad: `App1.dll!MethodA`

   - Použijte operátor kontextu v nativním jazyce C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Příklad: `{MethodA, , App1.dll}+2`

1. V rozevíracím **souboru Jazyk** zvolte jazyk funkce.

1. Vyberte **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Nastavení zarážky funkce pomocí adresy paměti (pouze nativní jazyk C++)
 Adresu objektu můžete použít k nastavení zarážky funkce na metodě volané určitou instancí třídy.  Například daný adresovatelný objekt `my_class`typu můžete nastavit zarážku funkce na metodu, `my_method` která instance volá.

1. Nastavte zarážku někde po instance třídy je vytvořena instance.

2. Vyhledejte adresu instance `0xcccccccc`(například).

3. Vyberte **ladit** > **novou zarážky zarážky zarážky zarážky** > **Function Breakpoint**nebo stiskněte **alt**+**F9** > **Ctrl**+**B**.

4. Přidejte do pole **Název funkce následující** a vyberte jazyk **C++.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Nastavení zarážek dat (jádra.net 3.0 nebo vyšší)

Zarážky dat zapuštnou spuštění při změně vlastnosti určitého objektu.

**Nastavení zarážky dat**

1. V projektu .NET Core spusťte ladění a počkejte, dokud není dosaženo zarážky.

2. V okně **Autos**, **Watch**nebo **Locals** klepněte pravým tlačítkem myši na vlastnost a při změně hodnoty v místní nabídce vyberte **Příkaz Přerušit.**

    ![Zarážka spravovaných dat](../debugger/media/managed-data-breakpoint.png "Zarážka spravovaných dat")

Zarážky dat v jádru .NET nebudou fungovat pro:

- Vlastnosti, které nelze rozbalit v okně s popisem Místní, Autos nebo Kukátko
- Statické proměnné
- Třídy s atributem DebuggerTypeProxy
- Pole uvnitř struktur

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Nastavení zarážek dat (pouze nativní jazyk C++)

 Zarážky dat zalomení spuštění při změně hodnoty uložené na zadané adrese paměti. Pokud je hodnota přečtena, ale není změněna, spuštění se nepřeruší.

**Nastavení zarážky dat:**

1. V projektu Jazyka C++ spusťte ladění a počkejte, dokud není dosaženo zarážky. V nabídce **Ladění** zvolte Nová zarážky dat **zarážky zarážky zarážky zarážky.** > **Data Breakpoint**

    Můžete také vybrat **novou** > **zarážky dat** v okně **Zarážky** nebo klepnout pravým tlačítkem myši na položku v okně **Autos**, **Watch**nebo **Locals** a vybrat **Přerušit, když se hodnota změní** v místní nabídce.

2. Do pole **Adresa** zadejte adresu paměti nebo výraz, který je vyhodnocen jako adresa paměti. Zadejte `&avar` například přerušení, když se `avar` změní obsah proměnné.

3. V rozevíracím souboru **Počet bajtů** vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4**, ladicí program bude sledovat `&avar` čtyři bajty začínající na a přerušit, pokud některý z těchto bajtů změnit hodnotu.

Zarážky dat nefungují za následujících podmínek:
- Proces, který není laděn zapisuje zápisy do umístění v paměti.
- Umístění paměti je sdíleno mezi dvěma nebo více procesy.
- Umístění paměti je aktualizováno v rámci jádra. Pokud je například paměť předána 32bitové funkci systému Windows, `ReadFile` bude paměť aktualizována z režimu jádra, takže ladicí program se při aktualizaci nepřeruší.
- Kde je výraz sledování větší než 4 bajty na 32bitovém hardwaru a 8 bajtů na 64bitovém hardwaru. Toto je omezení architektury x86.

> [!NOTE]
> - Zarážky dat závisí na konkrétní adresy paměti. Adresa proměnné se změní z jedné relace ladění na další, takže zarážky dat jsou automaticky zakázány na konci každé relace ladění.
>
> - Pokud nastavíte zarážky dat na místní proměnné, zarážka zůstane povolena, když funkce končí, ale adresa paměti již není použitelná, takže chování zarážky je nepředvídatelné. Pokud nastavíte zarážky dat na místní proměnné, měli byste odstranit nebo zakázat zarážku před ukončením funkce.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Správa zarážek v okně Zarážky

 Okno **Zarážky** můžete použít k zobrazení a správě všech zarážek v řešení. Toto centralizované umístění je užitečné zejména ve velkém řešení nebo pro složité scénáře ladění, kde jsou kritické zarážky.

V okně **Zarážky** můžete vyhledávat, řadit, filtrovat, povolit nebo zakázat nebo odstraňovat zarážky. Můžete také nastavit podmínky a akce nebo přidat novou funkci nebo zarážku dat.

Chcete-li otevřít okno **Zarážky,** vyberte **ladit** > **zarážky****systému Windows** > nebo stiskněte **klávesu Alt**+**F9** nebo **Ctrl**+**Alt**+**B**.

![Zarážky – okno](../debugger/media/breakpointswindow.png "Zarážky – okno")

Chcete-li vybrat sloupce, které se mají zobrazit v okně **Zarážky,** vyberte **zobrazit sloupce**. Vyberte záhlaví sloupce, chcete-li seznam zarážek seřadit podle tohoto sloupce.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Popisky zarážky
Popisky můžete použít k seřazení a filtrování seznamu zarážek v okně **Zarážky.**

1. Chcete-li k zarážky přidat popisek, klepněte pravým tlačítkem myši na zarážku ve zdrojovém kódu nebo v okně **Zarážky** a vyberte **příkaz Upravit popisky**. Přidejte nový popisek nebo zvolte existující popisek a pak vyberte **OK**.
2. Seřaďte seznam zarážek v okně **Zarážky** výběrem **záhlaví Popisky**, **Podmínky**nebo Jiných sloupců. Sloupce, které se mají zobrazit, můžete vybrat tak, že na panelu nástrojů vyberete **Zobrazit sloupce.**

### <a name="export-and-import-breakpoints"></a>Export a import zarážek
 Chcete-li uložit nebo sdílet stav a umístění zarážek, můžete je exportovat nebo importovat.

- Chcete-li exportovat jednu zarážku do souboru XML, klepněte pravým tlačítkem myši na zarážku ve zdrojovém kódu nebo okně **Zarážky** a vyberte **vybrat export** nebo **export .** Vyberte umístění exportu a pak vyberte **Uložit**. Výchozí umístění je složka řešení.
- Chcete-li exportovat několik zarážek, vyberte v okně **Zarážky** pole vedle zarážek nebo zadejte kritéria hledání do pole **Hledat.** Vyberte **možnost Exportovat všechny zarážky odpovídající aktuálnímu kritériu hledání** a soubor uložte.
- Chcete-li exportovat všechny zarážky, zrušte výběr všech polí a nechte pole **Hledat** prázdné. Vyberte **možnost Exportovat všechny zarážky odpovídající aktuálnímu kritériu hledání** a soubor uložte.
- Chcete-li importovat zarážky, vyberte v okně **Zarážky** **zarážky zarážky z ikony souboru,** přejděte do umístění souboru XML a vyberte **Otevřít**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Nastavení zarážek z oken ladicího programu

Můžete také nastavit zarážky z okna ladicího programu **zásobníku volání** a **demontáže.**

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Nastavení zarážky v okně Zásobník volání

 Chcete-li přerušit na instrukce nebo řádek, který volá funkce vrátí, můžete nastavit zarážku v okně **zásobníku volání.**

**Nastavení zarážky v okně Zásobník volání:**

1. Chcete-li otevřít okno **zásobníku volání,** musíte být během ladění pozastaven. Vyberte **možnost Ladění** > **zásobníku volání systému****Windows** > nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**C**.

2. V okně **Zásobník volání** klepněte pravým tlačítkem myši na volající funkci a vyberte **zarážku** > **Vložení zarážky**nebo stiskněte **klávesu F9**.

   Vedle názvu volání funkce v levém okraji zásobníku volání se zobrazí symbol zarážky.

Zarážky zásobníku volání se zobrazí v okně **Zarážky** jako adresa, s umístěním paměti, která odpovídá další spustitelné instrukce ve funkci.

Ladicí program se při instrukci přeruší.

Další informace o zásobníku volání najdete v [tématu Postup: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

Vizuálně trasovat zarážky během spuštění kódu, naleznete [v tématu Map metody v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně Demontáže

1. Chcete-li otevřít okno **Demontáže,** musíte být během ladění pozastaveni. Vyberte **možnost Ladění** > **demontáže****systému Windows** > nebo stiskněte **klávesu Alt**+**8**.

2. V okně **Demontáž** klepněte na levý okraj instrukce, kterou chcete přerušit. Můžete ji také vybrat a stisknout **klávesu F9**nebo klepnout pravým tlačítkem myši a vybrat**zarážku** **Breakpoint** > vložení .

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Napsat lepší kód Jazyka C# pomocí sady Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Poradce při potížích s zarážkymi v ladicím programu sady Visual Studio](../debugger/troubleshooting-breakpoints.md)
