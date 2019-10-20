---
title: 'Postupy: vytvoření testu jednotek řízeného daty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9dc5ad44a73f517b91562209abfab8b0b3e8d4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660524"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Postupy: Testy jednotek řízené daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód můžete nastavit metodu testování částí pro načtení hodnot použitých v testovací metodě ze zdroje dat. Metoda je postupně spouštěna pro každý řádek ve zdroji dat, což usnadňuje testování různých vstupů pomocí jediné metody.

 Toto téma obsahuje následující oddíly:

- [Testovaný způsob](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)

- [Vytvoření zdroje dat](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)

- [Přidání TestContext do testovací třídy](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)

- [Zápis testovací metody](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)

  - [Určení DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)

  - [Použití TestContext. DataRow pro přístup k datům](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)

- [Spuštění testu a zobrazení výsledků](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)

  Vytváření testu jednotek řízených daty zahrnuje následující kroky:

1. Vytvořte zdroj dat, který obsahuje hodnoty, které použijete v testovací metodě. Zdroj dat může být jakýkoli typ, který je zaregistrován na počítači, který spouští test.

2. Přidejte soukromé <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole a vlastnost Public `TestContext` do třídy testu.

3. Vytvořte metodu testování částí a přidejte do ní atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

4. Pomocí vlastnosti <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> indexer načtěte hodnoty, které používáte v testu.

## <a name="BKMK_The_method_under_test"></a>Testovaný způsob
 Předpokládejme například, že jsme vytvořili:

1. Řešení s názvem `MyBank`, které přijímá a zpracovává transakce pro různé typy účtů.

2. Projekt v `MyBank` nazvaný `BankDb`, který spravuje transakce pro účty.

3. Třída s názvem `Maths` v projektu `DbBank`, která provádí matematické funkce, aby se zajistilo, že je každá transakce pro banku výhodná.

4. Projekt testu jednotek s názvem `BankDbTests` k otestování chování komponenty `BankDb`.

5. Třída testu jednotek s názvem `MathsTests` pro ověření chování `Maths` třídy.

   Budeme testovat metodu v `Maths`, která přidá dvě celá čísla pomocí smyčky:

```
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="BKMK_Creating_a_data_source"></a>Vytvoření zdroje dat
 K otestování `AddIntegers` metody vytvoříme zdroj dat, který určuje rozsah hodnot pro parametry a součet, který chcete vrátit. V našem příkladu vytvoříme databázi SQL Compact s názvem `MathsData` a tabulku s názvem `AddIntegersData`, která obsahuje následující názvy a hodnoty sloupců.

|Prvníčíslo|Druhéčíslo|Zapůjčen|
|-----------------|------------------|---------|
|0,8|první|první|
|první|první|odst|
|odst|– 3|– 1|

## <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a>Přidání TestContext do testovací třídy
 Rozhraní testování částí vytvoří objekt `TestContext` pro uložení informací o zdroji dat pro test řízený daty. Rozhraní potom nastaví tento objekt jako hodnotu vlastnosti `TestContext`, kterou vytvoříme.

```

private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}

```

 V testovací metodě získáte přístup k datům prostřednictvím vlastnosti `DataRow` indexer `TestContext`.

## <a name="BKMK_Writing_the_test_method"></a>Zápis testovací metody
 Testovací metoda pro `AddIntegers` je poměrně jednoduchá. Pro každý řádek ve zdroji dat zavoláme `AddIntegers` hodnoty sloupce **prvníčíslo** a **druhéčíslo** jako parametry a ověříme návratovou hodnotu oproti hodnotě sloupce **Sum** :

```

[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});

}

```

 Všimněte si, že metoda `Assert` obsahuje zprávu, která zobrazuje `x` a `y` hodnoty neúspěšné iterace. Ve výchozím nastavení jsou hodnoty s hodnotou `expected` a `actual` již zahrnuty v podrobnostech o neúspěšném testu.

### <a name="BKMK_Specifying_the_DataSourceAttribute"></a>Určení DataSourceAttribute
 Atribut `DataSource` Určuje připojovací řetězec pro zdroj dat a název tabulky, kterou použijete v testovací metodě. Přesné informace v připojovacím řetězci se liší v závislosti na typu zdroje dat, který používáte. V tomto příkladu jsme použili databázi SqlServerCe.

```
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

 Atribut DataSource má tři konstruktory.

```
[DataSource(dataSourceSettingName)]
```

 Konstruktor s jedním parametrem používá informace o připojení, které jsou uloženy v souboru App. config pro řešení. *DataSourceSettingsName* je název elementu XML v konfiguračním souboru, který určuje informace o připojení.

 Použití souboru App. config umožňuje změnit umístění zdroje dat bez provedení změn v samotném testu jednotek. Informace o tom, jak vytvořit a použít soubor App. config, najdete v tématu [Návod: použití konfiguračního souboru k definování zdroje dat.](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```
[DataSource(connectionString, tableName)]
```

 Konstruktor `DataSource` se dvěma parametry Určuje připojovací řetězec pro zdroj dat a název tabulky, která obsahuje data pro testovací metodu.

 Připojovací řetězce závisí na typu typu zdroje dat, ale měl by obsahovat element provider, který určuje neutrální název poskytovatele dat.

```
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a>Použití TestContext. DataRow pro přístup k datům
 Pro přístup k datům v tabulce `AddIntegersData` použijte indexer `TestContext.DataRow`. `DataRow` je objekt <xref:System.Data.DataRow>, takže načteme hodnoty sloupců podle názvů indexů nebo sloupců. Vzhledem k tomu, že hodnoty jsou vraceny jako objekty, je nutné je převést na příslušný typ:

```
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);

```

## <a name="BKMK_Running_the_test_and_viewing_results"></a>Spuštění testu a zobrazení výsledků
 Po dokončení psaní testovací metody Sestavte projekt testů. Testovací metoda se zobrazí v okně Průzkumník testů ve skupině **Nespuštěné testy** . Když spouštíte, píšete a znovu spustíte testy, Průzkumník testů zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**a **nespustí testy**. Můžete zvolit **Spustit vše** , pokud chcete spustit všechny testy, nebo kliknout na **Spustit...** a vybrat podmnožinu testů, které chcete spustit.

 Pruh výsledků testu v horní části Průzkumníka je animovaný jako vaše testovací běhy. Na konci testovacího běhu bude pruh zelený, pokud všechny testy byly úspěšné nebo červené, pokud došlo k selhání některého testu. Souhrn testovacího běhu se zobrazí v podokně podrobností v dolní části okna Průzkumníka testů. Vyberte test pro zobrazení podrobností testu v dolním podokně.

 Pokud jste v našem příkladu spustili metodu `AddIntegers_FromDataSourceTest`, panel výsledků se změní na červenou a testovací metoda je přesunuta na **neúspěšné testy** na základě dat, pokud některé z iterací ze zdroje dat selžou. Když v okně Průzkumníka testů zvolíte neúspěšný test řízený daty, v podokně podrobností se zobrazí výsledky každé iterace, která je identifikována indexem řádku dat. V našem příkladu se zobrazí, že algoritmus `AddIntegers` nezpracovává záporné hodnoty správně.

 Při opravě testované metody a opětovném spuštění testu se pruh výsledků změní na zelený a testovací metoda je přesunuta do **předané testovací** skupiny.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName><xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
 [Postupy: vytvoření a spuštění testování jednotek jednotek testování](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48) [kódu](../test/unit-test-your-code.md) [spuštění testů jednotek pomocí testů v Průzkumníku testů](../test/run-unit-tests-with-test-explorer.md) [pro .NET Framework s využitím rozhraní testování částí Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)
