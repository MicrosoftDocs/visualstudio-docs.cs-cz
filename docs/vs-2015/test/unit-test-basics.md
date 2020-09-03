---
title: Základy testování částí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0657fdd846c201b4f9bff4910bdd9fc271c399c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543777"
---
# <a name="unit-test-basics"></a>Základní informace o testování částí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvořením a spuštěním testů jednotek ověřte, zda váš kód funguje podle očekávání. Nazývá se testování částí, protože funkce programu rozdělíte do diskrétního testovatelné chování, které můžete testovat jako jednotlivé *jednotky*. Visual Studio Test Explorer nabízí flexibilní a efektivní způsob, jak spustit testy jednotek a zobrazit jejich výsledky v aplikaci Visual Studio. Visual Studio nainstaluje architektury testování částí společnosti Microsoft pro spravovaný a nativní kód. Pomocí *architektury jednotkového testování* můžete vytvořit testy jednotek, spustit je a ohlásit výsledky těchto testů. Spusťte testy jednotek znovu, když provedete změny a otestujete, zda váš kód stále pracuje správně. Při použití Visual Studio Enterprise můžete testy spouštět automaticky po každém sestavení.

 Testování částí má největší vliv na kvalitu kódu, pokud je nedílnou součástí pracovního postupu vývoje softwaru. Jakmile napíšete funkci nebo jiný blok kódu aplikace, vytvořte testy jednotek, které ověřují chování kódu v reakci na standardní, hranici a nesprávné případy vstupních dat a které kontrolují všechny explicitní nebo implicitní předpoklady, které provádí kód. U *vývoje řízeného testem*vytvoříte testy jednotek před zápisem kódu, takže používáte testy jednotek jako dokumentaci k návrhu i funkční specifikace.

 Můžete rychle vygenerovat testovací projekty a testovací metody z vašeho kódu nebo je ručně vytvořit podle potřeby. Když použijete IntelliTest k prozkoumávání kódu .NET, můžete vygenerovat testovací data a sadu testů jednotek. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí.  Zjistěte, jak [pro svůj kód generovat testy jednotek](https://msdn.microsoft.com/library/dn823749.aspx).

 Průzkumník testů může také spouštět rozhraní a open source testovacích jednotek od třetích stran, které implementovaly rozhraní doplňků Průzkumníka testů. Mnohé z těchto rozhraní můžete přidat prostřednictvím Správce rozšíření sady Visual Studio a galerie sady Visual Studio. Viz [instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md)

- [Rychlé starty](#BKMK_Quick_starts)

- [Příklad řešení MyBank](#BKMK_The_MyBank_Solution_example)

- [Vytváření projektů testování částí a testovacích metod](#BKMK_Creating_the_unit_test_projects)

- [Zápis testů](#BKMK_Writing_your_tests)

- [Spustit testy v Průzkumníku testů](#BKMK_Running_tests_in_Test_Explorer)

- [Spuštění a zobrazení testů](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)

## <a name="unit-testing-overview"></a><a name="BKMK_Unit_testing_overview"></a> Přehled testování částí

### <a name="quick-starts"></a><a name="BKMK_Quick_starts"></a> Rychlé starty
 Úvodní informace o testování částí, které vás zavedou přímo do kódování, najdete v jednom z těchto témat:

- [Návod: Vytváření a spouštění testů částí pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Rychlý začátek: Vývoj řízený testy s použitím Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Testování částí nativního kódu pomocí Průzkumníka testů](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)

## <a name="the-mybank-solution-example"></a><a name="BKMK_The_MyBank_Solution_example"></a> Příklad řešení MyBank
 V tomto tématu budeme používat vývoj fiktivní aplikace označované `MyBank` jako příklad. Nepotřebujete vlastní kód, který by měl postupovat podle vysvětlení v tomto tématu. Testovací metody jsou napsány v jazyce C# a prezentovány pomocí architektury testování částí společnosti Microsoft pro spravovaný kód, ale koncepty lze snadno přenést do jiných jazyků a rozhraní.

 ![Řešení MyBank](../test/media/ute-mybanksolution.png "UTE_MyBankSolution")

 Náš první pokus o návrh `MyBank` aplikace zahrnuje účty komponenty, které představují jednotlivé účty a jejich transakce s bankou, a databázovou komponentu, která představuje funkce pro agregaci a správu jednotlivých účtů.

 Vytvoříme `MyBank` řešení, které obsahuje dva projekty:

- `Accounts`

- `BankDb`

  Náš první pokus o návrh `Accounts` projektu obsahuje třídu pro uchovávání základních informací o účtu, rozhraní, které určuje společné funkce libovolného typu účtu, jako je například ukládání a odvolávání prostředků z účtu, a třídu odvozenou z rozhraní, které představuje kontrolní účet. Projekty účtů zahájíme vytvořením následujících zdrojových souborů:

- `AccountInfo.cs` definuje základní informace o účtu.

- `IAccount.cs` Definuje standardní `IAccount` rozhraní pro účet, včetně metod pro uložení a stažení prostředků z účtu a načtení zůstatku účtu.

- `CheckingAccount.cs` obsahuje `CheckingAccount` třídu, která implementuje `IAccounts` rozhraní pro kontrolní účet.

  Víme od vás, že jedna věc z kontrolního účtu, kterou je potřeba zrušit, je nutné zajistit, aby byla stažená částka menší než zůstatek účtu. Proto jsme `IAccount.Withdaw` metodu v metodě `CheckingAccount` , která kontroluje tuto podmínku, přepsala. Tato metoda může vypadat takto:

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

 Teď, když máme nějaký kód, je čas na testování.

## <a name="create-unit-test-projects-and-test-methods"></a><a name="BKMK_Creating_the_unit_test_projects"></a> Vytváření projektů testování částí a testovacích metod
 Je často rychlejší generovat projekt testování částí a zástupné procedury testu jednotek z vašeho kódu. Nebo můžete zvolit, že se má projekt testování jednotek a testy vytvořit ručně v závislosti na vašich požadavcích.

 **Generovat projekt testu jednotek a zástupné procedury testu jednotek**

1. V okně editoru kódu klikněte pravým tlačítkem myši a v místní nabídce vyberte možnost **vytvořit testy jednotek** .

    ![V okně editoru zobrazte kontextovou nabídku.](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")

2. Kliknutím na tlačítko OK přijměte výchozí hodnoty pro vytvoření testů jednotek, nebo změňte hodnoty používané k vytvoření a pojmenování projektu testování částí a testování částí. Můžete vybrat kód, který je přidán ve výchozím nastavení do metody testování částí.

    ![Pravý&#45;klikněte v editoru a vyberte vytvořit testy jednotek.](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")

3. Zástupné procedury testu jednotek jsou vytvořeny v novém projektu testování částí pro všechny metody ve třídě.

    ![Testy jednotek jsou vytvořeny](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")

4. Nyní se přeskočíme, jak [přidat kód do testovacích metod jednotek](#BKMK_Writing_your_tests) , abyste měli smysl pro testování částí a všechny další testy jednotek, které můžete chtít přidat k důkladnému testování kódu.

   **Vytvořit projekt testování částí a testování částí ručně**

   Projekt testování částí obvykle odráží strukturu jednoho kódu projektu. V příkladu MyBank přidáte dva projekty testování částí s názvem `AccountsTests` a `BankDbTests` do `MyBanks` řešení. Názvy testovacích projektů jsou libovolné, ale je vhodné přijmout standardní konvence pojmenování.

   **Přidání projektu testu jednotek do řešení:**

5. V nabídce **soubor** klikněte na příkaz **Nový** a zvolte možnost **projekt** (klávesnice Ctrl + Shift + N).

6. V dialogovém okně Nový projekt rozbalte uzel **nainstalováno** , zvolte jazyk, který chcete použít pro testovací projekt, a pak zvolte možnost **test**.

7. Chcete-li použít jeden z rozhraní testování částí od společnosti Microsoft, v seznamu šablon projektu vyberte možnost **projekt testování částí** . V opačném případě vyberte šablonu projektu pro systém testů jednotek, který chcete použít. Chcete-li otestovat `Accounts` projekt našeho příkladu, měli byste projekt pojmenovat `AccountsTests` .

   > [!WARNING]
   > Ne všechny testovací architektury třetích stran a open source jednotky poskytují šablonu projektu sady Visual Studio. Informace o vytvoření projektu naleznete v dokumentu rozhraní.

8. V projektu testu jednotek přidejte odkaz na projekt kódu pod testem v našem příkladu do projektu účty.

    Chcete-li vytvořit odkaz na projekt kódu:

   1. Vyberte projekt v Průzkumník řešení.

   2. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

   3. V dialogovém okně Správce odkazů otevřete uzel **řešení** a vyberte **projekty**. Vyberte název projektu kódu a zavřete dialogové okno.

   Každý projekt testů jednotek obsahuje třídy, které zrcadlí názvy tříd v kódu projektu. V našem příkladu `AccountsTests` by projekt obsahoval následující třídy:

- `AccountInfoTests` Třída obsahuje metody testování částí pro `AccountInfo` třídu v `BankAccount` projektu.

- `CheckingAccountTests` Třída obsahuje metody testování částí pro `CheckingAccount` třídu.

## <a name="write-your-tests"></a><a name="BKMK_Writing_your_tests"></a> Zápis testů
 Rozhraní pro testování částí, které použijete, a Visual Studio IntelliSense vás provede zápisem kódu pro testování částí pro projekt kódu. Pro spuštění v Průzkumníku testů většina rozhraní vyžaduje, abyste přidali konkrétní atributy pro identifikaci metod testování částí. Rozhraní také poskytují způsob – obvykle prostřednictvím příkazů kontrolního výrazu nebo atributů metody – k označení, zda metoda testu prošla nebo se nezdařila. Jiné atributy identifikují volitelné metody nastavení, které jsou při inicializaci třídy a před každou metodou testu a rozboru metody, které jsou spouštěny po každé testovací metodě a před zničením třídy.

 Vzor AAA (uspořádat, ACT, Assert) je běžným způsobem psaní testů jednotek pro testované metody.

- Oddíl **Uspořádat** v metodě testování částí inicializuje objekty a nastaví hodnotu dat, která jsou předána do testované metody.

- Oddíl **Act** vyvolá zkoušenou metodu s použitím seřazených parametrů.

- V části **Assert** se ověří, že se akce testované metody chová podle očekávání.

  Chcete-li otestovat `CheckingAccount.Withdraw` metodu našeho příkladu, můžeme zapsat dva testy: jeden, který ověřuje standardní chování metody a druhý, který ověřuje, že stažení většího množství než vyvážení selže. Do `CheckingAccountTests` třídy přidáme následující metody:

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

 Všimněte si, že `Withdraw_ValidAmount_ChangesBalance` pomocí explicitního `Assert` příkazu určíte, zda metoda testu projde nebo se nezdařila, zatímco `Withdraw_AmountMoreThanBalance_Throws` používá `ExpectedException` atribut k určení úspěchu testovací metody. V rámci pokrývá rámec testu jednotek balí testovací metody v příkazech try/catch. Ve většině případů je-li výjimka zachycena, metoda testu se nezdařila a výjimka je ignorována. `ExpectedException`Atribut způsobí, že metoda testu bude splněna, pokud je vyvolána zadaná výjimka.

 Další informace o architekturách testování částí společnosti Microsoft naleznete v následujících tématech:

- [Zápis testů částí pro rozhraní .NET Framework s infrastrukturou pro testování částí Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [Zápis testů jednotek pro C/C++ s infrastrukturou testování částí Microsoft Unit Testing Framework pro C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

## <a name="set-timeouts-for-unit-tests"></a>Nastavení časových limitů pro testy jednotek
 Nastavení časového limitu pro jednotlivé testovací metody:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

```vb

```

 Nastavení časového limitu na povolené maximum:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a> Spustit testy v Průzkumníku testů
 Při sestavování testovacího projektu se testy zobrazí v Průzkumníku testů. Pokud není Průzkumník testů viditelný, zvolte možnost **test** v nabídce aplikace Visual Studio, zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

 ![Průzkumník testů jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Při spuštění, zápisu a opětovném spuštění testů se ve výchozím zobrazení Průzkumníka testů zobrazí výsledky ve skupinách **neúspěšných testů**, **Úspěšné testy**, **přeskočené testy** a **nespustí testy**. Můžete zvolit záhlaví skupiny a otevřít tak zobrazení, které zobrazí všechny testy v dané skupině.

 Můžete také filtrovat testy v jakémkoli zobrazení pomocí odpovídajícího textu ve vyhledávacím poli na globální úrovni nebo výběrem jednoho z předdefinovaných filtrů. Můžete kdykoli spustit libovolný výběr testů. Výsledky testovacího běhu jsou v horní části okna Průzkumníka okamžitě patrné na panelu předat/selhat. Podrobnosti o výsledku testovací metody se zobrazí, když vyberete test.

### <a name="run-and-view-tests"></a><a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a> Spuštění a zobrazení testů
 Panel nástrojů Průzkumník testů vám pomůže zjistit, uspořádat a spustit testy, které vás zajímají.

 ![Spustit testy z panelu nástrojů Průzkumníka testů](../test/media/ute-toolbar.png "UTE_ToolBar")

 Výběrem možnosti **Spustit vše** můžete spustit všechny testy, nebo výběrem možnosti **Spustit** vyberte podmnožinu testů, které chcete spustit. Po spuštění sady testů se v dolní části okna Průzkumník testů zobrazí souhrn testovacího běhu. Vyberte test pro zobrazení podrobností testu v dolním podokně. Vyberte možnost **Otevřít test** z kontextové nabídky (klávesnice: F12) a zobrazte zdrojový kód pro vybraný test.

 Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí tlačítka ![ustit&#95;parallelicon&#45;malého](../test/media/ute-parallelicon-small.png "UTE_parallelicon – malý") přepínacího tlačítka na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

### <a name="run-tests-after-every-build"></a><a name="BKMK_Running_tests_after_every_build"></a> Spustit testy po každém sestavení

> [!WARNING]
> Spuštění testů jednotek po každém sestavení je podporováno pouze v Visual Studio Enterprise.

|Image|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Chcete-li spustit testy jednotek po každém místním sestavení, klikněte na tlačítko **test** v nabídce Standard a poté na panelu nástrojů Průzkumníka testů klikněte na možnost **Spustit testy po sestavení** .|

### <a name="filter-and-group-the-test-list"></a><a name="BKMK_Filtering_and_grouping_the_test_list"></a> Filtrovat a seskupit seznam testů
 Pokud máte velký počet testů, můžete zadat do vyhledávacího pole Průzkumníka testů, aby seznam vyfiltroval podle zadaného řetězce. Událost filtru můžete omezit tak, že vyberete ze seznamu filtru.

 ![Kategorie vyhledávacích filtrů](../test/media/ute-searchfilter.png "UTE_SearchFilter")

|Image|Popis|
|-|-|
|![Tlačítko skupiny Průzkumníka testů](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Chcete-li seskupit testy podle kategorie, klikněte na tlačítko **Seskupit podle** .|

 Další informace najdete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) .

## <a name="qa"></a>Otázky a odpovědi
 **Otázka: Návody ladit testy jednotek?**

 **A:** Pomocí Průzkumníka testů spusťte ladicí relaci pro vaše testy. Krokování kódu pomocí ladicího programu sady Visual Studio plynule přebírá mezi testy jednotek a testovaným projektem zpět. Spuštění ladění:

1. V editoru sady Visual Studio nastavte zarážku v jedné nebo více testovacích metodách, které chcete ladit.

   > [!NOTE]
   > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metodách, které chcete ladit.

2. V Průzkumníku testů vyberte testovací metody a pak zvolte možnost **ladit vybrané testy** z místní nabídky.

   Přečtěte si další informace o [ladění testů jednotek](../debugger/debugging-in-visual-studio.md).

   **Otázka: Pokud používám TDD, jak mohu generovat kód z mých testů?**

   **A:** Pomocí technologie IntelliSense vygenerujte třídy a metody v kódu projektu. Zapište příkaz v testovací metodě, která volá třídu nebo metodu, kterou chcete vygenerovat, a pak otevřete nabídku IntelliSense pod voláním. Pokud je volání konstruktoru nové třídy, v nabídce vyberte možnost **generovat nový typ** a postupujte podle pokynů průvodce a vložte třídu do projektu kódu. Pokud je volání metody, vyberte možnost **Generovat novou metodu** z nabídky technologie IntelliSense.

   ![Vygenerovat nabídku se zástupnými procedurami IntelliSense](../test/media/ute-generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")

   **Otázka: je možné vytvořit testy jednotek, které při spuštění testu přebírají více sad dat jako vstup?**

   **Odpověď:** Ano. *Testovací metody řízené daty* umožňují testovat rozsah hodnot pomocí jediné metody testování částí. Použijte `DataSource` atribut pro testovací metodu, která určuje zdroj dat a tabulku obsahující proměnné hodnoty, které chcete testovat.  V těle metody přiřadíte hodnoty řádku k proměnným pomocí `TestContext.DataRow[` *ColumnName* `]` indexeru ColumnName.

> [!NOTE]
> Tyto postupy se vztahují pouze na testovací metody, které zapisujete pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód. Pokud používáte jiné rozhraní, Projděte si dokumentaci k rozhraní pro ekvivalentní funkce.

 Předpokládejme například, že přidáte nepotřebnou metodu do `CheckingAccount` třídy, která je pojmenována `AddIntegerHelper` . `AddIntegerHelper` přidá dvě celá čísla.

 Chcete-li vytvořit test řízený daty pro `AddIntegerHelper` metodu, nejprve vytvoříme databázi Access s názvem `AccountsTest.accdb` a tabulku s názvem `AddIntegerHelperData` . `AddIntegerHelperData`Tabulka definuje sloupce pro zadání prvního a druhého operandu přidání a sloupce, které určují očekávaný výsledek. Vyplníme počet řádků odpovídajícími hodnotami.

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

 Metoda s atributem se spustí jednou pro každý řádek v tabulce. Průzkumník testů hlásí selhání testu pro metodu, pokud některá iterace selže. Podokno podrobností výsledků testu pro metodu ukazuje metodu stavu Pass/selhat pro každý řádek dat.

 Přečtěte si další informace o [testech jednotek řízených daty](../test/how-to-create-a-data-driven-unit-test.md).

 **Otázka: mohu zobrazit, kolik z mých kódů je Testováno pomocí mých testů částí?**

 **Odpověď:** Ano. Můžete určit množství kódu, který je skutečně testován pomocí testu jednotek pomocí nástroje pokrytí kódu sady Visual Studio. Jsou podporovány nativní a spravované jazyky a všechny architektury testování částí, které lze spustit v rámci testovacího rozhraní jednotky.

 Můžete spustit pokrytí kódu pro vybrané testy nebo pro všechny testy v řešení. V okně výsledky pokrytí kódu se zobrazí procentuální podíl bloků kódu produktu, které byly uplatněny pomocí řádku, funkce, třídy, oboru názvů a modulu.

 Chcete-li spustit pokrytí kódu pro testovací metody v řešení, zvolte možnost **testy** v nabídce aplikace Visual Studio a pak zvolte možnost **Analyzovat pokrytí kódu**.

 Výsledky pokrytí se zobrazí v okně výsledky pokrytí kódu.

 ![Výsledky pokrytí kódu](../test/media/ute-codecoverageresults.png "UTE_CodeCoverageResults")

 Přečtěte si další informace o [pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

 **Otázka: Jak můžu testovat metody v mém kódu, které mají vnější závislosti?**

 **Odpověď:** Ano. Pokud máte Visual Studio Enterprise, je možné použít napodobeniny společnosti Microsoft s testovacími metodami, které zapisujete pomocí testovacích rozhraní jednotek pro spravovaný kód.

 Napodobeniny Microsoftu využívají dva přístupy k vytváření náhradních tříd pro externí závislosti.

1. Zástupné *procedury* generují náhradní třídy odvozené z nadřazeného rozhraní třídy Target závislosti. Metody zástupných procedur lze nahradit veřejnými virtuálními metodami cílové třídy.

2. *Překrytí* používají instrumentaci za běhu k přesměrování volání cílové metody do náhradní metody Shim pro jiné než virtuální metody.

   V obou metodách použijete vygenerované delegáty volání metody závislosti k určení chování, které chcete v testovací metodě.

   Přečtěte si další informace o [izolaci metod testování částí s napodobeninami Microsoftu](../test/isolating-code-under-test-with-microsoft-fakes.md).

   **Otázka: je možné použít jiné architektury testování částí k vytvoření testů jednotek?**

   **A:** Ano, pomocí následujícího postupu můžete [Najít a nainstalovat další architektury](../test/install-third-party-unit-test-frameworks.md). Po restartování sady Visual Studio znovu otevřete řešení a vytvořte testy jednotek a potom vyberte vaše nainstalovaná rozhraní zde:

   ![Vybrat další instalovaný systém pro testování částí](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")

   Vaše zástupné procedury testu jednotek budou vytvořeny pomocí vybraného rozhraní.
