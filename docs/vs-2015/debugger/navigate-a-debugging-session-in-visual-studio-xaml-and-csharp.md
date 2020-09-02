---
title: Navigace v relaci ladění (XAML a C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8d24f01f7882e8c760918119a03a1c489c727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156857"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Přechod na relaci ladění ve Visual Studiu (Xaml a C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento rychlý Start ukazuje, jak navigovat relace ladění sady Visual Studio a jak zobrazit a změnit stav programu v relaci.

 Tento rychlý Start je určen vývojářům, kteří jsou novinkou k ladění pomocí sady Visual Studio a pro vývojáře, kteří se chtějí dozvědět více o navigaci v ladicí relaci sady Visual Studio. Neučí grafiku samotného ladění. Metody v ukázkovém kódu jsou určeny pouze k předvedení postupů ladění popsaných v tomto tématu. Metody nevyužívají osvědčené postupy návrhu aplikací nebo funkcí. Ve skutečnosti rychle zjistíte, že metody a samotná aplikace nedělají vůbec žádné z jakýchkoli věcí.

 Části tohoto rychlého startu byly navržené tak, aby byly co nezávisle, takže můžete přeskočit všechny části, které obsahují informace, se kterými už jste obeznámeni. Nemusíte také vytvářet ukázkovou aplikaci. doporučujeme ho ale doporučit a co nejjednodušší je udělat.

 **Klávesové zkratky pro ladicí program.** Navigace v ladicím programu sady Visual Studio je optimalizovaná pro myš i klávesnici. Mnohé z kroků v tomto tématu zahrnují klávesovou zkratku nebo klávesovou zkratku v případě přeznačení kulatého kulatého závorky. Například (klávesnice: F5) označuje, že psaní klávesy F5 se spustí nebo pokračuje v provádění ladicího programu.

## <a name="in-this-topic"></a>V tomto tématu
 Můžete se dozvědět, jak:

- [Vytvoření ukázkové aplikace](#BKMK_CreateTheApplication)

- [Nastavit a spustit na zarážku, Krokovat s vnořením do metody a prozkoumávat data programu](#BKMK_StepInto)

- [Krokovat s vnořením metod](#BKMK_StepIntoOverOut)

- [Nastavte podmíněnou zarážku, spusťte ji na kurzor a vizualizujte proměnnou.](#BKMK_ConditionCursorVisualize)

- [Upravit a pokračovat, obnovit z výjimky](#BKMK_EditContinueRecoverExceptions)

## <a name="create-the-sample-app"></a><a name="BKMK_CreateTheApplication"></a> Vytvoření ukázkové aplikace
 Ladění je o kódu, takže ukázková aplikace používá architekturu aplikace pro Windows Store pouze k vytvoření zdrojového souboru, ve kterém vidíte, jak navigace ladicí relace funguje a jak kontrolovat a měnit stav programu. Veškerý kód, který budete volat, je volán z konstruktoru hlavní stránky; nepřidaly se žádné ovládací prvky a nezpracovávají se žádné události.

 **Vytvoří výchozí aplikaci pro Windows Store v C#.** Otevřete sadu Visual Studio. Na domovské stránce klikněte na odkaz **Nový projekt** . V dialogovém okně Nový projekt zvolte v seznamu **nainstalované** položku **Visual C#** a pak zvolte možnost **Windows Store**. V seznamu šablon projektu vyberte možnost **aplikace**. Visual Studio vytvoří nové řešení a projekt a zobrazí MainPage. XAML Designer a Editor kódu XAML.

 **Otevřete zdrojový soubor MainPage.xaml.cs.** Klikněte pravým tlačítkem myši kdekoli v editoru XAML a vyberte **Zobrazit kód**. Zobrazí se soubor kódu na pozadí MainPage.xaml.cs. Všimněte si, že `MainPage()` v souboru je uvedena pouze jedna metoda, konstruktor.

 **Nahraďte konstruktor MainPage ukázkovým kódem.** Odstraňte metodu MainPage (). Použijte tento odkaz: [ladicí program pro navigaci v ladicím programu (XAML a C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)a potom zkopírujte kód uvedený v části C# do schránky. (Kliknutím na tlačítko **zpět** v prohlížeči nebo v prohlížeči nápovědy se vraťte na tuto stránku rychlý Start.) V editoru sady Visual Studio vložte kód do `partial class MainPage` bloku. Klikněte na tlačítko CTRL + s a soubor uložte.

 Teď můžete postupovat podle příkladů v tomto tématu.

## <a name="set-and-run-to-a-breakpoint-step-into-a-method-and-examine-program-data"></a><a name="BKMK_StepInto"></a> Nastavit a spustit na zarážku, Krokovat s vnořením do metody a prozkoumávat data programu
 Nejběžnější způsob, jak spustit relaci ladění, je zvolit možnost **Spustit ladění** z nabídky **ladění** (klávesnice: F5). Spuštění začíná a pokračuje, dokud není dosaženo zarážky, dojde k ručnímu pozastavení provádění, výskytu výjimky nebo ukončení aplikace.

 Když je spuštění pozastaveno v ladicím programu, můžete zobrazit hodnotu aktivní proměnné v datovém tipu přesunutím ukazatele myši na proměnnou. Můžete také otevřít okna místní hodnoty a automatické hodnoty a zobrazit tak seznamy aktivních proměnných a jejich aktuální hodnoty. Přidání jedné nebo více proměnných do okna kukátka vám umožní soustředit se na hodnotu proměnných, když aplikace pokračuje v provádění.

 Po pozastavení provádění aplikace (která se také označuje jako rozdělení do ladicího programu) můžete řídit způsob, jakým se spustí zbytek kódu programu. Můžete pokračovat řádek po řádku, přesun z volání metody do samotné metody nebo můžete spustit volanou metodu v jednom kroku. Tyto postupy se nazývají krokování aplikace. Můžete také obnovit standardní spuštění aplikace, spuštění na další zarážku, kterou jste nastavili, nebo na řádek, na který jste umístili kurzor. Ladicí relaci můžete kdykoli zastavit. Ladicí program je navržen tak, aby prováděl nezbytné operace vyčištění a ukončila provádění.

### <a name="example-1"></a>Příklad 1
 V tomto příkladu nastavíte zarážku v konstruktoru MainPage souboru MainPage.xaml.cs, krok do první metody, prohlédněte hodnoty proměnných a pak zastavíte ladění.

 **Nastavte zarážku.** Nastavte zarážku na příkaz `methodTrack = "Main Page";` v konstruktoru MainPage. Vyberte čáru ve stínovém rámečku editoru zdrojového kódu (klávesnice: Umístěte kurzor na řádek a vyberte klávesu F9).

 ![Krokovat s vnořením](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Ikona zarážky se zobrazí na hřbetu.

 **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5).

 Aplikace začne provádět a pozastaví provádění přímo před příkazem, na kterém jste nastavili zarážku. Ikona aktuálního řádku na hřbetu označuje vaše umístění a zvýrazní se aktuální příkaz.

 ![Nastavení zarážky](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Nyní máte kontrolu nad prováděním aplikace a můžete zkontrolovat stav programu při procházení příkazů programu.

 **Krok do metody.** V nabídce **ladění** vyberte možnost **Krokovat** s vnořením (klávesnice: F11).

 ![Aktuální řádek](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Všimněte si, že ladicí program se přesune na další řádek, což je volání metody priklad1. Vyberte znovu krok. Ladicí program se přesune ke vstupnímu bodu metody priklad1. To znamená, že metoda byla načtena do zásobníku volání a byla přidělena paměť pro lokální proměnné.

 Při kroku na řádek kódu provede ladicí program jednu z následujících akcí:

- Pokud další příkaz není voláním funkce ve vašem řešení, ladicí program provede příkaz, přesune se k dalšímu příkazu a pak pozastaví provádění.

- Pokud je příkaz volání funkce ve vašem řešení, ladicí program se přesune do vstupního bodu volané funkce a pak pozastaví provádění.

  Pokračujte krokem do příkazů priklad1, dokud nedosáhnete bodu ukončení. Ladicí program zvýrazní pravou složenou závorku metody.

  **Prověřte hodnoty proměnných v tipech k datům.** Když najedete myší na název proměnné, zobrazí se název, hodnota a typ proměnné v popisku dat.

  ![Tip pro data ladicího programu](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Najeďte myší na proměnnou `a` . Poznamenejte si název, hodnotu a datový typ. Najeďte myší na proměnnou `methodTrack` . Znovu si poznamenejte název, hodnotu a datový typ.

  **Prověřte hodnoty proměnných v okně místních hodnot.** V nabídce **ladění** přejděte na příkaz **Windows**a vyberte možnost **místní**. (Klávesnice: ALT + 4).

  ![Místní hodnoty – okno](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Okna místních hodnot jsou stromovým zobrazením parametrů a proměnných funkce. Vlastnosti proměnné objektu jsou podřízené uzly samotného objektu. `this`Proměnná je skrytý parametr v každé metodě objektu, která představuje samotný objekt. V tomto případě představuje třídu MainPage. Vzhledem k tomu `methodTrack` , že je členem třídy MainPage, je její hodnota a datový typ uvedena na řádku pod `this` . Rozbalením `this` uzlu zobrazíte `methodTrack` informace.

  **Přidejte kukátko pro proměnnou methodTrack.** `methodWatch`Proměnná se používá v rámci tohoto rychlého startu k zobrazení metod volaných v příkladech. Chcete-li usnadnit zobrazení hodnoty proměnné, přidejte ji do okna kukátka. Klikněte pravým tlačítkem myši na název proměnné v okně místní hodnoty a zvolte možnost **Přidat kukátko**.

  ![Kukátko – okno](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  V okně kukátka můžete sledovat více proměnných. Hodnoty sledovaných proměnných, jako jsou hodnoty v oknech lokální hodnoty a data, se aktualizují pokaždé, když je spuštění pozastaveno. Do okna kukátka můžete také přidat proměnné z editoru kódu. Vyberte proměnnou, která se má sledovat, klikněte pravým tlačítkem myši a pak zvolte **Přidat kukátko**.

## <a name="step-into-over-and-out-of-methods"></a><a name="BKMK_StepIntoOverOut"></a> Krokovat s vnořením metod
 Na rozdíl od krokování do metody, která je volána nadřazenou metodou, krokování nad metodou provede podřízenou metodu a poté pozastaví provádění v volající metodě jako nadřazené operace obnovení. Můžete krokovat s metodou, pokud znáte způsob, jakým metoda funguje, a ujistěte se, že její spuštění nebude mít vliv na problém, který zkoumáte.

 Krokování nad řádkem kódu, který neobsahuje volání metody, provede řádek stejně jako krokování do řádku.

 Krokování mimo podřízenou metodu pokračuje v provádění metody a pak pozastaví provádění poté, co se metoda vrátí ke své volající metodě. Pokud určíte, že zbytek funkce není významný, může dojít k zakrokování na dlouhou funkci.

 Při krokování a krokování ven z funkce se spustí funkce.

 ![Krokovat s vnořením metod](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Příklad 2
 V tomto příkladu můžete krokovat s metodou.

 **V konstruktoru MainPage volejte metodu example2.** Upravte konstruktor MainPage a nahraďte řádek následujícím: `methodTrack = String.Empty;` `Example2();` .

 ![Volat metodu example2 z ukázkové metody](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5). Ladicí program pozastaví provádění na zarážce.

 **Krok za řádkem kódu.** V nabídce **ladění** vyberte možnost **Krokovat přes** (klávesnice: F10). Ladicí program spustí `methodTrack = "MainPage";` příkaz stejným způsobem jako krokování příkazu.

 **Krok do example2 a Example2_A.** Vyberte klávesu F11 a proveďte krok do příkladu 2 metody. Pokračujte krokem na příkazy example2, dokud se nedostanete na řádek `int x = Example2_A();` . Opakujte krok do tohoto řádku, aby se přesunul na vstupní bod Example2_A. Pokračujte krokem do každého příkazu Example2_A, dokud se nevrátíte do example2.

 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Krokovat s funkcí** Všimněte si, že další řádek v example2 `int y = Example2_A();` je v podstatě stejný jako předchozí řádek. Přes tento řádek můžete bezpečně krokovat. Vyberte klávesu F10 pro přechod od obnovení example2 k druhému volání Example2_A. Vyberte F10 pro krokování této metody. Všimněte si, že `methodTrack` řetězec označuje, že metoda example2_a byla provedena dvakrát. Všimněte si také, že ladicí program se okamžitě přesune na další řádek. Neblokuje provádění v bodu example2 pokračování.

 **Krok ven z funkce** Vyberte klávesu F11 pro krok do Example2_B metody. Všimněte si, že Example2_B se neliší od Example2_A. Chcete-li Krokovat s metodou, v nabídce **ladění** vyberte možnost **Krok ven** (klávesnice: Shift + F11). Všimněte si, že `methodTrack` Proměnná označuje, že byla provedena example2_b a že se ladicí program vrátil do bodu, kde example2 pokračuje.

 **Zastavit ladění.** V nabídce ladění vyberte možnost zastavit ladění (klávesnice: Shift + F5). Tím skončí vaše ladicí relace.

## <a name="set-a-conditional-breakpoint-run-to-the-cursor-and-visualize-a-variable"></a><a name="BKMK_ConditionCursorVisualize"></a> Nastavte podmíněnou zarážku, spusťte ji na kurzor a vizualizujte proměnnou.
 Podmíněná zarážka Určuje podmínku, která způsobí, že ladicí program zastaví provádění. Podmínka je určena jakýmkoli výrazem kódu, který lze vyhodnotit jako true nebo false. Můžete například použít podmíněnou zarážku k prohlédnutí stavu programu často volanou metodou pouze v případě, že proměnná dosáhne určité hodnoty.

 Běžící na kurzor je jako nastavení jednorázové zarážky. Když je spuštění pozastavené, můžete vybrat řádek ve zdroji a pokračovat v provádění, dokud se nedosáhne vybraného řádku. Například můžete prohloubit smyčku v metodě a určit, že kód ve smyčce provádí správné fungování. Namísto krokování v každé iteraci smyčky můžete spustit na ukazatel, který je umístěn po provedení smyčky.

 V některých případech je obtížné zobrazit hodnotu proměnné na řádku s tipem dat nebo v okně proměnných. Ladicí program může zobrazit řetězce, HTML a XML v Vizualizér textu, který prezentuje formátované zobrazení hodnoty v rolovacím okně.

### <a name="example-3"></a>Příklad 3
 V tomto příkladu nastavíte podmíněnou zarážku na přerušení v konkrétní iteraci smyčky a pak ji spustíte na kurzor, který je umístěný po smyčce. Také se zobrazí hodnota proměnné v Vizualizér textu.

 **V konstruktoru MainPage volejte metodu example3.** Upravte konstruktor MainPage a nahraďte řádek následujícím `methodTrack = String.Empty;` řádkem `Example3();` .

 ![Volání example3 z ukázkové metody](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Spustit na zarážku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5). Ladicí program pozastaví provádění na zarážce v metodě MainPage.

 **Proveďte krok do metody example3.** Zvolením možnosti **Krokovat** v nabídce **ladění** (klávesnice: F11) přejděte na vstupní bod metody example3. Pokračujte v krokování do metody, dokud neprovedete iteraci jednoho nebo dvou smyček `for` bloku. Všimněte si, že provedete dlouhou dobu ke krokování všech iterací 1000.

 **Nastavte podmíněnou zarážku.** V levém horním rohu okna Code klikněte pravým tlačítkem myši na řádek `x += i;` a zvolte možnost **Podmínka**. Zaškrtněte políčko **Podmínka** a potom zadejte `i == 500;` do textového pole. Vyberte možnost **je true** a klikněte na **tlačítko OK**. Zarážka umožňuje kontrolovat hodnotu v iteraci 500th `for` smyčky.

 ![Podmínka zarážky – dialogové okno](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Můžete určit podkladovou ikonu zarážky pomocí bílé křížení.

 ![Podmíněná zarážka](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Spustit na zarážku.** V nabídce ladění vyberte možnost pokračovat (klávesnice: F5). V okně místní hodnoty potvrďte, že aktuální hodnota `i` je 500. Všimněte si, že proměnná `s` je reprezentována jako jeden řádek a je mnohem delší než okno.

 **Vizuální a řetězcovou proměnnou.** Klikněte na ikonu lupy ve sloupci **hodnota** v `s` .

 Zobrazí se okno Vizualizér textu a hodnota řetězce je prezentována jako víceřádkový řetězec.

 **Spustit na kurzor.** Klikněte na čáru pravým tlačítkem myši `methodTrack += "->Example3";` a pak zvolte možnost **Spustit ke kurzoru** (klávesnice: přesunout kurzor na řádek; CTRL + F10). Ladicí program dokončí iterace smyčky a pak pozastaví provádění na řádku.

 **Zastavit ladění.** V nabídce ladění vyberte možnost zastavit ladění (klávesnice: Shift + F5). Tím skončí vaše ladicí relace.

## <a name="edit-and-continue-recover-from-an-exception"></a><a name="BKMK_EditContinueRecoverExceptions"></a> Upravit a pokračovat, obnovit z výjimky
 V některých případech, při přerozdělování do kódu v ladicím programu sady Visual Studio máte příležitost změnit hodnotu proměnné a dokonce i logiky příkazů. Tato funkce se nazývá upravit a pokračovat.

 Možnost upravit a pokračovat může být obzvláště užitečná při přerušení výjimky. Místo nutnosti zastavit a znovu spustit ladění dlouhého a souvisejícího postupu, abyste se vyhnuli výjimce, můžete "unwind" výjimku pro přesun provádění do bodu bezprostředně před tím, než došlo k výjimce, a poté změnit problematickou proměnnou nebo příkaz a pokračovat v aktuální relaci ladění ve stavu, který nevyvolá výjimku.

 I když můžete použít funkci upravit a pokračovat v nejrůznějších situacích, je obtížné určit konkrétní podmínky, které nepodporují funkci upravit a pokračovat, protože podmínky závisí na programovacím jazyku, aktuálním stavu zásobníku programu a schopnost ladicího programu změnit stav bez poškození procesu. Nejlepším způsobem, jak určit, zda je změna úpravy podporována, je pouze vyzkoušet si ji. ladicí program vám umožní okamžitě zjistit, jestli není změna podporovaná.

### <a name="example-4"></a>Příklad 4
 V tomto příkladu spustíte ladicí program pro výjimku, znovu převedete výjimku, opravíte logiku metody a pak změníte hodnotu proměnné tak, aby bylo možné pokračovat v provádění metody.

 **V konstruktoru MainPage volejte metodu Example4.** Upravte konstruktor MainPage () a nahraďte řádek následujícím `methodTrack = String.Empty;` řádkem `Example4();` .

 ![Volání example4 z ukázkové metody](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Spusťte výjimku.** Spusťte ladicí relaci výběrem možnosti **Spustit ladění** v nabídce **ladění** (klávesnice: F5). Stisknutím klávesy F5 znovu pokračujte v provádění. Ladicí program pozastaví provádění na výjimce v metodě example4 a zobrazí dialogové okno výjimky.

 ![Výjimka – dialogové okno](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Změňte logiku programu.** Je zřejmé, že chyba je v `if` podmínce: hodnota `x` by měla být změněna, pokud `x` je rovna 0; ne, pokud `x` není rovna nule. Vyberte možnost **přerušit** pro opravu logiky metody. Při pokusu o úpravu řádku se zobrazí další dialogové okno.

 ![Dialogové okno Upravit a pokračovat](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Zvolte **Upravit** a pak změňte řádek `if (x != 0)` na `if (x == 0)` . Ladicí program uchovává změny v logice programu do zdrojového souboru.

 **Změňte hodnotu proměnné.** Prověřte hodnotu `x` v tipu dat nebo v okně místní hodnoty. Je stále 0 (nula). Pokud se pokusíte spustit příkaz, který způsobil původní výjimku, bude znovu vyvolána. Můžete změnit hodnotu `x` . V okně místní hodnoty dvakrát klikněte na sloupec **hodnota** řádku **x** . Změňte hodnotu z 0 na 1.

 ![Úprava hodnoty v okně místních hodnot](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Vyberte klávesu F11 a proveďte krok do příkazu, který dříve vyvolal výjimku. Všimněte si, že se řádek spouští bez chyby. Znovu vyberte klávesu F11.

 **Zastavit ladění.** V nabídce **ladění** vyberte možnost **Zastavit ladění** (klávesnice: Shift + F5). Tím skončí vaše ladicí relace.

## <a name="see-also"></a>Viz také
 [Spuštění ladicí relace (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [aktivační události pro ladění, obnovení a události na pozadí pro Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) : [ladění aplikací v aplikaci Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
