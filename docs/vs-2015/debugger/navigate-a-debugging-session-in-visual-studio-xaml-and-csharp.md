---
title: Přechod na relaci ladění (Xaml a C#) | Dokumentace Microsoftu
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
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a3dc5236d47450cb755ff8abbffd5b6497ff145
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052242"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Přechod na relaci ladění ve Visual Studiu (Xaml a C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento rychlý start ukazuje, jak se zorientovat relacemi ladění sady Visual Studio a jak zobrazit a změnit stav programu v relaci.

 Tento rychlý start je pro vývojáře, kteří jsou nové pro ladění v sadě Visual Studio a pro vývojáře, kteří chtějí získat další informace o navigaci v sadě Visual Studio relace ladění. To se nezabývá techniky ladění samotný. Metody ve vzorovém kódu slouží pouze k předvedení ladění postupů popsaných v tomto tématu. Metody nepoužívají osvědčených postupů návrhu aplikace nebo funkce. Ve skutečnosti rychle zjistíte, že metody a vlastní aplikaci a není vhodné použít co nejvíce všeho vůbec.

 Části tohoto rychlého startu byly navržené jako jako nezávislé, jako je to možné, takže můžete přeskočit všechny části, která obsahuje informace, které jste už obeznámení s. Také se nejsou potřebné k vytvoření ukázkové aplikace; ale doporučujeme ho a provedli proces co nejjednodušší.

 **Ladicí program klávesové zkratky.** Navigace ladicího programu Visual Studio je optimalizovaná pro myš a klávesnici. Celá řada kroků v tomto tématu patří klávesové zkratky nebo klávesovou zkratku v kulatých závorek příspěvku. Například (klávesnice: F5) označuje zadáním klávesu F5, spustí nebo pokračuje v provádění ladicího programu.

## <a name="in-this-topic"></a>V tomto tématu
 Můžete získat informace tom, jak:

-   [Vytvoření ukázkové aplikace](#BKMK_CreateTheApplication)

-   [Nastavit a spusťte zarážku, krokování s vnořením do metody a prozkoumejte data programu](#BKMK_StepInto)

-   [Krokovat do, nad a z metody](#BKMK_StepIntoOverOut)

-   [Nastavení podmíněné zarážky, přechod ke kurzoru a vizualizovat proměnné](#BKMK_ConditionCursorVisualize)

-   [Upravit a pokračovat, obnovení z výjimky](#BKMK_EditContinueRecoverExceptions)

##  <a name="BKMK_CreateTheApplication"></a> Vytvoření ukázkové aplikace
 Ladění je kód, takže ukázková aplikace používá rozhraní framework aplikace Windows Store pouze k vytvoření zdrojového souboru, ve kterém uvidíte navigace ladicí relaci jak funguje a jak zkontrolovat a změnit stav programu. Veškerý kód, který bude volat funkce je volána z konstruktoru hlavní stránky. žádné ovládací prvky jsou přidány a jsou zpracovány žádné události.

 **Vytvořte výchozí aplikaci C# Windows Store.** Otevřít Visual Studio. Na domovské stránce, zvolte **nový projekt** odkaz. V dialogovém okně Nový projekt, zvolte **Visual C#** v **nainstalováno** seznamu a klikněte na tlačítko **Windows Store**. V seznamu šablon projektu vyberte **aplikace**. Visual Studio vytvoří nová řešení a projektu a zobrazí MainPage.xaml návrháře a editoru kódu XAML.

 **Otevřete zdrojový soubor MainPage.xaml.cs.** Klikněte pravým tlačítkem na libovolné místo v editoru XAML a zvolte **zobrazit kód**. Použití modelu code-behind souboru MainPage.xaml.cs se zobrazí. Všimněte si, že pouze jednu metodu `MainPage()` konstruktoru, je uveden v souboru.

 **Nahraďte konstruktoru MainPage ukázkový kód.** Delete – metoda MainPage(). Na tomto odkazu: [ladicího programu vzorový kód pro navigaci (Xaml a C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)a potom zkopírujte kód uvedený v části jazyka C# do schránky. (Zvolte **zpět** v prohlížeči nebo prohlížeč nápovědy se vraťte na tuto stránku rychlý start.) V editoru sady Visual Studio, vložte kód `partial class MainPage` bloku. Zvolte kombinaci kláves CTRL + s uložte soubor.

 Teď můžete sledovat, spolu s příklady v tomto tématu.

##  <a name="BKMK_StepInto"></a> Nastavit a spusťte zarážku, krokování s vnořením do metody a prozkoumejte data programu
 Nejběžnější způsob spuštění ladicí relace je zvolit **spustit ladění** z **ladění** nabídce (klávesnice: F5). Provádění začne a pokračuje, dokud není dosaženo zarážky, můžete ručně pozastavení provádění, dojde k výjimce nebo ukončení aplikace.

 Když je spuštění pozastaveno v ladicím programu, můžete zobrazit hodnotu active proměnné v popisu dat podržením ukazatele myši nad proměnnou. Můžete také otevřít místní hodnoty a automatické hodnoty windows zobrazíte seznam aktivních proměnné a jejich aktuální hodnoty. Přidání jednoho nebo více proměnných do okna umožňuje sledovat, se můžete soustředit na hodnotu proměnné, protože aplikace pokračuje v provádění kódu.

 Po pozastavení provádění aplikace (označuje se také rozdělení do ladicího programu), řídit způsob, jakým je provést zbytek kódu programu. Můžete dál řádek po řádku, přechod z volání metody, metody nebo volané metody lze provést v jediném kroku. Tyto postupy jsou volány krokování aplikace. Můžete také obnovit standardní provádění, spuštěnou aplikaci až k další zarážce, kterou jste nastavili, nebo na řádku tam, kam jste umístili kurzor. Můžete zastavit ladicí relaci v každém okamžiku. Ladicí program je určena k provedení nezbytných operací čištění a ukončí provádění.

### <a name="example-1"></a>Příklad 1
 V tomto příkladu můžete nastavit zarážku v konstruktoru MainPage v souboru MainPage.xaml.cs, Krokovat s vnořením první metoda, zobrazení hodnot proměnných a poté zastavte ladění.

 **Nastavte zarážku.** Nastavit zarážku na příkaz `methodTrack = "Main Page";` v konstruktoru MainPage. Zvolte řádek na vystínovanou ovládací prvek editoru zdrojového kódu (klávesnice: Umístěte kurzor na řádku a stiskněte klávesu F9).

 ![Krokovat s vnořením](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Ikona zarážky se zobrazí ve hřbetu.

 **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5).

 Aplikace začne spouštět a pozastaví provádění bezprostředně před příkaz, ve kterém můžete nastavit zarážku. Aktuální ikona řádku na ovládací prvek určuje umístění a aktuální příkaz je zvýrazněn.

 ![Nastavit zarážku](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Nyní jsou v řízení spouštění aplikace a můžete zkontrolovat stav programu krocích příkazy programu.

 **Krokovat s vnořením metody.** Na **ladění** nabídce zvolte **Krokovat s vnořením** (klávesnice: F11).

 ![Aktuální řádek](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Všimněte si, že ladicí program se přesune na další řádek, který je volání metody test1. Zvolte Krokovat s vnořením znovu. Ladicí program se přesune na vstupní bod metodu test1. To znamená, že metoda byl načten v zásobníku volání a byla přidělena paměť pro místní proměnné.

 Když vejdete do jediného řádku kódu provede ladicí program jednu z následujících akcí:

- Pokud další příkaz není voláním funkce ve vašem řešení, ladicí program provede příkaz, přesune na další příkaz a následně pozastaví provádění kódu.

- Pokud je příkaz voláním funkce ve vašem řešení, ladicí program se přesune na vstupní bod volané funkce a následně pozastaví provádění kódu.

  Přejděte ke kroku na příkazy test1, dokud nedosáhnete výstupním bodě. Ladicí program zvýrazní uzavírací složenou závorku metody.

  **Zkontrolujte hodnoty proměnných v datových tipech.** Když myší najedete myší název proměnné, zobrazí se název, hodnotu a typ proměnné v popisu dat.

  ![Ladicí program datového tipu](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Najeďte myší proměnnou `a`. Poznámka: Zadejte název, hodnotu a data. Najeďte myší proměnnou `methodTrack`. Zadejte název, hodnotu a data znovu, mějte na paměti.

  **Zkontrolujte hodnoty proměnné v okně místních hodnot.** Na **ladění** nabídky, přejděte k **Windows**a klikněte na tlačítko **lokální**. (Klávesnice: Alt + 4).

  ![Okno místních hodnot](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Lokální windows je stromové zobrazení parametry a proměnné, funkce. Vlastnosti proměnné objektu jsou podřízené uzly samotného objektu. `this` Proměnná je skrytý parametr v každé metody objektu, který představuje samotného objektu. V tomto případě představuje třídu MainPage. Protože `methodTrack` je členem typu třídy, jeho hodnota a data MainPage jsou uvedeny v řádku pod `this`. Rozbalte `this` uzlu zobrazíte `methodTrack` informace.

  **Přidáte kukátko methodTrack proměnné.** `methodWatch` v rámci tohoto rychlého startu k zobrazení metod volá se v příkladech se používá proměnná. Aby bylo snazší zobrazit hodnotu proměnné, přidejte ho do okna kukátka. Klikněte pravým tlačítkem na název proměnné v okně místních hodnot a klikněte na tlačítko **Přidat kukátko**.

  ![Okno kukátka](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Podívejte se na více proměnných v okně kukátko. Hodnoty proměnných sledovaných, jako jsou hodnoty v oknech místní hodnoty a datový tip windows, se aktualizují pokaždé, když je spuštění pozastaveno. K oknu kukátka můžete také přidat proměnné z editoru kódu. Vyberte proměnnou ke sledování, klikněte pravým tlačítkem a pak zvolte **Přidat kukátko**.

##  <a name="BKMK_StepIntoOverOut"></a> Krokovat do, nad a z metody
 Na rozdíl od krokování s vnořením do metody volané nadřazené metody, krokování přes metody spustí metodu podřízené a následně pozastaví provádění kódu ve volání metody jako nadřazený obnoví. Pokud jste obeznámeni s způsob, jak metoda funguje a si jisti, že jeho spuštění nebude mít vliv na problém, který se objeví prošetřovaná může Krokovat přes metodu.

 Krokování přes jediného řádku kódu, které nebude obsahovat volání metody spustí řádku stejně jako krokování s vnořením do řádku.

 Krokování mimo metodu podřízené pokračuje v provádění metody a následně pozastaví provádění po její volání metody vrací metoda. Až zjistíte, že zbytek funkce není důležité, může být vystoupení ze dlouhé funkce.

 Krokování přes i krokování ve funkci spuštění funkce.

 ![Krok do, nad a z metody](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Příklad 2
 V tomto příkladu můžete krokovat do, nad a z metod.

 **Volání metody priklad2 v konstruktoru MainPage.** Upravte konstruktor MainPage a nahraďte tento řádek `methodTrack = String.Empty;` s `Example2();`.

 ![Volání metody priklad2 z metody ukázka](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5). Ladicí program pozastaví provádění kódu na zarážce.

 **Krokovat přes řádek kódu.** Na **ladění** nabídce zvolte **Krokovat s přeskočením** (klávesnice: F10). Ladicí program provede `methodTrack = "MainPage";` příkaz stejným způsobem jako vstup do příkazu.

 **Krokování s vnořením priklad2 a Example2_A.** Stisknutím klávesy F11 Krokovat s vnořením metodu příklad 2. Přejděte ke kroku na priklad2 příkazy, dokud se nedostanete na řádku `int x = Example2_A();`. Znovu krokování s vnořením do tohoto řádku přesunout na vstupní bod Example2_A. Krokovat s vnořením každý příkaz Example2_A postupně se vraťte do priklad2 i nadále.

 ![Priklad2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Krokovat přes funkci.** Všimněte si, že se na další řádek v test2, `int y = Example2_A();` je v podstatě stejný jako předchozí řádek. Můžete bezpečně Krokovat přes tento řádek. Pro přesun z opětovné priklad2 do této druhé volání Example2_A stiskněte klávesu F10. Zvolte F10 Krokovat přes tuto metodu. Všimněte si, že `methodTrack` řetězec označuje metodu Example2_A spustil dvakrát. Můžete si všimnout, že ladicí program okamžitě přesune na další řádek. Nepozastaví zpracování na bod priklad2 obnoví.

 **Krok z funkce.** Stisknutím klávesy F11 Krokovat s vnořením Example2_B metody. Všimněte si, že není příliš neliší od Example2_A Example2_B. Chcete-li mimo metodu, zvolte **Krokovat s Vystoupením** na **ladění** nabídce (klávesnice: Shift + F11). Všimněte si, že `methodTrack` proměnné označuje, že byl proveden Example2_B a že ladicí program vrátil do bodu, kde priklad2 obnoví.

 **Zastavte ladění.** V nabídce ladit, zvolte Ukončit ladění (klávesnice: Shift + F5). Ukončí relaci ladění.

##  <a name="BKMK_ConditionCursorVisualize"></a> Nastavení podmíněné zarážky, přechod ke kurzoru a vizualizovat proměnné
 Podmíněné zarážky Určuje podmínku, která způsobí, že ladicí program k pozastavení provádění. Podmínka je zadaný libovolný výraz kód, který může být vyhodnocen jako true nebo false. Můžete například použít podmíněné zarážky prozkoumat stav programu v často volaných metodu pouze v případě, že proměnné dosáhne určité hodnoty.

 Provést do pozice kurzoru je třeba nastavit jednorázové zarážku. Když je spuštění pozastaveno, můžete vybrat řádek ve zdroji a obnovit spuštění, dokud nebude dosaženo vybraný řádek. Například můžete být krokování smyčky v metodě a určit, že kód ve smyčce pracuje správně. Místo procházení každé iteraci smyčky, můžete spustit na kurzor, který je umístěn po provedení smyčky je.

 V některých případech je obtížné zobrazíte hodnotu proměnné v řádku popisu dat nebo okně proměnné. Ladicí program může zobrazit řetězce, HTML a Xml ve vizualizéru text, který představuje formátovaný zobrazení hodnoty v posuvného okna.

### <a name="example-3"></a>Příklad 3
 V tomto příkladu je nastavit podmíněné zarážky zarážku konkrétní iteraci smyčky a pak spustit na kurzor, který je umístěn po smyčce. Můžete také zobrazit hodnotu proměnné v vizualizátor textu.

 **Volání metody Example3 v konstruktoru MainPage.** Upravte konstruktor MainPage a nahraďte tento řádek `methodTrack = String.Empty;` řádek `Example3();`.

 ![Volání z metody ukázka Example3](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Spusťte zarážku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5). Ladicí program pozastaví provádění na zarážku v metodě MainPage.

 **Krokování s vnořením do metody Example3.** Zvolte **Krokovat s vnořením** na **ladění** nabídce (klávesnice: F11) přesunout na vstupní bod metodu Example3. Krokování do metody, dokud se mají provést iteraci smyčky jednu nebo dvě z pokračovat `for` bloku. Všimněte si, že ho by vám neměl zabrat dlouhou dobu, chcete-li si všechny 1000 iterací.

 **Nastavení podmíněné zarážky.** V levém hřbetu okna kódu, klikněte pravým tlačítkem na řádku `x += i;` a klikněte na tlačítko **podmínku**. Zvolte **podmínku** zaškrtněte políčko a potom zadejte `i == 500;` v textovém poli. Zvolte **platí** možnost a vyberte **OK**. Zarážky můžete ke kontrole hodnoty v 500th iterace `for` smyčky.

 ![Dialogové okno podmínky zarážky](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Ikona podmíněné zarážky může identifikovat podle jeho bílé mezi.

 ![Podmíněné zarážky](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Spusťte zarážku.** V nabídce ladit, vyberte pokračovat (klávesnice: F5). V okně místních hodnot, ujistěte se, že aktuální hodnotu `i` je 500. Všimněte si, že proměnná `s` je vyjádřena jako jeden řádek a je mnohem delší než časový interval.

 **Vizuální proměnnou s řetězcem.** Klikněte na ikonu lupy v **hodnotu** sloupec `s`.

 Zobrazí se okno Vizualizátor textu a hodnotou řetězce je zobrazen jako Víceřádkový řetězec.

 **Přechod ke kurzoru.** Klikněte pravým tlačítkem na řádku `methodTrack += "->Example3";` a klikněte na tlačítko **spustit ke kurzoru** (klávesnice: Přesuňte kurzor na řádek; CTRL + F10). Ladicí program dokončí iterací smyčky a následně pozastaví provádění kódu na řádku.

 **Zastavte ladění.** V nabídce ladit, zvolte Ukončit ladění (klávesnice: Shift + F5). Ukončí relaci ladění.

##  <a name="BKMK_EditContinueRecoverExceptions"></a> Upravit a pokračovat, obnovení z výjimky
 V některých případech až proniknout do kódu v ladicím programu sady Visual Studio budete mít příležitost změnit hodnoty proměnných a dokonce i logics příkazy. Tato funkce je volána upravit a pokračovat.

 Upravit a pokračovat může být zvláště užitečné při rozdělit na výjimku. Namísto nutnosti zastavit a znovu spusťte ladění dlouhé a potřebný postup výjimce vyhnout, můžete "vrátit se zpět" výjimka, která má přesunout zpracování do bodu bezprostředně před došlo k výjimce a změňte problematický proměnné nebo příkazu a Pokračujte s aktuální relaci ladění ve stavu, který nevyvolá výjimku.

 I když můžete použití operace upravit a pokračovat v nejrůznějších situacích, určité podmínky, které nechcete upravit a pokračovat je obtížné určit, protože podmínky, závisí na programovací jazyk, aktuální stav do zásobníku programu a možnosti ladicího programu ke změně stavu bez poškozující proces. Nejlepší způsob, jak zjistit, jestli se o změnu úpravy podporuje je jenom vyzkoušet; ladicí program umožňuje okamžitě vědět, pokud se tato změna není podporována.

### <a name="example-4"></a>Příklad 4:
 V tomto příkladu spustit ladicí program na výjimku, rewind výjimku, opravte logiku metody a potom změňte hodnotu proměnné tak, že můžete pokračovat v provádění metody.

 **Volání metody Example4 v konstruktoru MainPage.** Upravte konstruktor MainPage() a nahraďte tento řádek `methodTrack = String.Empty;` řádek `Example4();`.

 ![Volání z metody ukázka Example4](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Spusťte na výjimku.** Spuštění relace ladění zvolením **spustit ladění** na **ladění** nabídce (klávesnice: F5). Stisknutím klávesy F5 pokračovat v provádění. Ladicí program přeruší provádění při výjimce v metodě Example4 a zobrazí se dialogové okno výjimky.

 ![Dialogové okno výjimky](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Změňte programovou logiku.** Je zřejmé, že se chybu v `if` podmínku: hodnota `x` by měla být změněna při `x` rovná 0, ne v případě `x` není rovna hodnotě nula. Zvolte **přerušit** opravit logiku metody. Při pokusu o úpravy řádku se zobrazí jiné dialogové okno.

 ![Upravit a pokračovat – dialogové okno](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Zvolte **upravit** a potom změňte řádek `if (x != 0)` k `if (x == 0)`. Ladicí program se uchovávají změny programovou logiku ke zdrojovému souboru.

 **Změňte hodnotu proměnné.** Zkoumat hodnoty `x` v popisu dat nebo v okně místních hodnot. Stále je 0 (nula). Pokud se pokusíte o provedení příkazu, která způsobila původní výjimku, ho pouze vyvolá znovu. Můžete změnit hodnotu `x`. V okně místních hodnot, dvakrát klikněte **hodnotu** sloupec **x** řádek. Změňte hodnotu od 0 do 1.

 ![Úprava hodnoty v okně místních hodnot](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Stisknutím klávesy F11 Krokovat s vnořením příkazu, který dříve došlo k výjimce. Všimněte si, že řádek se spustí bez chyby. Zvolte F11 znovu.

 **Zastavte ladění.** Na **ladění** nabídce zvolte **Zastavit ladění** (klávesnice: Shift + F5). Ukončí relaci ladění.

## <a name="see-also"></a>Viz také
 [Spuštění ladicí relace (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [aktivační události pozastavení, obnovení a událostí na pozadí pro Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [ladění aplikací v sadě Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
