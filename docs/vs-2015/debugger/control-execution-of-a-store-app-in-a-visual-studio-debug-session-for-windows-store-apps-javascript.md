---
title: Řízení spouštění aplikace pro Store v relaci ladění pro aplikace pro Windows Store (JavaScript) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9238bd4f42291af23a1279c9caa83f1039c8f249
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828619"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Řízení spouštění aplikace pro Store v ladicí relaci sady Visual Studio pro aplikace pro Windows Store (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento rychlý Start ukazuje, jak navigovat v ladicím programu sady Visual Studio a jak zobrazit stav programu v relaci.

 Tento rychlý Start je určen vývojářům, kteří jsou novinkou k ladění pomocí sady Visual Studio a pro vývojáře, kteří se chtějí dozvědět více o navigaci v ladicí relaci sady Visual Studio. Neučí grafiku samotného ladění. Funkce v ukázkovém kódu jsou určeny pouze k předvedení postupů ladění popsaných v tomto tématu. Funkce nevyužívají osvědčené postupy pro aplikace nebo návrh funkcí. Ve skutečnosti rychle zjistíte, že funkce a samotná aplikace nedělají všechno vůbec.

 Části tohoto rychlého startu byly navržené tak, aby byly co nezávisle, takže můžete přeskočit všechny části, které obsahují informace, se kterými už jste obeznámeni. Nemusíte také vytvářet ukázkovou aplikaci. Doporučujeme ho ale doporučit a co nejjednodušší je udělat.

 **Klávesové zkratky pro ladicí program.** Navigace v ladicím programu sady Visual Studio je optimalizovaná pro myš i klávesnici. Mnohé z kroků v tomto tématu zahrnují klávesovou zkratku nebo klávesovou zkratku v případě přeznačení kulatého kulatého závorky. Například (klávesnice: F5) označuje, že psaní klávesy F5 se spustí nebo pokračuje v provádění ladicího programu.

> [!NOTE]
> **Vzor modulu**
>
> Aplikace pro Windows Store často používají *model modulu* JavaScript k zapouzdření dat a funkcí na stránce. Vzor modulu používá jedno, samostatně vykonávajícího a anonymního uzavření, aby funkce stránky byly oddělené od globálního oboru názvů. V tomto tématu budeme volat tuto funkci *modulu*.

## <a name="in-this-topic"></a>V tomto tématu
 Můžete se dozvědět, jak:

 [Vytvoření ukázkové aplikace](#BKMK_Create_the_sample_app)

 [Nastavení a spuštění na zarážku, krok do funkce a kontrola dat programu](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [Krokovat s vnořením funkcí](#BKMK_Step_into__over__and_out_of_functions)

 [Nastavte podmíněnou zarážku, spusťte ji na kurzor a vizualizujte proměnnou.](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Zobrazení dat proměnných v okně místních hodnot](#BKMK_View_variable_data_in_the_Locals_window)

- [Zobrazení dat proměnných a řetězce prototypu objektu](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Prověřte data řetězu oboru](#BKMK_Examine_scope_chain_data)

  [Přechod na kód pomocí okna zásobník volání](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

## <a name="create-the-sample-app"></a><a name="BKMK_Create_the_sample_app"></a> Vytvoření ukázkové aplikace
 Ladění je o kódu, takže ukázková aplikace používá architekturu aplikace pro Windows Store pouze k vytvoření zdrojového souboru, ve kterém vidíte, jak navigace ladicí relace funguje a jak kontrolovat stav programu. Veškerý kód, který budete volat, je volán z `module` funkce default.js souboru. Nepřidaly se žádné ovládací prvky a nezpracovávají se žádné události.

1. **Vytvoření prázdné aplikace pro Windows Store v JavaScriptu** Otevřete sadu Visual Studio. Na domovské stránce klikněte na odkaz **Nový projekt** . V dialogovém okně **Nový projekt** zvolte v seznamu **nainstalované** možnost **JavaScript** a pak zvolte **Windows Store**. V seznamu šablon projektu vyberte možnost **prázdná aplikace**. Visual Studio vytvoří nové řešení a projekt a zobrazí soubor default.htm v editoru kódu.

    Poznamenejte si soubory skriptu, které jsou načteny na stránku.

   - `base.js`Soubory a `ui.js` vytvoří **knihovnu Windows Library pro JavaScript**. Knihovna Windows pro jazyk JavaScript je sada souborů JavaScript a CSS, které usnadňují vytváření aplikací pro Windows Store pomocí jazyka JavaScript. Můžete ji použít společně s HTML, CSS a prostředí Windows Runtime k vytvoření aplikace.

   - Kód začíná v `default.js`  souboru.

2. **Otevřete zdrojový soubor default.js.** V Průzkumník řešení otevřete uzel **js** a vyberte `default.js` .

3. **Nahraďte obsah stránky ukázkovým kódem.** Odstraní ze souboru veškerý obsah `default.js` . Použijte tento odkaz: [ladicí program pro navigaci v ladicím programu (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md)a potom zkopírujte kód uvedený v oddílu JavaScript do schránky. (Kliknutím na tlačítko **zpět** v prohlížeči nebo v prohlížeči nápovědy se vraťte na tuto stránku rychlý Start.) V editoru sady Visual Studio vložte kód do pole nyní prázdné `default.js` . Klikněte na tlačítko **CTRL + S** a soubor uložte.

   Teď můžete postupovat podle příkladů v tomto tématu.

## <a name="set-and-run-to-a-breakpoint-step-into-a-function-and-examine-program-data"></a><a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Nastavení a spuštění na zarážku, krok do funkce a kontrola dat programu
 Nejběžnější způsob, jak spustit relaci ladění, je zvolit možnost **Spustit ladění** z nabídky **ladění** (klávesnice: F5). Aplikace se spustí a pokračuje, dokud není dosaženo zarážky, dojde k ručnímu pozastavení provádění, dojde k výjimce nebo skončí aplikace.

 Pokud je spuštění pozastaveno v ladicím programu, můžete zobrazit hodnotu aktivní proměnné v datovém tipu pozastavením myši na proměnné.

 Po pozastavení provádění aplikace (která se také označuje jako rozdělení do ladicího programu) můžete řídit způsob, jakým se spustí zbytek programového kódu. Můžete pokračovat řádek po řádku, přesunutím z volání funkce do samotné funkce nebo můžete spustit volanou funkci v jednom kroku. Tyto postupy se nazývají krokování aplikace. Můžete také obnovit standardní spuštění aplikace, spuštění na další zarážku, kterou jste nastavili, nebo na řádek, na který jste umístili kurzor. Ladicí relaci můžete kdykoli zastavit. Ladicí program je navržen tak, aby prováděl nezbytné operace vyčištění a ukončila provádění.

### <a name="example-1"></a><a name="BKMK_Example_1"></a> Příklad 1
 V tomto příkladu nastavíte zarážku v těle `module` funkce v `default.js` , protože volá první z našich uživatelských příkazů. Pak se můžete krokovat s vnořením do funkce, zobrazit hodnoty proměnných v tipech pro data ladicího programu a pak zastavit ladění.

1. **Nastavte zarážku.** Nastavte zarážku na příkaz `callTrack = "module function";` , který se nachází hned po volání `app.start()` . Vyberte čáru ve stínovém rámečku editoru zdrojového kódu (klávesnice: Umístěte kurzor na řádek a vyberte klávesu **F9** ).

    ![Nastavení zarážky v priklad1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Ikona zarážky se zobrazí na hřbetu.

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5).

    Aplikace začne provádět a pozastaví provádění přímo před příkazem, na kterém jste nastavili zarážku. Ikona aktuálního řádku na hřbetu označuje vaše umístění a zvýrazní se aktuální příkaz.

    ![Spustit na zarážku](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Nyní máte kontrolu nad prováděním aplikace a můžete zkontrolovat stav programu při procházení příkazů programu.

3. **Krok do funkce.** V nabídce **ladění** vyberte možnost **Krokovat** s vnořením (klávesnice: **F11**).

    ![Krokovat na řádek kódu](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Všimněte si, že ladicí program se přesune na další řádek, který je voláním `example1` funkce. Vyberte znovu **Krok** . Ladicí program se přesune na první řádek kódu `example1` funkce. Zvýrazněný řádek nebyl proveden, ale funkce byla načtena do zásobníku volání a byla přidělena paměť pro lokální proměnné.

4. Při kroku na řádek kódu provede ladicí program jednu z následujících akcí:

   - Pokud další příkaz není voláním funkce ve vašem řešení, ladicí program provede příkaz, přesune se k dalšímu příkazu a pak pozastaví provádění.

   - Pokud je příkaz volání funkce ve vašem řešení, ladicí program se přesune na první řádek volané funkce a pak pozastaví provádění.

     Pokračujte krokem do příkazů, `example1` dokud nedosáhnete bodu ukončení. Ladicí program zvýrazní pravou složenou závorku funkce.

5. **Zobrazit hodnoty proměnných v tipech k datům.** Pokračujte krokem do příkazů, `example1` dokud nedosáhnete bodu ukončení. Ladicí program zvýrazní pravou složenou závorku funkce. Když pozastavíte myš na název proměnné, zobrazí se název a hodnota proměnné v popisku dat.

    ![Zobrazit hodnoty proměnných v popisku dat](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **Přidejte kukátko pro proměnnou callTrack.** `callTrack`Proměnná se používá v rámci tohoto rychlého startu k zobrazení funkcí volaných v příkladech. Chcete-li usnadnit zobrazení hodnoty proměnné, přidejte ji do okno Kukátko. Vyberte název proměnné v editoru a pak zvolte **Přidat kukátko** z místní nabídky.

    ![Sledovat proměnnou](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    V okně kukátka můžete sledovat více proměnných. Hodnoty sledovaných proměnných, jako jsou hodnoty v oknech s popisem dat, se aktualizují pokaždé, když je spuštění pozastaveno. Sledované proměnné jsou uloženy napříč relacemi ladění.

7. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: **SHIFT + F5**). Tím skončí vaše ladicí relace.

## <a name="step-into-over-and-out-of-functions"></a><a name="BKMK_Step_into__over__and_out_of_functions"></a> Krokovat s vnořením funkcí
 Na rozdíl od krokování do funkce, která je volána nadřazenou funkcí, krokování na funkci provede podřízenou funkci a poté pozastaví provádění ve volání funkce jako nadřazené operace obnovení. Pokud jste obeznámeni se způsobem fungování funkce a jste se ujistili, že její spuštění nebude mít vliv na problém, který zkoumáte, můžete na funkci krokovat.

 Krokování nad řádkem kódu, který neobsahuje volání funkce, provede řádek stejně jako krokování do řádku.

 Krokování mimo podřízenou funkci pokračuje v provádění této funkce a pak je vykoná, jakmile se funkce vrátí ke své volající funkci. Pokud určíte, že zbytek funkce není významný, může dojít k zakrokování na dlouhou funkci.

 Při krokování a krokování ven z funkce se spustí funkce.

 ![Krokovat s vnořením metod](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a><a name="BKMK_Example_2"></a> Příklad 2
 V tomto příkladu můžete krokovat s funkcemi.

1. **Ve funkci modulu volejte funkci example2.** Upravte `module` funkci a nahraďte řádek následujícím: `var callTrack = "module function"` `example2();` .

     ![Volání funkce example2](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5). Ladicí program pozastaví provádění na zarážce.

3. **Krok za řádkem kódu.** V nabídce **ladění** vyberte možnost **Krokovat přes** (klávesnice: F10). Ladicí program spustí `var callTrack = "module function"` příkaz stejným způsobem jako krokování příkazu.

4. **Krok do example2 a example2_a.** Vyberte klávesu **F11** ke kroku do `example2` funkce. Pokračujte krokem do příkazů, `example2` dokud se nedostanete na řádek `var x = example2_a();` . Opakujte krok do tohoto řádku, aby se přesunul na vstupní bod `example2_a` . Pokračujte krokem do každého příkazu, `example2_a` dokud se nevrátíte do `example2` .

     ![Krokovat s funkcí](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5. **Krokovat s funkcí** Všimněte si, že další řádek v `example2` , `var y = example2_a();` je v podstatě stejný jako předchozí řádek. Přes tento řádek můžete bezpečně krokovat. Vyberte klávesu **F10** pro přechod z obnovení `example2` do tohoto druhého volání `example2_a` . Všimněte si, že `callTrack` řetězec označuje, že `example2_a` funkce byla provedena dvakrát.

6. **Krok ven z funkce** Vyberte klávesu **F11** ke kroku do `example2_b` funkce. Všimněte si, že `example2_b` se neliší od `example2_a` . Chcete-li krok z funkce krokovat, v nabídce **ladění** vyberte možnost **Krok ven** (klávesnice: **SHIFT + F11**). Všimněte si, že `callTrack` Proměnná označuje, že `example2_b` byla provedena a že se ladicí program vrátil do bodu, kde `example2` pokračuje.

7. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: **SHIFT + F5**). Tím skončí vaše ladicí relace.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Nastavte podmíněnou zarážku, spusťte ji na kurzor a vizualizujte proměnnou.
 Podmíněná zarážka Určuje podmínku, která způsobí, že ladicí program zastaví provádění. Podmínka je určena jakýmkoli výrazem kódu, který lze vyhodnotit jako true nebo false. Můžete například použít podmíněnou zarážku k prohlédnutí stavu programu často volanou funkci pouze v případě, že proměnná dosáhne určité hodnoty.

 Běžící na kurzor je jako nastavení jednorázové zarážky. Když je spuštění pozastavené, můžete vybrat řádek ve zdroji a pokračovat v provádění, dokud se nedosáhne vybraného řádku. Například můžete prohloubit smyčku ve funkci a určit, že kód ve smyčce provádí správné fungování. Namísto krokování v každé iteraci smyčky můžete spustit na ukazatel, který je umístěn po provedení smyčky.

 Někdy je obtížné zobrazit hodnotu proměnné na řádku tipu dat nebo v jiném okně dat. Ladicí program může zobrazit řetězce, HTML a XML v Vizualizér textu, který prezentuje formátované zobrazení hodnoty v rolovacím okně.

### <a name="example-3"></a><a name="BKMK_Example_3"></a> Příklad 3
 V tomto příkladu nastavíte podmíněnou zarážku na přerušení v konkrétní iteraci smyčky a pak ji spustíte na kurzor, který je umístěný po smyčce. Také se zobrazí hodnota proměnné v Vizualizér textu.

1. **Ve funkci modulu volejte funkci example3.** Upravte `module` funkci a nahraďte řádek následujícím `var callTrack = "module function";` řádkem `example3();` .

     ![Example3 volání](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: **F5**). Ladicí program pozastaví provádění na zarážce ve `module` funkci.

3. **Krok do funkce example3** Zvolením možnosti **Krokovat** v nabídce **ladění** (klávesnice: **F11**) přejděte na vstupní bod `example3` funkce. Pokračujte v krokování do funkce, dokud neprovedete iteraci jednoho nebo dvou smyček `for` bloku. Všimněte si, že provedete dlouhou dobu ke krokování všech iterací 1000.

4. **Nastavte podmíněnou zarážku.** V levém horním rohu okna Code klikněte pravým tlačítkem myši na řádek `s += i.toString() + "\n";` a pak zvolte možnost **Podmínka** v místní nabídce.

     Zaškrtněte políčko **Podmínka** a zadejte `i == 500;` do textového pole. Vyberte možnost **je true** a klikněte na **tlačítko OK**. Zarážka umožňuje kontrolovat hodnotu v iteraci 500th `for` smyčky. Můžete určit podkladovou ikonu zarážky pomocí bílé křížení.

     ![Ikona zarážky podmíněný](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5. **Spustit na zarážku.** V nabídce **ladění** vyberte možnost **pokračovat** (klávesnice: **F5**). Pozastavením na `i` pro potvrďte, že aktuální hodnota `i` je 500. Všimněte si také, že proměnná `s` je reprezentována jako jeden řádek a je mnohem delší než okno s tipem dat.

6. **Vizualizujte proměnnou řetězce.** Klikněte na ikonu lupy v datovém hrotu v `s` .

     Zobrazí se okno Vizualizér textu a hodnota řetězce je prezentována jako víceřádkový řetězec.

     ![Vizualizér ladění textu](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7. **Spustit na kurzor.** Vyberte řádek `callTrack += "->example3";` a pak zvolte možnost **Spustit pro kurzor** v místní nabídce (klávesnice: **CTRL + F10**). Ladicí program dokončí iterace smyčky a pak pozastaví provádění na řádku.

8. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: **SHIFT + F5**). Tím skončí vaše ladicí relace.

### <a name="use-run-to-cursor-to-return-to-your-code-and-delete-a-breakpoint"></a><a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Pomocí kurzoru spustit pro se vrátíte do kódu a odstraníte zarážku.
 Běžící na kurzor může být velmi užitečné, pokud jste se přihlásili ke kódu knihovny od společnosti Microsoft nebo třetí strany. Při procházení kódu knihovny může být informativní, často může trvat dlouhou dobu. A obvykle ještě mnohem více zajímáte o vlastní kód. V tomto cvičení se dozvíte, jak to provést.

1. **Nastavte zarážku ve volání app. Start.** Ve `module` funkci nastavte zarážku na řádku. `app.start()`

2. **Spusťte na zarážku a krok do funkce Library.**

     Při krokovat s vnořením `app.start()` v editoru se zobrazí kód v `base.js` . Proveďte krok do několika dalších řádků.

3. **Krokování funkcí a převzetí služeb při selhání.** Při krokování (**F10**) a krok ven z (**SHIFT + F11**) kódu v `base.js` můžete přijít k závěru, že zkoumání složitosti a délky spouštěcí funkce není to, co chcete dělat.

4. **Nastavte kurzor na svůj kód a spusťte jej.** Přepněte zpět do `default.js` souboru v editoru kódu. Vyberte první řádek kódu za `app.start()` (nemůžete spustit do komentáře nebo prázdného řádku). Z místní nabídky vyberte možnost **Spustit ke kurzoru** . Ladicí program pokračuje v provádění funkce App. Start a pozastaví provádění na zarážce.

## <a name="view-variable-data-in-the-locals-window"></a><a name="BKMK_View_variable_data_in_the_Locals_window"></a> Zobrazení dat proměnných v okně místních hodnot
 Okna místních hodnot jsou stromové zobrazení parametrů a proměnných v řetězci oboru aktuálně vykonávané funkce.

### <a name="view-variable-data-and-the-prototype-chain-of-an-object"></a><a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Zobrazení dat proměnných a řetězce prototypu objektu

1. **Přidejte objekt Array funkce modulu.** Upravte `module` funkci a nahraďte řádek následujícím: `var callTrack = "module function"``var myArray = new Array(1, 2, 3);`

     ![definice myArray](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: **F5**). Ladicí program pozastaví provádění na zarážce. Krokovat s vnořením na řádek.

3. **Otevřete okno místní hodnoty.** V nabídce **ladění** přejděte na příkaz **Windows**a vyberte možnost **místní**. (Klávesnice: ALT + 4).

4. **Kontrola místních proměnných ve funkci modulu** Okna místní hodnoty zobrazí proměnné aktuálně vykonávané funkce ( `module` funkce) jako uzly nejvyšší úrovně stromu. Když zadáte funkci, JavaScript vytvoří všechny proměnné a poskytne jim hodnotu `undefined` . Funkce, které jsou definovány ve funkci, mají jejich text jako hodnotu.

     ![Místní hodnoty – okno](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5. **Projděte si definice callTrack a myArray.** V okně místní hodnoty Najděte proměnné callTrack a myArray. Krok za (**F10**) dvě definice a Všimněte si, že pole **hodnota** a **typ** se změnila. Okno místních hodnot zvýrazní hodnoty proměnných, které se od posledního přerušení změnily.

6. **Prověřte objekt myArray** . Rozbalte `myArray` proměnnou. Každý prvek pole je uveden v uzlu **[prototyp]** , který obsahuje hierarchii dědičnosti `Array` objektu. Rozbalte tento uzel.

     ![Řetězec prototypu v okně místních hodnot](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    - Uzel **metody** obsahuje seznam všech metod `Array` objektu.

    - Uzel **[prototyp]** obsahuje prototyp `Object` objektu, ze kterého `Array` je odvozen. uzly **[prototyp]** mohou být rekurzivní. Každý nadřazený objekt v hierarchii objektů je popsán v uzlu **[prototyp]** svého podřízeného objektu.

7. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: Shift + F5). Tím skončí vaše ladicí relace.

## <a name="examine-scope-chain-data"></a><a name="BKMK_Examine_scope_chain_data"></a> Prověřte data řetězu oboru
 *Řetěz rozsahu* funkce zahrnuje všechny proměnné, které jsou aktivní a dosažitelné funkcí. Globální proměnné jsou součástí řetězu oboru, stejně jako všechny objekty (včetně funkcí), které jsou definovány ve funkci, která definuje aktuálně prováděnou funkci. Například `callTrack` Proměnná, která je definována ve `module` funkci, `default.js` je dosažitelná všemi funkcemi, které jsou definovány ve `module` funkci. Každý obor je uveden samostatně v okně místní hodnoty.

- Proměnné aktuálně vykonávané funkce jsou uvedeny v horní části okna.

- Proměnné každého oboru funkce v řetězu oboru jsou uvedeny pod uzlem **[scope]** pro danou funkci. Funkce oboru jsou uvedeny podle jejich pořadí v řetězci, ze funkce, která definuje aktuální funkci na vnější funkci řetězce.

- Uzel **[globals]** obsahuje seznam globálních objektů, které jsou definovány mimo jakoukoliv funkci.

  Řetězy rozsahu mohou být matoucí a jsou nejlépe znázorněny příkladem. V následujícím příkladu vidíte, jak `module` funkce vytvoří svůj vlastní obor a jak můžete vytvořit další úroveň rozsahu vytvořením uzávěru.

### <a name="example-4"></a><a name="BKMK_Example_4"></a> Příklad 4

1. **Volejte funkci example4 z funkce modulu.** Upravte `module` funkci a nahraďte řádek následujícím `var callTrack = "module function"` `example4()` :

     ![Example4 volání](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: **F5**). Ladicí program pozastaví provádění na zarážce.

3. **Otevřete okno místní hodnoty.** V případě potřeby v nabídce **ladění** přejděte na možnost **Windows**a pak zvolte možnost **místní**. (Klávesnice: **ALT + 4**). Všimněte si, že okno obsahuje všechny proměnné a funkce ve `module` funkci a také obsahuje uzel **[globals]** .

4. **Prověřte globální proměnné.** Rozbalte uzel **[globals]** . Objekty a proměnné v globální sadě byly nastaveny knihovnou Windows Library for JavaScript. Do globálního oboru můžete přidat vlastní proměnné.

5. **Krok do example4 a přezkoumání jeho místních proměnných a proměnných oboru** Krokovat s vnořením funkce (klávesnice: **F11**) `example4` . Vzhledem k tomu `example4` , že je ve `module` funkci definován, funkce se `module` stala nadřazeným oborem. `example4` může volat libovolné funkce ve `module` funkci a přistupovat k jejím proměnným. Rozbalte uzel **[scope]** v okně místní hodnoty a Všimněte si, že obsahuje stejné a proměnné `module` funkce.

     ![Obory metody example4](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6. **Krok do example4_a a prohlédnutí jeho místních proměnných a proměnných oboru** Pokračujte krokem do `example4` a do volání `example4_a` . Všimněte si, že místní proměnné jsou nyní z `example4_a` a že uzel **[scope]** nadále drží proměnné `module` funkce. I když proměnné `example4` jsou aktivní, nemohou být dostupné v `example4_a` a již nejsou součástí řetězu oboru.

7. **Krok do multiplyByA a přezkoumání jeho místních proměnných a proměnných oboru** Projděte si zbytek `example4_a` a na řádek `var x = multiplyByA(b);` .

     Proměnná funkce `multiplyByA` byla nastavena na `multiplyClosure` funkci, která je *uzavřená*. `multiplyClosure` definuje a vrátí vnitřní funkci, `multiplyXby` , a zachycuje (ukončí) jeho parametr a proměnnou. Při uzavření má vrácená vnitřní funkce přístup k datům vnější funkce a vytvoří svou vlastní úroveň rozsahu.

     Když přejdete na krok do, přejdete `var x = multiplyByA(b);` na `return a * b;` řádek `multiplyXby` vnitřní funkce.

8. V okně místní hodnoty je pouze parametr `b` uveden jako místní proměnná v `multiplyXby` , ale byla přidána nová úroveň **[scope]** . Rozbalením tohoto uzlu vidíte, že obsahuje parametry, funkce a proměnné `multiplyClosure` , včetně `a` proměnné s názvem v prvním řádku `multiplyXby` . Rychlá kontroly druhého uzlu **[scope]** odhalí proměnné funkcí modulu, které `multiplyXby` přistupují k dalšímu řádku.

9. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: **SHIFT + F5**). Tím skončí vaše ladicí relace.

## <a name="navigate-to-code-by-using-the-call-stack-window"></a><a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Přechod na kód pomocí okna zásobník volání
 Zásobník volání je datová struktura, která obsahuje informace o funkcích, které jsou spuštěny v aktuálním vlákně aplikace. Když zaškrtnete zarážku, okno zásobník volání zobrazí seznam všech funkcí, které jsou v zásobníku aktivní. Aktuálně vykonávaná funkce je v horní části seznamu oken zásobníku volání. Funkce, která inicializuje vlákno, je na konci seznamu. Funkce v mezi zobrazují cestu volání z funkce iniciace do aktuální funkce.

 Kromě zobrazení cesty volání k aktuálně vykonávané funkci lze okno zásobník volání použít k přechodu na kód v editoru kódu. Tato funkce může být užitečná, když pracujete s více soubory a chcete rychle přejít na konkrétní funkci.

### <a name="example-5"></a><a name="BKMK_Example_5"></a> Příklad 5
 V tomto příkladu je třeba Krokovat s cestou volání, která obsahuje pět uživatelsky definovaných funkcí.

1. **Ve funkci modulu volejte funkci example5.** Upravte `module` funkci a nahraďte řádek následujícím `var callTrack = "module function";` řádkem `example5();` .

     ![Example5 volání](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2. **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: **F5**). Ladicí program pozastaví provádění na zarážce ve funkci modulu.

3. **Otevřete okno zásobník volání.** V nabídce **ladění** zvolte **okna**a pak zvolte **zásobník volání** (klávesnice: ALT + 7). Všimněte si, že okno zásobník volání zobrazuje dvě funkce:

    - **Globální kód** je vstupním bodem `module` funkce v dolní části zásobníku volání.

    - **Anonymní funkce** zobrazuje řádek ve `module` funkci, kde je provádění pozastaveno. Toto je horní část zásobníku volání.

4. **Krok do funkcí pro dosažení example5_d funkce.** Zvolením možnosti **Krokovat** v nabídce **ladění** (klávesnice: **F11**) spusťte volání v cestě volání, dokud nedosáhnete vstupního bodu funkce example5_d. Všimněte si, že pokaždé, když funkce volá funkci, je uloženo číslo řádku volající funkce a volaná funkce je umístěna v horní části zásobníku. Číslo řádku funkce volání je bod, ve kterém volající funkce pozastavila provádění. Žlutá šipka ukazuje na aktuálně vykonávanou funkci.

     ![Okno zásobníku volání](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5. **Pomocí okna zásobník volání přejděte na kód example5_a a nastavte zarážku.** V okně zásobník volání vyberte `example5_a` položku seznamu a v místní nabídce zvolte možnost **Přejít ke zdroji** . Editor kódu nastaví jeho kurzor na návratovou řádku funkce. Nastaví zarážku na tomto řádku. Všimněte si, že aktuální řádek spuštění se nemění. Přesunul se pouze kurzor editoru.

6. **Krok do funkcí a následné spuštění na zarážku.** Pokračujte v krokování `example5_d` . Všimněte si, že když se vrátíte z funkce, je vyvoláno v zásobníku volání. Stisknutím klávesy **F5** pokračujte v provádění programu. Zastavíte se na zarážce vytvořené v předchozím kroku.

7. **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: **SHIFT + F5**). Tím skončí vaše ladicí relace.

## <a name="see-also"></a>Viz také
 [Spuštění ladicí relace (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [rychlý Start: navigace ladicího programu (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) : ladění aktivačních událostí [HTML a šablon stylů CSS](../debugger/quickstart-debug-html-and-css.md) [pozastavení, obnovení a události na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
