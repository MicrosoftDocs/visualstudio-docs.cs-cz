---
title: Řízení spouštění aplikace pro Store v ladicí relace pro aplikace Windows Store (JavaScript) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca8e2a584ff68786d22bd90ddd8827a70c66a557
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052213"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Řízení spouštění aplikace pro Store v ladicí relaci sady Visual Studio pro aplikace Windows Store (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento rychlý start ukazuje, jak pro navigaci v ladicím programu sady Visual Studio a jak zobrazit stav programu v relaci.

 Tento rychlý start je pro vývojáře, kteří jsou nové pro ladění v sadě Visual Studio a pro vývojáře, kteří chtějí získat další informace o navigaci v sadě Visual Studio relace ladění. To se nezabývá techniky ladění samotný. Funkce ve vzorovém kódu slouží pouze k předvedení ladění postupů popsaných v tomto tématu. Funkce není dodržovat doporučené postupy návrhu aplikace nebo funkce. Ve skutečnosti rychle zjistíte, že funkce a aplikace, není vhodné použít co nejvíce všeho vůbec.

 Části tohoto rychlého startu byly navržené jako jako nezávislé, jako je to možné, takže můžete přeskočit všechny části, která obsahuje informace, které jste už obeznámení s. Také není nutné k vytvoření ukázkové aplikace. Ale doporučujeme ho a provedli proces co nejjednodušší.

 **Ladicí program klávesové zkratky.** Navigace v ladicím programu sady Visual Studio je optimalizovaná pro myš a klávesnici. Celá řada kroků v tomto tématu patří klávesové zkratky nebo klávesovou zkratku v kulatých závorek příspěvku. Například (klávesnice: F5) označuje zadáním klávesu F5, spustí nebo pokračuje v provádění ladicího programu.

> [!NOTE]
>  **Vzor modulu**
>
>  Aplikace Windows Store často používají jazyk JavaScript *modulu vzor* k zapouzdření data a funkce na stránce. Vzor modul používá jeden, samostatně prováděného a anonymní uzavření udržovat odděleně od globální obor názvů funkce stránky. V tomto tématu se budeme volat tuto funkci *modulu*.

## <a name="in-this-topic"></a>V tomto tématu
 Můžete získat informace tom, jak:

 [Vytvoření ukázkové aplikace](#BKMK_Create_the_sample_app)

 [Nastavit a spusťte zarážku, krokování s vnořením do funkce a prozkoumejte data programu](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [Krokovat do, nad a z funkce](#BKMK_Step_into__over__and_out_of_functions)

 [Nastavení podmíněné zarážky, přechod ke kurzoru a vizualizovat proměnné](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Zobrazení dat proměnných v okně místních hodnot](#BKMK_View_variable_data_in_the_Locals_window)

- [Zobrazit data proměnných a řetězec prototypu objektu](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Prozkoumejte data řetězce oboru](#BKMK_Examine_scope_chain_data)

  [Přejít ke kódu pomocí okna zásobník volání](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

##  <a name="BKMK_Create_the_sample_app"></a> Vytvoření ukázkové aplikace
 Ladění je kód, takže ukázková aplikace používá rozhraní framework aplikace Windows Store pouze k vytvoření zdrojového souboru, ve kterém uvidíte fungování navigace ladicí relaci a tom, jak zkontrolovat stav programu. Veškerý kód, který bude volat funkce je volána z `module` funkce soubor default.js. Žádné ovládací prvky jsou přidány a jsou zpracovány žádné události.

1. **Vytvořte prázdnou aplikaci pro Windows Store jazyka JavaScript.** Otevřít Visual Studio. Na domovské stránce, zvolte **nový projekt** odkaz. Na **nový projekt** dialogového okna zvolte **JavaScript** v **nainstalováno** seznamu a klikněte na tlačítko **Windows Store**. V seznamu šablon projektu vyberte **prázdná aplikace**. Visual Studio vytvoří nová řešení a projektu a zobrazí souboru default.htm v editoru kódu.

    Mějte na paměti, která jsou načtena do stránky soubory skriptů.

   -   `base.js` a `ui.js` vytvoření souborů **knihovnu Windows pro jazyk JavaScript**. Knihovna Windows pro jazyk JavaScript je sada JavaScript a soubory šablon stylů CSS, které usnadňují vytváření aplikací pro Windows Store pomocí jazyka JavaScript. Použijete ho spolu s HTML, CSS a prostředí Windows Runtime k vytvoření vaší aplikace.

   -   Váš kód se spustí v `default.js` souboru.

2. **Otevřete zdrojový soubor default.js.** V Průzkumníku řešení otevřete **js** uzlu a zvolte `default.js`.

3. **Nahraďte obsah stránky se vzorovým kódem.** Odstranit veškerý obsah z `default.js` souboru. Na tomto odkazu: [ladicího programu vzorový kód pro navigaci (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md)a potom zkopírujte kód uvedený v části jazyka JavaScript do schránky. (Zvolte **zpět** v prohlížeči nebo prohlížeč nápovědy se vraťte na tuto stránku rychlý start.) V editoru sady Visual Studio, vložte kód do prázdné nyní `default.js`. Zvolte **Ctrl + S** k uložení souboru.

   Teď můžete sledovat, spolu s příklady v tomto tématu.

##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Nastavit a spusťte zarážku, krokování s vnořením do funkce a prozkoumejte data programu
 Nejběžnější způsob spuštění ladicí relace je zvolit **spustit ladění** z **ladění** nabídce (klávesnice: F5). Aplikace spustí a pokračuje v provádění, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce nebo ukončení aplikace.

 Když je spuštění pozastaveno v ladicím programu, můžete zobrazit hodnotu active proměnné v popisu dat. když pozastavíte myší na proměnnou.

 Po pozastavení provádění aplikace (označuje se také rozdělení do ladicího programu), řídit způsob, jakým spouští zbývající části kódu programu. Můžete dál řádek po řádku přesouvá z volání funkce do funkce samotná, nebo volané funkce lze provést v jediném kroku. Tyto postupy jsou volány krokování aplikace. Můžete také obnovit standardní provádění, spuštěnou aplikaci až k další zarážce, kterou jste nastavili, nebo na řádku tam, kam jste umístili kurzor. Můžete zastavit ladicí relaci v každém okamžiku. Ladicí program je určena k provedení nezbytných operací čištění a ukončí provádění.

###  <a name="BKMK_Example_1"></a> Příklad 1
 V tomto příkladu nastavte zarážku v těle `module` fungovat v `default.js` volá první příkazy našich uživatelů. Poté krokovat s vnořením funkci, zobrazení hodnot proměnných v datových tipech ladicího programu a poté zastavte ladění.

1. **Nastavte zarážku.** Nastavit zarážku na příkaz `callTrack = "module function";` , který vyvolá hned po volání `app.start()`. Zvolte řádek na vystínovanou ovládací prvek editoru zdrojového kódu (klávesnice: Umístěte kurzor na řádek a zvolte **F9** klíč).

    ![Nastavit zarážku na test1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Ikona zarážky se zobrazí ve hřbetu.

2. **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5).

    Aplikace začne spouštět a pozastaví provádění bezprostředně před příkaz, ve kterém můžete nastavit zarážku. Aktuální ikona řádku na ovládací prvek určuje umístění a aktuální příkaz je zvýrazněn.

    ![Spusťte zarážku](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Nyní jsou v řízení spouštění aplikace a můžete zkontrolovat stav programu krocích příkazy programu.

3. **Krokovat s vnořením funkcí.** Na **ladění** nabídce zvolte **Krokovat s vnořením** (klávesnice: **F11**).

    ![Krokování s vnořením do řádku kódu](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Všimněte si, že ladicí program se přesune na další řádek, který je volání `example1` funkce. Zvolte **Krokovat s vnořením** znovu. Ladicí program se přesune na první řádek kódu `example1` funkce. Zvýrazněný řádek nebyl proveden, ale načetl funkci v zásobníku volání a byla přidělena paměť pro lokální proměnné.

4. Když vejdete do jediného řádku kódu provede ladicí program jednu z následujících akcí:

   - Pokud další příkaz není voláním funkce ve vašem řešení, ladicí program provede příkaz, přesune na další příkaz a následně pozastaví provádění kódu.

   - Pokud je příkaz voláním funkce ve vašem řešení, ladicí program se přesune na první řádek volané funkce a následně pozastaví provádění kódu.

     Nadále můžete krokovat s vnořením opustí `example1` dokud jste dosáhli výstupním bodě. Ladicí program zvýrazní uzavírací složenou závorku funkce.

5. **Zobrazení hodnot proměnných v datových tipech.** Nadále můžete krokovat s vnořením opustí `example1` dokud jste dosáhli výstupním bodě. Ladicí program zvýrazní uzavírací složenou závorku funkce. Při pozastavení myši na název proměnné, zobrazí se název a hodnotu proměnné v popisu dat.

    ![Zobrazení hodnot proměnných v popisu dat](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **Přidáte kukátko callTrack proměnné.** `callTrack` k zobrazit funkce volané v příkladech se používá v rámci tohoto rychlého startu proměnná. Aby bylo snazší zobrazit hodnotu proměnné, přidejte ho do okna kukátka. Vyberte název proměnné v editoru a klikněte na tlačítko **Přidat kukátko** z místní nabídky.

    ![Podívejte se na proměnnou](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Podívejte se na více proměnných v okně kukátko. Hodnoty proměnných sledovaných, jako je hodnot v oknech tip dat, se aktualizují pokaždé, když je spuštění pozastaveno. Sledované proměnné jsou uloženy napříč relacemi ladění.

7. **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: **Shift + F5**). Ukončí relaci ladění.

##  <a name="BKMK_Step_into__over__and_out_of_functions"></a> Krokovat do, nad a z funkce
 Na rozdíl od krokování s vnořením do funkcí volaných funkcí nadřazené, krokování přes funkci provede podřízené funkce a následně pozastaví provádění kódu ve funkci volání jako obnoví nadřazený. Pokud jste obeznámeni s způsob, jak funkce funguje a si jisti, že jeho spuštění nebude mít vliv na problém, který se objeví prošetřovaná může Krokovat přes funkci.

 Krokování přes jediného řádku kódu, které nebude obsahovat volání funkce spustí řádku stejně jako krokování s vnořením do řádku.

 Krokování ve funkci podřízené pokračuje v provádění funkce a následně pozastaví provádění po vrácení funkce k její volání funkce. Až zjistíte, že zbytek funkce není důležité, může být vystoupení ze dlouhé funkce.

 Krokování přes i krokování ve funkci spuštění funkce.

 ![Krok do, nad a z metody](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

###  <a name="BKMK_Example_2"></a> Příklad 2
 V tomto příkladu můžete krokovat do, nad a z funkce.

1.  **Volání funkce priklad2 ve funkci modulu.** Upravit `module` fungovat a nahraďte tento řádek `var callTrack = "module function"` s `example2();`.

     ![Volání funkce priklad2](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2.  **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5). Ladicí program pozastaví provádění kódu na zarážce.

3.  **Krokovat přes řádek kódu.** Na **ladění** nabídce zvolte **Krokovat s přeskočením** (klávesnice: F10). Ladicí program provede `var callTrack = "module function"` příkaz stejným způsobem jako vstup do příkazu.

4.  **Krokovat s vnořením priklad2 a example2_a.** Zvolte **F11** klíče krokování s vnořením `example2` funkce. Dál můžete krokovat s vnořením `example2` příkazů, dokud se nedostanete na řádku `var x = example2_a();`. Znovu, Krokovat s vnořením tento řádek, přejděte na vstupní bod `example2_a`. Dál můžete krokovat s vnořením každý příkaz `example2_a` postupně se vraťte do `example2`.

     ![Krok přes funkci](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5.  **Krokovat přes funkci.** Všimněte si, že se na další řádek v `example2`, `var y = example2_a();` je v podstatě stejný jako předchozí řádek. Můžete bezpečně Krokovat přes tento řádek. Zvolte **F10** klíč k přesunutí z opětovné `example2` do této druhé volání `example2_a`. Všimněte si, že `callTrack` řetězec označuje `example2_a` funkce byla spuštěna dvakrát.

6.  **Krok z funkce.** Zvolte **F11** klíče krokování s vnořením `example2_b` funkce. Všimněte si, že `example2_b` není příliš neliší od `example2_a`. Chcete-li mimo funkci, zvolte **Krokovat s Vystoupením** na **ladění** nabídce (klávesnice: **Shift + F11**). Všimněte si, že `callTrack` proměnné označuje, že `example2_b` se provedl a, který ladicí program vrátil do bodu kde `example2` obnoví.

7.  **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: **Shift + F5**). Ukončí relaci ladění.

##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Nastavení podmíněné zarážky, přechod ke kurzoru a vizualizovat proměnné
 Podmíněné zarážky Určuje podmínku, která způsobí, že ladicí program k pozastavení provádění. Podmínka je zadaný libovolný výraz kód, který může být vyhodnocen jako true nebo false. Můžete například použít podmíněné zarážky prozkoumat stav programu v často volaných funkcí pouze v případě, že proměnné dosáhne určité hodnoty.

 Provést do pozice kurzoru je třeba nastavit jednorázové zarážku. Když je spuštění pozastaveno, můžete vybrat řádek ve zdroji a obnovit spuštění, dokud nebude dosaženo vybraný řádek. Například je může krokování smyčku ve funkci a určit, že kód ve smyčce pracuje správně. Místo procházení každé iteraci smyčky, můžete spustit na kurzor, který je umístěn po provedení smyčky je.

 V některých případech je zobrazíte hodnotu proměnné v řádku popisu dat nebo jiné okno data obtížná. Ladicí program může zobrazit řetězce, HTML a Xml ve vizualizéru text, který představuje formátovaný zobrazení hodnoty v posuvného okna.

###  <a name="BKMK_Example_3"></a> Příklad 3
 V tomto příkladu je nastavit podmíněné zarážky zarážku konkrétní iteraci smyčky a pak spustit na kurzor, který je umístěn po smyčce. Můžete také zobrazit hodnotu proměnné v vizualizátor textu.

1.  **Volání funkce example3 ve funkci modulu.** Upravit `module` fungovat a nahraďte tento řádek `var callTrack = "module function";` řádek `example3();`.

     ![Volání example3](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2.  **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: **F5**). Ladicí program pozastaví provádění kódu na zarážce v `module` funkce.

3.  **Krokovat s vnořením example3 funkce.** Zvolte **Krokovat s vnořením** na **ladění** nabídce (klávesnice: **F11**) přesunout do vstupní bod `example3` funkce. Pokračovat, dokud máte provést iteraci smyčky jednu nebo dvě z krokování do funkce `for` bloku. Všimněte si, že ho by vám neměl zabrat dlouhou dobu, chcete-li si všechny 1000 iterací.

4.  **Nastavení podmíněné zarážky.** V levém hřbetu okna kódu, klikněte pravým tlačítkem na řádku `s += i.toString() + "\n";` a klikněte na tlačítko **podmínku** v místní nabídce.

     Vyberte **podmínku** zaškrtněte políčko a potom zadejte `i == 500;` v textovém poli. Zvolte **platí** možnost a vyberte **OK**. Zarážky můžete ke kontrole hodnoty v 500th iterace `for` smyčky. Ikona podmíněné zarážky může identifikovat podle jeho bílé mezi.

     ![Ikona zarážky podmíněný](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5.  **Spusťte zarážku.** Na **ladění** nabídce zvolte **pokračovat** (klávesnice: **F5**). Zastavte se na `i` potvrdit, že aktuální hodnotu `i` je 500. Všimněte si také, že proměnná `s` je vyjádřena jako jeden řádek a je mnohem delší než okno tipů data.

6.  **Vizualizujte proměnnou s řetězcem.** Klikněte na ikonu lupy v popisu dat z `s`.

     Zobrazí se okno Vizualizátor textu a hodnotou řetězce je zobrazen jako Víceřádkový řetězec.

     ![Ladění vizualizátor textu](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7.  **Přechod ke kurzoru.** Vyberte řádek `callTrack += "->example3";` a klikněte na tlačítko **spustit ke kurzoru** v místní nabídce (klávesnice: **Ctrl + F10**). Ladicí program dokončí iterací smyčky a následně pozastaví provádění kódu na řádku.

8.  **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: **Shift + F5**). Ukončí relaci ladění.

###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Použití spustit ke kurzoru se vraťte do vašeho kódu a odstranění zarážky
 Provést do pozice kurzoru může být velmi užitečné, když jste vkročili knihovny kódu od společnosti Microsoft nebo třetích stran. Krokování kódem knihovny mohou být informativní, často může trvat dlouhou dobu. A obvykle jsou mnohem více zajímá váš vlastní kód. V tomto cvičení se dozvíte, jak na to.

1.  **Nastavení zarážky na volání app.start.** V `module` fungovat, nastavte zarážku na řádku `app.start()`

2.  **Spusťte zarážku a můžete krokovat s vnořením funkce knihovny.**

     Při krokování s vnořením `app.start()`, zobrazuje kód v editoru `base.js`. Krokovat s vnořením několik více řádků.

3.  **Krok nad a z funkcí.** Jak Krokovat přes (**F10**) a krok z celkového počtu (**SHIFT + F11**) kódu v `base.js`, může dojít k závěru zkoumání složitost a délka – spuštění funkce je, co nechcete dělat.

4.  **Nastavte kurzor do vašeho kódu a spustit na ni.** Přepněte zpět `default.js` souboru v editoru kódu. Vyberte první řádek kódu po `app.start()` (nemůžete spustit na komentář nebo na prázdný řádek). Zvolte **spustit ke kurzoru** z místní nabídky. Ladicí program pokračuje v provádění funkce app.start a pozastaví provádění kódu na zarážce.

##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Zobrazení dat proměnných v okně místních hodnot
 Lokální windows je stromové zobrazení parametry a proměnné v oboru řetězci aktuálně prováděné funkci.

###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Zobrazit data proměnných a řetězec prototypu objektu

1.  **Přidání pole objektu funkce modulu.** Upravit `module` fungovat a nahraďte tento řádek `var callTrack = "module function"` s `var myArray = new Array(1, 2, 3);`

     ![definice pole](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2.  **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: **F5**). Ladicí program pozastaví provádění kódu na zarážce. Krokovat s vnořením do řádku.

3.  **Otevřete v okně místních hodnot.** Na **ladění** nabídky, přejděte k **Windows**a klikněte na tlačítko **lokální**. (Klávesnice: Alt + 4).

4.  **Zkontrolujte místní proměnné ve funkci modulu** The lokální systém windows zobrazí proměnné aktuálně prováděné funkci ( `module` funkce) jako na nejvyšší úrovni uzly stromu. Při zadání funkce jazyka JavaScript vytvoří všechny proměnné a poskytne jim hodnotu `undefined`. Funkce, které jsou definovány ve funkci mají jejich text jako hodnotu.

     ![Okno místních hodnot](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5.  **Projděte skrze definice callTrack a pole.** Najdete callTrack a pole proměnných v okně místních hodnot. Krokovat přes (**F10**) dvě definice a Všimněte si, že **hodnotu** a **typ** pole se změní. V okně místních hodnot zvýrazní hodnoty proměnných, které se změnily od posledního pozastavení.

6.  **Zkontrolujte pole objektu** Rozbalit `myArray` proměnné. Každý prvek pole je uveden **[prototypu]** uzel, který obsahuje hierarchii dědičnosti `Array` objektu. Rozbalte tento uzel.

     ![Řetězec prototypu v okně místních hodnot](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    -   **Metody** uzel obsahuje všechny metody `Array` objektu.

    -   **[Prototypu]** uzel obsahuje prototyp funkce `Object` objekt, ze kterého `Array` pochází. **[prototypu]**  uzly mohou být rekurzivní. Každý nadřazený objekt v hierarchii objektů je popsána v **[prototypu]** jeho podřízeného uzlu.

7.  **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: Shift + F5). Ukončí relaci ladění.

##  <a name="BKMK_Examine_scope_chain_data"></a> Prozkoumejte data řetězce oboru
 *Oboru řetězu* funkce zahrnuje všechny proměnné, které jsou aktivní a je dostupný prostřednictvím funkce. Globální proměnné jsou součástí řetězce rozsahu, jako jsou objekty (včetně funkcí), která jsou definována ve funkci, která definuje aktuálně prováděné funkci. Například `callTrack` proměnné, která je definována v `module` funkce `default.js` je dostupná pro všechny funkce, které je definováno v `module` funkce. Každý obor zobrazeny v okně místních hodnot.

- Proměnné aktuálně prováděné funkce jsou zobrazeny v horní části okna.

- Proměnné každý obor funkce v řetězci rozsahu patří **[oboru]** uzlu funkce. Obor funkcí jsou seřazeny podle jejich pořadí v řetězu certifikátů z funkce, která definuje aktuální funkci k nejzevnější funkce řetězce.

- **[Globální parametry]** uzel uvádí globální objekty, které jsou definovány mimo všechny funkce.

  Obor řetězce může být matoucí a jsou znázorněny nejlépe podle příkladu. V následujícím příkladu je vidět způsob, jakým `module` funkce vytvoří vlastní rozsah a jak můžete vytvořit další úrovně oboru tak, že vytvoříte uzavřenou.

###  <a name="BKMK_Example_4"></a> Příklad 4:

1.  **Volání funkce example4 z funkce modulu.** Upravit `module` fungovat a nahraďte tento řádek `var callTrack = "module function"` s `example4()`:

     ![Volání example4](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2.  **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: **F5**). Ladicí program pozastaví provádění kódu na zarážce.

3.  **Otevřete v okně místních hodnot.** V případě potřeby na **ladění** nabídky, přejděte k **Windows**a klikněte na tlačítko **lokální**. (Klávesnice: **Alt + 4**). Všimněte si, že v okně zobrazí seznam všech proměnných a funkcí v `module` fungovat a obsahuje také **[globální parametry]** uzlu.

4.  **Prozkoumejte globální proměnné.** Rozbalte **[globální parametry]** uzlu. Objekty a proměnné v globální byly nastavené zásadami knihovny Windows pro jazyk JavaScript. Přidejte vlastní proměnné pro globální obor.

5.  **Krokovat s vnořením example4 a zkontrolujte jeho místní a obor proměnné** Krokovat s vnořením (klávesnice: **F11**) `example4` funkce. Protože `example4` je definována v `module` funkce, `module` funkce stane nadřazený obor. `example4` můžete volat jakékoli funkce v `module` fungovat a přístup ke své proměnné. Rozbalte **[oboru]** uzel v okně místních hodnot a Všimněte si, že obsahuje stejné a proměnné `module` funkce.

     ![Obory metody example4](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6.  **Krokovat s vnořením example4_a a zkontrolujte jeho místní a obor proměnné** i nadále můžete krokovat s vnořením `example4` a do volání `example4_a`. Všimněte si, že místní proměnné se teď z `example4_a`a že **[oboru]** uzel pokračuje k uložení proměnné `module` funkce. I když proměnné `example4` jsou aktivní, nesmí být dosažitelný podle `example4_a` a nadále již nebudou součástí řetězce oboru.

7.  **Krokovat s vnořením multipyByA a zkontrolujte jeho místní a obor proměnné** projít zbývající část `example4_a` a do řádku `var x = multilpyByA(b);`.

     Proměnnou funkce `multipyByA` byla nastavena `multiplyClosure` funkce, která je *uzavření*. `multipyClosure` definuje a vrátí vnitřní funkce `mulitplyXby`a zachytí (zavře přes) proměnné a parametru. Vrácené vnitřní funkce v uzávěru, má přístup k datům vnější funkce a proto vytvoří vlastní úroveň oboru.

     Při krokování s vnořením `var x = multilpyByA(b);`, přejdete `return a * b;` řádku v `mulitplyXby` vnitřní funkce.

8.  V okně místních hodnot, pouze parametr `b` je uveden jako místní proměnné v `multiplyXby`, ale nové **[oboru]** úroveň se přidala. Rozbalením tohoto uzlu, uvidíte, že obsahuje parametry, funkce a proměnné `multiplyClosure`, včetně `a` proměnná volána v prvním řádku `multiplyXby`. Rychlá kontrola druhého **[oboru]** uzel ukáže proměnné funkce modulu, který `multiplyXby` přistupuje k jeho dalším řádku.

     ![Obory uzavření v okně místních hodnot](../debugger/media/dbg-jsnav-scope-mulitplyxby.png "DBG_JSNAV_scope_mulitplyXby")

9. **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: **Shift + F5**). Ukončí relaci ladění.

##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Přejít ke kódu pomocí okna zásobník volání
 Zásobník volání je datová struktura, která obsahuje informace o funkcích, které jsou spuštěny v aktuálním vlákně aplikace. Při dosažení zarážky v okně zásobník volání zobrazí seznam všech funkcí, které jsou aktivní v zásobníku. Aktuálně prováděné funkce je v horní části seznamu okna zásobník volání. Funkce, která inicializuje vlákno je v dolní části seznamu. Funkce mezi zobrazit cestu volání z inicializační funkce na aktuální funkci.

 Kromě zobrazení volání cestu k aktuálně prováděné funkci, v okně zásobník volání je možné přejít ke kódu v editoru kódu. Tato funkce může být důležité, když pracujete s více soubory a chcete rychle přesunout do konkrétní funkce.

###  <a name="BKMK_Example_5"></a> Příklad 5
 V tomto příkladu můžete krokovat s vnořením volání cestu, která obsahuje pět uživatelem definované funkce.

1.  **Volání funkce example5 ve funkci modulu.** Upravit `module` fungovat a nahraďte tento řádek `var callTrack = "module function";` řádek `example5();`.

     ![Volání example5](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2.  **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: **F5**). Ladicí program pozastaví provádění na zarážku ve funkci modulu.

3.  **Otevření okna zásobník volání.** Na **ladění** nabídce zvolte **Windows**a klikněte na tlačítko **zásobník volání** (klávesnice: Alt + 7). Všimněte si, že v okně zásobník volání se zobrazí dvě funkce:

    -   **Globální kódu** je vstupním bodem `module` funkce v dolní části zásobníku volání.

    -   **Anonymní funkce** ukazuje na řádku `module` funkce, kde je spuštění pozastaveno. Toto je začátek zásobníku volání.

4.  **Krokovat s vnořením funkce k dosažení example5_d funkce.** Zvolte **Krokovat s vnořením** na **ladění** nabídce (klávesnice: **F11**) k provedení volání v cestě k volání, dokud se nedostanete vstupní bod funkce example5_d. Všimněte si, že pokaždé, když, že funkce volá funkci, číslo řádku volání funkce se uloží a volaná funkce je umístěn v horní části zásobníku. Číslo řádku volání funkce je bod, ve kterém byla pozastavena volání funkce spuštění. Žlutá šipka odkazuje na aktuálně prováděné funkci.

     ![Okno zásobník volání](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5.  **Použití okna zásobník volání pro přechod na kód example5_a a nastavte zarážku.** V okně zásobník volání, vyberte `example5_a` položky seznamu a klikněte na tlačítko **přejděte ke zdroji** v místní nabídce. Editor kódu nastaví jeho kurzoru do řádku vrácení funkce. Nastavte zarážku na tomto řádku. Všimněte si, že aktuální řádek provádění se nemění. Má přesunout kurzor editoru.

6.  **Krokovat s vnořením funkce a spusťte zarážku.** Pokračujte v krokování s vnořením do `example5_d`. Všimněte si, že při návratu z funkce se odebírá ze zásobníku volání. Stisknutím klávesy **F5** pro pokračování ve spouštění programu. Zastavení na zarážce vytvořili v předchozím kroku.

7.  **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: **Shift + F5**). Ukončí relaci ladění.

## <a name="see-also"></a>Viz také
 [Spuštění ladicí relace (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [rychlý start: ladicí program navigace (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md) [aktivační události pozastavení, obnovení a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
