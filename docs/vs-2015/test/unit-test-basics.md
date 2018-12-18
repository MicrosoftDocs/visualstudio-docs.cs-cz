---
title: Základní informace o testování částí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.UnitTest.CreateUnitTest
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 29
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62a451b1004a6e93980d7fb594781e661b06246d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863618"
---
# <a name="unit-test-basics"></a>Základní informace o testech jednotek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zkontrolujte, že je váš kód funguje podle očekávání tím vytváření a spouštění testování částí. Je volána testování, protože můžete rozdělit podle funkce programu do samostatných testovatelného chování, které můžete testovat jako jednotlivé *jednotky*. Visual Studio Test Explorer poskytuje flexibilní a efektivní způsob, jak spustit testování částí a zobrazit jejich výsledky v sadě Visual Studio. Visual Studio nainstaluje testování části Microsoft rozhraní pro spravovaný a nativní kód. Použití *jednotkových testů* vytvořit testy jednotek, je spustit a ohlásí výsledky těchto testů. Pokud provedete změny k testování, že váš kód stále pracuje správně testů jednotek spusťte znovu. Pokud používáte Visual Studio Enterprise, můžete spustit testy automaticky po každém sestavení.  
  
 Testování částí má největší vliv na kvalitu kódu, pokud je to nedílná součást pracovního postupu vývoje software. Jakmile napíšete funkce nebo další blok kódu aplikace, vytvořte testy jednotek, které ověří chování kódu v reakci na standard, hranice a správné případy vstupních dat a kontrolují žádné explicitní nebo implicitní předpoklady v kódu. S *vývoj řízený testy*, vytvořte jednotkové testy před napsáním kódu, proto použijete jako dokumentace k návrhu a funkční specifikace testů jednotek.  
  
 Můžete rychle vytvořit projekty testů a testovací metody v kódu nebo ručně vytvořit testy podle potřeby. Když pomocí funkce IntelliTest dá prozkoumat kód .NET, můžete vygenerovat testovací data a sady testování částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí. Zjistěte, jak [generování testů jednotek pro kód](http://msdn.microsoft.com/library/dn823749.aspx).  
  
 Průzkumník testů také můžete spustit třetích stran a open source rozhraní pro testování částí, které mají implementované rozhraní doplněk Průzkumníka testů. Můžete přidat řadu tyto architektury prostřednictvím Správce rozšíření sady Visual Studio a v galerii sady Visual Studio. Zobrazit [nainstalovat rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)  
  
-   [Rychlé starty](#BKMK_Quick_starts)  
  
-   [Příklad MyBank řešení](#BKMK_The_MyBank_Solution_example)  
  
-   [Vytvoření projektů jednotkových testů a testovací metody](#BKMK_Creating_the_unit_test_projects)  
  
-   [Zápis testů](#BKMK_Writing_your_tests)  
  
-   [Spustit testy v Průzkumníku testů](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Spustit a zobrazit testy](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)  
  
##  <a name="BKMK_Unit_testing_overview"></a> Přehled testování jednotek  
  
###  <a name="BKMK_Quick_starts"></a> Rychlé starty  
 Úvod do testování částí, která vás přesměruje přímo do psaní kódu naleznete v těchto tématech:  
  
-   [Návod: Vytváření a spouštění testů částí pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)  
  
-   [Rychlý začátek: Vývoj řízený testy s použitím Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)  
  
-   [Testování částí nativního kódu pomocí Průzkumníka testů](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)  
  
##  <a name="BKMK_The_MyBank_Solution_example"></a> Příklad MyBank řešení  
 V tomto tématu, používáme vývoj fiktivní aplikaci s názvem `MyBank` jako příklad. Není nutné skutečný kód a postupujte v tomto tématu vysvětlené v částech. Testovací metody jsou napsané v jazyce C# a zobrazí s použitím Microsoft Unit Testing Framework pro spravovaný kód, ale koncepty snadno přenést do jiných jazyků a architektur.  
  
 ![Řešení MyBank](../test/media/ute-mybanksolution.png "UTE_MyBankSolution")  
  
 Naše první pokus o návrhu `MyBank` aplikace obsahuje komponentu účtů, která představuje individuálního účtu a jeho transakce se banky a databáze komponenty, která představuje funkci, která agregují a spravovat samostatné účty.  
  
 Vytvoříme `MyBank` řešení, které obsahuje dva projekty:  
  
- `Accounts`  
  
- `BankDb`  
  
  Naše první pokus o návrhu `Accounts` projektu obsahuje třídy pro uložení základní informace o účtu, rozhraní, které určuje běžné funkce jakýkoli typ účtu, jako je uložení a odebírá z účtu a třída prostředků odvozený z rozhraní, která představuje běžný účet. Můžeme začít projekty účty tak, že vytvoříte následující zdrojové soubory:  
  
- `AccountInfo.cs` definuje základní informace o účtu.  
  
- `IAccount.cs` definuje standardní `IAccount` rozhraní pro účet, včetně metod pro uložení a odebrání prostředků z účtu a k načtení zůstatek na účtu.  
  
- `CheckingAccount.cs` obsahuje `CheckingAccount` třídu, která implementuje `IAccounts` rozhraní pro běžný účet.  
  
  Víme z prostředí, že tento jednou z věcí, které musíte provést stažení z účtu kontroluje se ujistěte, že vybíraná hodnota je menší než zůstatek na účtu. Proto jsme přepsat `IAccount.Withdaw` metoda `CheckingAccount` s metodou, která kontroluje pro tuto podmínku. Metoda může vypadat takto:  
  
```csharp  
  
public void Withdraw(double amount)  
{  
    if(m_balance >= amount)  
    {  
        m_balance -= amount;  
    }  
    else  
    {  
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")  
    }  
}  
  
```  
  
 Když teď máme nějaký kód, je čas pro testování.  
  
##  <a name="BKMK_Creating_the_unit_test_projects"></a> Vytvoření projektů jednotkových testů a testovací metody  
 Je často rychlejší generování projektu testování částí a zástupných procedur testu jednotek z vašeho kódu. Nebo můžete vytvořit projekt testů jednotek a testů ručně v závislosti na vašich požadavcích.  
  
 **Generovat projekt testování částí a zástupné procedury pro testování částí**  
  
1. V okně editoru kódu, klikněte pravým tlačítkem a zvolte **vytvořit testy jednotek** v místní nabídce.  
  
    ![V okně editoru zobrazit kontextovou nabídku](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")  
  
2. Klikněte na OK přijmete výchozí hodnoty pro vytváření testů jednotek nebo změnu hodnoty použité k vytvoření a název jednotky testování projektů a testy jednotek. Můžete vybrat kód, který se ve výchozím nastavení přidá do metody jednotkového testu.  
  
    ![Pravé&#45;klikněte v editoru a zvolte Vytvořit testy jednotek](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")  
  
3. Zástupné procedury testu jednotek se vytvoří v nový projekt testů jednotek pro všechny metody ve třídě.  
  
    ![Jednotkové testy jsou vytvořeny](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")  
  
4. Teď přejděte k další postupy [přidejte kód do metody jednotkového testu](#BKMK_Writing_your_tests) smysluplné testování částí a všechny další jednotky testů, které chcete přidat do důkladně otestujte svůj kód.  
  
   **Vytvoření testování částí projektu a testy jednotek ručně**  
  
   Projekt testování částí obvykle zrcadlí strukturu projektu jeden kód. V tomto příkladu MyBank přidejte dva projekty testů jednotek s názvem `AccountsTests` a `BankDbTests` k `MyBanks` řešení. Názvy projektů testů libovolného, ale přijetí standardní zásady vytváření názvů je vhodné.  
  
   **Chcete-li přidat projekt do řešení pro testování částí:**  
  
5. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu** (klávesnice: Ctrl + Shift + N).  
  
6. V dialogovém okně Nový projekt rozbalte **nainstalováno** uzlu, vyberte jazyk, který chcete použít pro testovací projekt a pak zvolte **testování**.  
  
7. Chcete-li použít jeden z rozhraní pro testování částí Microsoft, zvolte **projekt testů jednotek** ze seznamu šablon projektu. V opačném případě vyberte šablonu projektu jednotky testů, který chcete použít. K testování `Accounts` projektu v našem příkladu by projekt pojmenujte `AccountsTests`.  
  
   > [!WARNING]
   >  Ne všechna rozhraní pro testování částí třetích stran a open source poskytují šablony projektu sady Visual Studio. Informace o vytvoření projektu naleznete v dokumentu framework.  
  
8. V projektu testování částí přidejte odkaz na projekt kódu v rámci testu v našem příkladu do projektu účty.  
  
    Chcete-li vytvořit odkaz na projekt kódu:  
  
   1.  Vyberte projekt v Průzkumníku řešení.  
  
   2.  Na **projektu** nabídce zvolte **přidat odkaz**.  
  
   3.  V dialogovém okně Správce odkazů otevřete **řešení** uzlu a zvolte **projekty**. Vyberte název projektu kódu a zavřete dialogové okno.  
  
   Každý projekt jednotkového testu obsahuje třídy, které zrcadlí názvy tříd v projektu kódu. V našem příkladu `AccountsTests` projekt bude obsahovat následující třídy:  
  
-   `AccountInfoTests` Třída obsahující metody jednotkového testu pro `AccountInfo` třídy v `BankAccount` projektu  
  
-   `CheckingAccountTests` Třída obsahující metody jednotkového testu pro `CheckingAccount` třídy.  
  
##  <a name="BKMK_Writing_your_tests"></a> Zápis testů  
 Testy jednotek, který používáte a IntelliSense ve Visual Studio vás provede zápis kódu pro testování částí pro kód projektu. Spustit v Průzkumníku testů, většina architektur vyžaduje přidání specifických atributů k identifikaci metody jednotkového testu. Rozhraní také poskytují způsob – obvykle prostřednictvím Assert – příkazy nebo atributy metody – označuje, zda má testovací metoda předané nebo se nezdařilo. Ostatní atributy Identifikujte volitelné nastavení metody, které jsou při inicializaci třídy a před každou metodu testu a metody jejich vyřazování z provozu, které jsou spuštěny po jednotlivých zkušebních metod a zničen třídy.  
  
 Vzor AAA (Assert uspořádat, Act) je běžný způsob psaní testů jednotek pro metody v rámci testu.  
  
- **Uspořádat** část metodu testovací jednotky inicializuje objekty a nastaví hodnotu data, která se předá metodě v rámci testu.  
  
- **Act** část volá metodu v rámci testu s uspořádané parametry.  
  
- **Assert** části ověřuje, že akce testované metody chová podle očekávání.  
  
  K testování `CheckingAccount.Withdraw` metoda našeho příkladu jsme napsali dva testy: ten, který ověřuje standardní chování metody a jednu, která ověřuje, že se nepodaří stažení větší než zůstatek na účtu. V `CheckingAccountTests` třídy, jsme přidejte následující metody:  
  
```csharp  
[TestMethod]  
public void Withdraw_ValidAmount_ChangesBalance()  
{  
    // arrange  
    double currentBalance = 10.0;  
    double withdrawal = 1.0;  
    double expected = 9.0;  
    var account = new CheckingAccount("JohnDoe", currentBalance);  
    // act  
    account.Withdraw(withdrawal);  
    double actual = account.Balance;  
    // assert  
    Assert.AreEqual(expected, actual);  
}  
  
[TestMethod]  
[ExpectedException(typeof(ArgumentException))]  
public void Withdraw_AmountMoreThanBalance_Throws()  
{  
    // arrange  
    var account = new CheckingAccount("John Doe", 10.0);  
    // act  
    account.Withdraw(20.0);  
    // assert is handled by the ExpectedException  
}  
  
```  
  
 Všimněte si, že `Withdraw_ValidAmount_ChangesBalance` používá explicitní `Assert` příkaz k určení, zda testovací metoda projde nebo selže, zatímco `Withdraw_AmountMoreThanBalance_Throws` používá `ExpectedException` atribut k určení úspěšnosti testovací metody. Pod pokličkou zabalí rozhraní testování částí testovacích metod v příkazech v bloku try/catch. Ve většině případů Pokud je výjimka zachycena, testovací metoda selže a výjimka bude ignorována. `ExpectedException` Atribut způsobí, že metoda testu předat, pokud je vyvolána Zadaná výjimka.  
  
 Další informace o rozhraní testování částí Microsoft naleznete v následujících tématech:  
  
-   [Zápis testů částí pro rozhraní .NET Framework s infrastrukturou pro testování částí Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Zápis testů jednotek pro C/C++ s infrastrukturou testování částí Microsoft Unit Testing Framework pro C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)  
  
## <a name="set-timeouts-for-unit-tests"></a>Nastavit vypršení časového limitu pro testování částí  
 Nastavení časového limitu na jednotlivé testovací metody:  
  
```csharp  
[TestMethod]  
[Timeout(2000)]  // Milliseconds  
public void My_Test()  
{ ...  
}  
```  
  
```vb  
  
```  
  
 Nastavit časový limit pro maximální povolený počet:  
  
```csharp  
[TestMethod]  
[Timeout(TestTimeout.Infinite)]  // Milliseconds  
public void My_Test ()  
{ ...  
}  
```  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Spustit testy v Průzkumníku testů  
 Když sestavíte testovací projekt, testy se zobrazí v Průzkumníku testů. Pokud se nezobrazí Průzkumník testů, zvolte **testovací** v nabídce sady Visual Studio, zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.  
  
 ![Průzkumník testu jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Při spuštění, zápisu a znovu spustit testy, zobrazuje výchozí zobrazení Průzkumníka testů výsledky ve skupinách **neúspěšné testy**, **úspěšné testy**, **přeskočené testy** a  **Nespuštěné testy**. Můžete použít skupiny záhlaví otevřete zobrazení, které se zobrazí všechny testy v této skupině.  
  
 Můžete také filtrovat testy ve všech zobrazeních odpovídající text do vyhledávacího pole na globální úrovni nebo výběrem jedné z předdefinovaných filtrů. Kdykoli můžete spustit libovolných vybraných testů. Výsledky testovacího běhu se okamžitě zřejmý v panel úspěšný/selhání v horní části okna Průzkumníka. Podrobnosti výsledku testu metody se zobrazí, když vyberete testu.  
  
###  <a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a> Spustit a zobrazit testy  
 Panel nástrojů Průzkumník testů umožňuje zjišťovat, uspořádání a spuštění testů, které vás zajímají.  
  
 ![Spuštění testů z panelu nástrojů Průzkumník testování](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
 Můžete zvolit **spustit všechny** chcete spustit všechny testy, nebo zvolte **spustit** vybrat podmnožinu testů ke spuštění. Po spuštění sady testů zobrazí se souhrn testovacího běhu v dolní části okna Průzkumníka testů. Vyberte test, chcete-li zobrazit podrobnosti o testu v dolním podokně. Zvolte **otevřít Test** v místní nabídce (klávesnice: F12) Chcete-li zobrazit zdrojový kód pro vybraný test.  
  
 Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute-parallelicon-small.png "UTE_parallelicon malé") přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.  
  
###  <a name="BKMK_Running_tests_after_every_build"></a> Spustit testy po každém sestavení  
  
> [!WARNING]
>  Spuštění testů jednotky po každém sestavení je podporováno pouze v sadě Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Spustit po sestavení](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Chcete-li spouštět testy jednotek po každém místním sestavení, zvolte **testovací** ve standardní nabídce zvolte **spustit testy po sestavení** na panelu nástrojů Průzkumník testů.|  
  
###  <a name="BKMK_Filtering_and_grouping_the_test_list"></a> Filtr a seskupení seznamu testů  
 Pokud máte velký počet testů, můžete zadat v Průzkumníku testů vyhledávacího pole filtrovat seznam podle zadaného řetězce. Můžete omezit další výběrem ze seznamu filtrů filtr události.  
  
 ![Hledat filtr kategorií](../test/media/ute-searchfilter.png "UTE_SearchFilter")  
  
|||  
|-|-|  
|![Tlačítko Test Explorer skupiny](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Chcete-li seskupit podle kategorie testů, zvolte **Group** tlačítko.|  
  
 Další informace najdete v tématu [spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)  
  
## <a name="qa"></a>FUNKCE Q &AMP; A  
 **Otázka: Jak mohu ladit testy jednotek?**  
  
 **Odpověď:** pomocí Průzkumníka testů ke spuštění relace ladění pro testy. Krokování kódu s ladicím programem Visual Studio bez problémů přejdete vpřed a zpět mezi testováním částí a testovaný projekt. Spuštění ladění:  
  
1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.  
  
   > [!NOTE]
   >  Vzhledem k tomu, že zkušební metody lze spustit v libovolném pořadí, nastavte zarážky v všechny testovací metody, které chcete ladit.  
  
2. V Průzkumníku testů vyberte testovací metody a pak zvolte **ladit vybrané testy** z místní nabídky.  
  
   Přečtěte si další podrobnosti o [ladění testů jednotek](../debugger/debugging-in-visual-studio.md).  
  
   **Otázka: Pokud používám TDD, postup generování kódu z mé testy?**  
  
   **Odpověď:** IntelliSense použít ke generování třídy a metody v kódu projektu. Napíšete příkaz v testovací metodě, která volá třída nebo metoda, kterou chcete vygenerovat a pak otevřete nabídku technologie IntelliSense v rámci volání. Pokud je volání konstruktoru nové třídy, zvolte **generovat nový typ** v nabídce a postupujte podle průvodce a vložte třídy do projektu kódu. Pokud je volání metody, zvolte **generovat novou metodu** z nabídky technologie IntelliSense.  
  
   ![Metoda se zakázaným inzerováním Intellisense nabídka Generovat](../test/media/ute-generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")  
  
   **Dotaz: lze vytvořit testy jednotek, neměl zabrat víc kopií dat jako vstup pro spuštění testu?**  
  
   **Odpověď:** Ano. *Test řízený daty metody* umožní otestovat rozsah hodnot s testovací metodou jednu jednotku. Použití `DataSource` atribut testovací metody, která určuje zdroj dat a tabulky, který obsahuje hodnoty proměnné, které chcete testovat.  V těle metody přiřazují hodnoty řádků do proměnných pomocí `TestContext.DataRow[` *Názevsloupce* `]` indexeru.  
  
> [!NOTE]
>  Tyto postupy platí pouze pro testovací metody, které zapisují pomocí rozhraní pro testování jednotek Microsoft pro spravovaný kód. Pokud používáte jiné rozhraní, najdete v dokumentaci rozhraní ekvivalentní funkce.  
  
 Předpokládejme například, můžeme přidat zbytečné způsob `CheckingAccount` třídu, která má název `AddIntegerHelper`. `AddIntegerHelper` Přidá dvou celých čísel.  
  
 Chcete-li vytvořit test řízený daty pro `AddIntegerHelper` metodě nejprve vytvoříme databázi aplikace Access s názvem `AccountsTest.accdb` a tabulku s názvem `AddIntegerHelperData`. `AddIntegerHelperData` Tabulka definuje sloupce, které chcete zadat prvního a druhého operandu sčítání a ve sloupci k určení očekávaný výsledek. Jsme počet řádků, vyplnit odpovídající hodnoty.  
  
```csharp  
  
[DataSource(  
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",   
    "AddIntegerHelperData"  
)]  
[TestMethod()]  
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()  
{  
    var target = new CheckingAccount();  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.AddIntegerHelper(x, y);  
    Assert.AreEqual(expected, actual);  
}  
  
```  
  
 Atributy metody spustí jednou pro každý řádek v tabulce. Průzkumník testů hlásí selhání testu pro metodu, pokud selžou i všechny iterace. Podokno podrobností výsledky testu pro metodu zobrazuje metodu úspěšného/neúspěšného stav pro každý řádek dat.  
  
 Další informace o [testy jednotek řízené daty](../test/how-to-create-a-data-driven-unit-test.md).  
  
 **Dotaz: lze zobrazit, jak velká část kódu je testována mých testů jednotek?**  
  
 **Odpověď:** Ano. Můžete určit množství kódu, který je skutečně testován prostřednictvím testů jednotky pomocí nástroje pokrytí kódu sady Visual Studio. Jsou podporovány nativní a spravované jazyky a všechna rozhraní pro testování částí, které můžou běžet v rámci testu rozhraní jednotky.  
  
 Můžete spustit pokrytí kódem u vybraných testů nebo u všech testů v řešení. Okno výsledky pokrytí kódu zobrazuje procento bloků kódu produktu, které byly vykonány podle řádku, funkce, třídy, oboru názvů a modulu.  
  
 Chcete-li spustit pokrytí kódu pro testovací metody v řešení, zvolte **testy** v nabídce sady Visual Studio a klikněte na tlačítko **analyzovat pokrytí kódu**.  
  
 Výsledky pokrytí se zobrazí v okně Výsledky pokrytí kódu.  
  
 ![Výsledky pokrytí kódu](../test/media/ute-codecoverageresults.png "UTE_CodeCoverageResults")  
  
 Další informace o [pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .  
  
 **Otázka: jak lze zkušební metody v okně můj kód, který mají vnější závislosti?**  
  
 **Odpověď:** Ano. Pokud máte Visual Studio Enterprise, Microsoft Fakes lze použít s testovacími metodami, které zapisují pomocí rozhraní pro testování částí pro spravovaný kód.  
  
 Microsoft Fakes používá dva přístupy k vytvoření náhradní třídy u externích závislostí.  
  
1. *Zástupné procedury* generovat náhradní třídy odvozené od nadřazené rozhraní cílovou třídu závislostí. Veřejné virtuální metody cílové třídy mohou být nahrazeny metody zástupných procedur.  
  
2. *Překrytí* použít k rozdělení volání cílové metody k metodě náhradní překrytí pro nevirtuální metody instrumentace modulu runtime.  
  
   V oba přístupy pomocí generovaného delegáti volání metody závislostí můžete určit chování, které chcete v testovací metodě.  
  
   Další informace o [izolace metody jednotkového testu s Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
   **Otázka: Mohu použít jiné rozhraní pro testování částí pro vytvoření testů jednotek?**  
  
   **Odpověď:** Ano, postupujte podle těchto kroků [najít a nainstalovat jiná rozhraní Framework](../test/install-third-party-unit-test-frameworks.md). Po restartování sady Visual Studio otevřete řešení k vytvoření testování částí a poté vyberte nainstalované rozhraní tady:  
  
   ![Vyberte jiné nainstalované testování částí](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")  
  
   Vaše zástupné procedury testu jednotek se vytvoří pomocí vybrané architektuře.



