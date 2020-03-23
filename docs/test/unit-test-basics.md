---
title: Základy testování částí
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77ac5ffd14f97fd6fdd753327fe193ceb80ea57e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846933"
---
# <a name="unit-test-basics"></a>Základní informace o testování částí

Zkontrolujte, zda váš kód funguje podle očekávání vytvořením a spuštěním testů částí. Říká se testování částí, protože rozdělení funkčnosti programu na diskrétní testovatelné chování, které můžete testovat jako jednotlivé *jednotky*. Visual Studio Test Explorer poskytuje flexibilní a efektivní způsob, jak spustit testy částí a zobrazit jejich výsledky v sadě Visual Studio. Visual Studio nainstaluje rozhraní microsoft testování částí pro spravovaný a nativní kód. Pomocí *rozhraní testování částí* vytvořit testování částí, spusťte je a sestavy výsledků těchto testů. Znovu spusťte testy částí, když provedete změny k testování, že váš kód stále pracuje správně. Visual Studio Enterprise to může udělat automaticky pomocí [živého testování částí](live-unit-testing-intro.md), který detekuje testy ovlivněné změnami kódu a spustí je na pozadí při psaní.

Testování částí má největší vliv na kvalitu kódu, pokud je nedílnou součástí pracovního postupu vývoje softwaru. Jakmile napíšete funkci nebo jiný blok kódu aplikace, vytvořte testy částí, které ověřují chování kódu v reakci na standardní, hraniční a nesprávné případy vstupních dat a které kontrolují všechny explicitní nebo implicitní předpoklady provedené kódem. S *vývoj řízený testováním*, můžete vytvořit testy částí před zápisem kódu, takže použijete testování částí jako dokumentaci návrhu a funkční specifikace.

Můžete rychle generovat testovací projekty a testovací metody z vašeho kódu nebo ručně vytvořit testy podle potřeby. Při použití IntelliTest prozkoumat váš kód .NET, můžete generovat testovací data a sadu testů částí. Pro každý příkaz v kódu se generuje zkušební vstup, který tento příkaz spustí.  Zjistěte, jak [generovat testy částí pro váš kód](generate-unit-tests-for-your-code-with-intellitest.md).

Průzkumník testů může také spustit rozhraní test ů třetích stran a jednotek s otevřeným zdrojovým kódem, které implementovaly rozhraní doplňků Průzkumníka testů. Mnoho z těchto architektur můžete přidat prostřednictvím Správce rozšíření sady Visual Studio a galerie Sady Visual Studio. Další informace naleznete [v tématu Instalace rozhraní test ů částí jiných výrobců](../test/install-third-party-unit-test-frameworks.md).

## <a name="get-started"></a>Začínáme

Úvod k testování částí, který vás přenese přímo do kódování, najdete v jednom z těchto témat:

- [Návod: Vytváření a spouštění testů jednotek pro spravovaný kód](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Úvodní příručka: Vývoj řízený testováním pomocí Průzkumníka testů](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Zápis testů částí pro C/C++ v sadě Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Příklad řešení MyBank

V tomto článku používáme vývoj fiktivní `MyBank` aplikace s názvem jako příklad. Nepotřebujete skutečný kód, abyste se řídili vysvětleními v tomto tématu. Testovací metody jsou zapsány v C# a prezentovány pomocí microsoft testování částí framework pro spravovaný kód. Koncepty jsou však snadno přeneseny do jiných jazyků a rámců.

::: moniker range="vs-2017"
![Řešení MyBank](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![MyBank Řešení 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Náš první pokus o `MyBank` návrh aplikace zahrnuje komponentu účtů, která představuje individuální účet a jeho transakce s bankou, a databázovou komponentu, která představuje funkci pro agregaci a správu jednotlivých účtů.

Vytváříme `MyBank` řešení, které obsahuje dva projekty:

- `Accounts`

- `BankDb`

Náš první pokus o `Accounts` návrh projektu obsahuje třídu pro uložení základních informací o účtu, rozhraní, které určuje běžné funkce libovolného typu účtu, jako je uložení a výběr majetku z účtu, a třídu odvozenou z rozhraní, které představuje běžný účet. Začínáme projekty účty vytvořením následujících zdrojových souborů:

- *AccountInfo.cs* definuje základní informace pro účet.

- *IAccount.cs* definuje standardní `IAccount` rozhraní pro účet, včetně metod pro vklad a výběr aktiv z účtu a pro načtení zůstatku na účtu.

- *CheckingAccount.cs* obsahuje `CheckingAccount` třídu, `IAccount` která implementuje rozhraní pro běžný účet.

Ze zkušenosti víme, že jedna věc, kterou musí výběr z běžnýho účtu udělat, je ujistit se, že stažená částka je nižší než zůstatek na účtu. Takže jsme přepsat `IAccount.Withdraw` metodu v `CheckingAccount` s metodou, která kontroluje pro tuto podmínku. Metoda může vypadat takto:

```csharp
public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(nameof(amount), "Withdrawal exceeds balance!");
    }
}
```

Teď, když máme nějaký kód, je čas na testování.

## <a name="create-unit-test-projects-and-test-methods"></a>Vytvořit projekty testování částí a zkušební metody

Je často rychlejší generovat projekt testování částí a testování částí z vašeho kódu. Nebo můžete vytvořit projekt testování částí a testy ručně v závislosti na vašich požadavcích. Pokud chcete vytvořit testy částí s rámcem třetích stran, budete potřebovat jedno z těchto rozšíření nainstalováno: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) nebo [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Generovat zkušební projekt částí a zkušební protokoly jednotek

1. V okně editoru kódu klikněte pravým tlačítkem myši a zvolte [**Vytvořit testy částí**](create-unit-tests-menu.md) z nabídky po kliknutí pravým tlačítkem myši.

   ::: moniker range="vs-2017"
   ![V okně editoru zobrazte kontextovou nabídku](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > Příkaz **příkazu Vytvořit testy jednotek** je k dispozici pouze pro spravovaný kód, který cílí na rozhraní .NET Framework (ale ne na jádro .NET).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![V okně editoru zobrazte kontextovou nabídku](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > Příkaz **Nabídky Vytvořit testy jednotek** je k dispozici pouze pro spravovaný kód.
   ::: moniker-end

2. Klepnutím na **tlačítko OK** přijměte výchozí hodnoty pro vytvoření testů částí nebo změňte hodnoty použité k vytvoření a pojmenování projektu testování částí a testů částí. Můžete vybrat kód, který je přidán ve výchozím nastavení do metod testování částí.

   ![Dialogové okno Vytvořit testy částí v sadě Visual Studio](../test/media/create-unit-tests.png)

3. Zástupné procedury testování částí jsou vytvořeny v projektu testování nové jednotky pro všechny metody ve třídě.

   ::: moniker range="vs-2017"
   ![Jednotkové testy jsou vytvořeny](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Jednotkové testy jsou vytvořeny](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Nyní přejděte dopředu a zjistěte, jak [přidat kód do testovacích metod částí,](#write-your-tests) aby byl test částí smysluplný, a všechny další testy částí, které můžete chtít přidat k důkladnému testování kódu.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Ruční vytvoření projektu testování částí a testů částí

Projekt testování částí obvykle zrcadlí strukturu jednoho projektu kódu. V příkladu MyBank přidáte dva projekty `BankDbTests` testování `MyBanks` částí s názvem `AccountsTests` a do řešení. Názvy testovacích projektů jsou libovolné, ale přijetí standardní konvence pojmenování je vhodné.

**Přidání projektu testování částí do řešení:**

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a zvolte **Přidat** > **nový** **projekt**.

::: moniker range="vs-2017"

2. V dialogovém okně **Nový projekt** rozbalte **nainstalovaný** uzel, zvolte jazyk, který chcete použít pro testovací projekt, a pak zvolte **Testovat**.

3. Chcete-li použít jeden z rozhraní testování částí společnosti Microsoft, zvolte **Projekt testování částí** ze seznamu šablon projektu. V opačném případě zvolte šablonu projektu rozhraní testování částí, které chcete použít. Chcete-li `Accounts` otestovat projekt našeho příkladu, pojmenujete projekt `AccountsTests`.

   > [!NOTE]
   > Ne všechny architektury testování částí jiných výrobců a open source poskytují šablonu projektu sady Visual Studio. Informace o vytvoření projektu naleznete v rámcovém dokumentu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Pomocí vyhledávacího pole šablony projektu vyhledejte šablonu projektu testování částí pro testovací rámec, který chcete použít.

3. Na další stránce pojmenujte projekt. Chcete-li `Accounts` otestovat projekt našeho příkladu, můžete projekt `AccountsTests`pojmenovat .

::: moniker-end

4. V projektu testování částí přidejte odkaz na testovaný projekt kódu v našem příkladu na projekt účty.

   Chcete-li vytvořit odkaz na projekt kódu:

   1. Vyberte projekt v **Průzkumníku řešení**.

   2. V nabídce **Projekt** zvolte **Přidat odkaz**.

   3. V dialogovém okně **Správce odkazů** otevřete uzel **Řešení** a zvolte **Projekty**. Vyberte název projektu kódu a zavřete dialogové okno.

Každý projekt testování částí obsahuje třídy, které zrcadlí názvy tříd v projektu kódu. V našem příkladu `AccountsTests` by projekt obsahoval následující třídy:

- `AccountInfoTests`třída obsahuje metody testování `AccountInfo` částí pro `Accounts` třídu v projektu

- `CheckingAccountTests`třída obsahuje metody testování `CheckingAccount` částí pro třídu.

## <a name="write-your-tests"></a>Napište své testy

Rozhraní testování částí, které používáte a Visual Studio IntelliSense vás provede psaní kódu pro testování částí pro projekt kódu. Chcete-li spustit v **Průzkumníku testů**, většina rozhraní vyžadují přidat konkrétní atributy k identifikaci metody testování částí. Rámce také poskytují způsob – obvykle prostřednictvím assert příkazy nebo atributy metody – k označení, zda zkušební metoda prošla nebo se nezdařila. Jiné atributy identifikují volitelné metody nastavení, které jsou při inicializaci třídy a před každou zkušební metodou a metodami teardown, které jsou spuštěny po každé zkušební metodě a před zničením třídy.

Vzor AAA (Uspořádat, Jednat, Assert) je běžný způsob psaní testů částí pro testovnu.

- Oddíl **Uspořádat** zkušební metody jednotky inicializuje objekty a nastaví hodnotu dat, která je předána do zkoušené metody.

- Část **Akt** vyvolá testovku s uspořádanými parametry.

- Assert **Assert** část ověří, že akce metody v testu se chová podle očekávání.

Chcete-li `CheckingAccount.Withdraw` otestovat metodu našeho příkladu, můžeme napsat dva testy: jeden, který ověří standardní chování metody a jeden, který ověří, že stažení více než zůstatek se nezdaří. Ve `CheckingAccountTests` třídě přidáme následující metody:

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

    // assert
    Assert.AreEqual(expected, account.Balance);
}

[TestMethod]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);

    // act and assert
    Assert.ThrowsException<System.ArgumentException>(() => account.Withdraw(20.0));
}
```

Další informace o rozhraních testování částí společnosti Microsoft naleznete v jednom z následujících témat:

- [Testování částí kódu](unit-test-your-code.md)

- [Zápis testů částí pro C/C++](writing-unit-tests-for-c-cpp.md)

- [Použití architektury MSTest v jednotkových testech](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Nastavení časových lhůt pro testy částí

Pokud používáte architekturu MSTest, můžete <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> použít k nastavení časového odčasového časového roku pro individuální testovací metodu:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Nastavení časového limitu na maximální povolenou hodnotu:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Spuštění testů v Průzkumníkovi testů

Při vytváření testovacího projektu se testy zobrazí v **Průzkumníku testů**. Pokud **Průzkumník testů** není viditelný, zvolte **Testovat** v nabídce Visual Studio, zvolte **Windows**a pak zvolte **Test Explorer**.

::: moniker range="vs-2017"
![Průzkumník testování částí](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Průzkumník testování částí](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Při spuštění, zápisu a opětovném spuštění testů může **Průzkumník testů** zobrazit výsledky ve skupinách **neúspěšných testů**, **Předané testy**, **Přeskočené testy** a **Nespouštět testy**. Na panelu nástrojů můžete zvolit různé možnosti podle skupiny.

Testy můžete také filtrovat v libovolném zobrazení porovnáním textu ve vyhledávacím poli na globální úrovni nebo výběrem jednoho z předdefinovaných filtrů. Můžete spustit libovolný výběr testů kdykoli. Výsledky testu jsou okamžitě patrné v pruhu průchodu/selhání v horní části okna průzkumníka. Podrobnosti o výsledku zkušební metody jsou zobrazeny při výběru testu.

### <a name="run-and-view-tests"></a>Spuštění a zobrazení testů

Panel nástrojů **Průzkumník testů** vám pomůže zjišťovat, organizovat a spouštět testy, které vás zajímají.

::: moniker range="vs-2017"
![Spuštění testů z panelu nástrojů Průzkumníka testů](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Spuštění testů z panelu nástrojů Průzkumníka testů](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Můžete zvolit **Spustit vše** pro spuštění všech testů nebo zvolte **Spustit** a zvolte podmnožinu testů, které chcete spustit. Vyberte test pro zobrazení podrobností tohoto testu v podokně podrobností testu. Zvolte **Otevřít test** z nabídky po kliknutí pravým tlačítkem myši (Klávesnice: **F12**), chcete-li zobrazit zdrojový kód pro vybraný test.

::: moniker range="vs-2017"

Pokud jednotlivé testy nemají žádné závislosti, které by bránily jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![UTE&#95;parallelicon&#45;malý](../test/media/ute_parallelicon-small.png) přepínat na panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jednotlivé testy nemají žádné závislosti, které brání jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testu v nabídce nastavení panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Spuštění testů po každém sestavení

::: moniker range="vs-2017"

|Tlačítko|Popis|
|-|-|
|![Spustit po sestavení](../test/media/ute_runafterbuild_btn.png)|Chcete-li spustit testy částí po každém místním sestavení, zvolte **Testovat** ve standardní nabídce a pak zvolte **Spustit testy po sestavení** na panelu nástrojů **Průzkumníka testů.**|

> [!NOTE]
> Spuštění testů částí po každém sestavení vyžaduje visual studio 2017 Enterprise edition nebo Visual Studio 2019. V sadě Visual Studio 2019 je tato funkce k dispozici v edici Community a Professional kromě edice Enterprise.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li spustit testy částí po každém místním sestavení, otevřete ikonu nastavení na panelu nástrojů Průzkumníktestů a vyberte **spustit testy po sestavení**.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Filtrování a seskupit seznam testů

Pokud máte velký počet testů, můžete zadat do vyhledávacího pole **Průzkumníka testů** a filtrovat seznam podle zadaného řetězce. Událost filtru můžete omezit více výběrem ze seznamu filtrů.

::: moniker range="vs-2017"
![Kategorie vyhledávacího filtru](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Kategorie vyhledávacího filtru](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Tlačítko|Popis|
|-|-|
|![Tlačítko Skupiny Průzkumníka testů](../test/media/ute_groupby_btn.png)|Chcete-li testy seskupit podle kategorie, zvolte tlačítko **Seskupit podle.**|

Další informace naleznete v [tématu Spuštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>Q&A

**Otázka: Jak lze ladit testy částí?**

**A:** Pomocí **Průzkumníka testů** spusťte relaci ladění testů. Krokování kódu s ladicím programem sady Visual Studio vás bez problémů přenese tam a zpět mezi testy částí a testovaného projektu. Zahájení ladění:

1. V editoru Visual Studio nastavte zarážku v jedné nebo více testovacích metod, které chcete ladit.

    > [!NOTE]
    > Vzhledem k tomu, že testovací metody lze spustit v libovolném pořadí, nastavte zarážky ve všech testovacích metod, které chcete ladit.

2. V **Průzkumníkovi testů**vyberte testovací metody a v místní nabídce zvolte **Ladit vybrané testy.**

Další informace o [ladění testů částí](../debugger/debugger-feature-tour.md).

**Otázka: Pokud používám TDD, jak mohu generovat kód z testů?**

**A:** Pomocí rychlých akcí vygenerujte třídy a metody v kódu projektu. Napište příkaz v testovací metodě, která volá třídu nebo metodu, kterou chcete generovat, a otevřete žárovku, která se zobrazí pod chybou. Pokud je volání konstruktoru nové třídy, zvolte **Generovat typ** z nabídky a postupujte podle průvodce pro vložení třídy do projektu kódu. Pokud je volání na metodu, zvolte **Generovat metodu** z nabídky IntelliSense.

::: moniker range="vs-2017"
![Generovat nabídku rychlé akce se zakázaným inzerováním metod](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Generovat nabídku rychlé akce se zakázaným inzerováním metod](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**Otázka: Lze vytvořit testy částí, které trvat více sad dat jako vstup ke spuštění testu?**

**Odpověď:** Ano. *Testovací metody řízené daty* umožňují testovat rozsah hodnot pomocí jedné zkušební metody jednotky. Použijte `DataSource` atribut pro testovací metodu, která určuje zdroj dat a tabulku obsahující hodnoty proměnných, které chcete testovat.  V těle metody přiřadíte hodnoty řádků proměnným pomocí indexeru `TestContext.DataRow[` *ColumnName.* `]`

> [!NOTE]
> Tyto postupy platí pouze pro testovací metody, které píšete pomocí rozhraní Microsoft unit test framework pro spravovaný kód. Pokud používáte jiný rámec, podívejte se do rámcové dokumentace pro ekvivalentní funkce.

Předpokládejme například, že přidáme `CheckingAccount` nepotřebnou `AddIntegerHelper`metodu do třídy s názvem . `AddIntegerHelper`přidá dvě celá čísla.

Chcete-li vytvořit test řízený `AddIntegerHelper` daty pro metodu, nejprve vytvoříme databázi `AddIntegerHelperData`aplikace Access s názvem *AccountsTest.accdb* a tabulku s názvem . Tabulka `AddIntegerHelperData` definuje sloupce pro určení prvního a druhého operandů přidání a sloupec pro určení očekávaného výsledku. Vyplníme řadu řádků s příslušnými hodnotami.

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

Přiřazená metoda je spuštěna jednou pro každý řádek v tabulce. **Průzkumník testů** hlásí selhání testu pro metodu, pokud některá z iterací nezdaří. Podokno podrobností výsledků testu pro metodu zobrazuje metodu stavu průchodu/selhání pro každý řádek dat.

Další informace o [testech částí řízených daty](../test/how-to-create-a-data-driven-unit-test.md).

**Otázka: Lze zobrazit, kolik kódu je testováno testy částí?**

**Odpověď:** Ano. Můžete určit množství kódu, který je ve skutečnosti testován testy částí pomocí nástroje pokrytí kódu Sady Visual Studio v sadě Visual Studio Enterprise. Nativní a spravované jazyky a všechny architektury testování částí, které lze spustit rozhraním testování částí jsou podporovány.

Pokrytí kódu můžete spustit na vybraných testech nebo na všech testech v řešení. Okno **Výsledky pokrytí kódu** zobrazuje procento bloků kódu produktu, které byly uplatněny podle řádku, funkce, třídy, oboru názvů a modulu.

Chcete-li spustit pokrytí kódu pro testovací metody v řešení, zvolte **Testovat** > **analyzovat pokrytí kódu pro všechny testy**.

Výsledky disponibility se zobrazí v okně **Výsledky pokrytí kódu.**

![Výsledky pokrytí kódu](../test/media/ute_codecoverageresults.png)

Další informace o [pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**Otázka: Lze testovat metody v kódu, které mají externí závislosti?**

**Odpověď:** Ano. Pokud máte Visual Studio Enterprise, Microsoft Fakes lze použít s testovací metody, které píšete pomocí rozhraní testování částí pro spravovaný kód.

Microsoft Fakes používá dva přístupy k vytvoření náhradní třídy pro externí závislosti:

1. *Zástupné procedury* generují náhradní třídy odvozené z nadřazeného rozhraní cílové třídy závislostí. Metody se zakázaným inzerováním lze nahradit veřejné virtuální metody cílové třídy.

2. *Překrytí* pomocí instrumentace za běhu přesměrovat volání na cílovou metodu na metodu náhradní překrytí pro nevirtuální metody.

V obou přístupech použijete generované delegáty volání metody závislosti k určení chování, které chcete v testovací metodě.

Další informace o [izolaci metod testování částí pomocí služby Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Otázka: Lze použít jiné rozhraní testování částí k vytvoření testování částí?**

**A:** Ano, pomocí těchto kroků [vyhledejte a nainstalujte další rozhraní](../test/install-third-party-unit-test-frameworks.md). Po restartování sady Visual Studio znovu otevřete řešení a vytvořte testy částí a vyberte zde nainstalované architektury:

![Vyberte další architekturu testování nainstalované jednotky](../test/media/createunittestsdialogextensions.png)

Vaše testovací útržky jednotky budou vytvořeny pomocí vybraného rozhraní.
