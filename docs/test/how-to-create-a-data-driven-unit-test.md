---
title: Vytváření testů jednotek řízených daty
ms.date: 05/08/2019
ms.topic: conceptual
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0a3162dcbbd041a7d2f540a335bd95854afd87d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643486"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Postupy: vytvoření testu jednotek řízených daty

Pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód můžete nastavit metodu testování částí pro načtení hodnot ze zdroje dat. Metoda je postupně spouštěna pro každý řádek ve zdroji dat, což usnadňuje testování různých vstupů pomocí jediné metody.

Vytváření testu jednotek řízených daty zahrnuje následující kroky:

1. Vytvořte zdroj dat, který obsahuje hodnoty, které použijete v testovací metodě. Zdroj dat může být jakýkoli typ, který je zaregistrován na počítači, který spouští test.

2. Přidejte soukromé <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole a vlastnost Public `TestContext` do třídy testu.

3. Vytvořte metodu testování částí a přidejte do ní atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

4. Pomocí vlastnosti <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> indexer načtěte hodnoty, které používáte v testu.

## <a name="the-method-under-test"></a>Testovaný způsob

Předpokládejme například, že máte následující:

1. Řešení s názvem `MyBank`, které přijímá a zpracovává transakce pro různé typy účtů.

2. Projekt v `MyBank` nazvaný `BankDb`, který spravuje transakce pro účty.

3. Třída s názvem `Maths` v projektu `BankDb`, která provádí matematické funkce, aby se zajistilo, že je každá transakce pro banku výhodná.

4. Projekt testu jednotek s názvem `BankDbTests` k otestování chování komponenty `BankDb`.

5. Třída testu jednotek s názvem `MathsTests` pro ověření chování `Maths` třídy.

Otestujeme metodu v `Maths`, která přidá dvě celá čísla pomocí smyčky:

```csharp
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

## <a name="create-a-data-source"></a>Vytvoření zdroje dat

Chcete-li otestovat metodu `AddIntegers`, vytvořte zdroj dat, který určuje rozsah hodnot pro parametry a součet, který chcete vrátit. V tomto příkladu vytvoříme databázi SQL Compact s názvem `MathsData` a tabulku s názvem `AddIntegersData`, která obsahuje následující názvy a hodnoty sloupců.

|Prvníčíslo|Druhéčíslo|Zapůjčen|
|-|------------------|-|
|0,8|první|první|
|první|první|odst|
|odst|– 3|– 1|

## <a name="add-a-testcontext-to-the-test-class"></a>Přidat TestContext do testovací třídy

Rozhraní testování částí vytvoří objekt `TestContext` pro uložení informací o zdroji dat pro test řízený daty. Rozhraní potom nastaví tento objekt jako hodnotu vlastnosti `TestContext`, kterou vytvoříte.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

V testovací metodě získáte přístup k datům prostřednictvím vlastnosti `DataRow` indexer `TestContext`.

> [!NOTE]
> .NET Core nepodporuje atribut [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) . Pokud se pokusíte získat přístup k datům testu tímto způsobem v projektu testu jednotek .NET Core nebo UWP, zobrazí se chyba podobná řetězci **"TestContext" neobsahuje definici pro "DataRow" a žádná přístupná metoda rozšíření ' DataRow ' nepřijímá první argument typu ' TestContext se najít (nechybí Direktiva using nebo odkaz na sestavení?)** .

## <a name="write-the-test-method"></a>Zapsat testovací metodu

Testovací metoda pro `AddIntegers` je poměrně jednoduchá. Pro každý řádek ve zdroji dat zavolejte `AddIntegers` s hodnotami sloupce **prvníčíslo** a **druhéčíslo** jako parametry a ověřte návratovou hodnotu oproti hodnotě sloupce **Sum** :

```csharp
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

Metoda `Assert` obsahuje zprávu, která zobrazuje `x` a `y` hodnoty neúspěšné iterace. Ve výchozím nastavení jsou hodnoty s hodnotou `expected` a `actual` již zahrnuty v podrobnostech o neúspěšném testu.

### <a name="specify-the-datasourceattribute"></a>Zadejte DataSourceAttribute

Atribut `DataSource` Určuje připojovací řetězec pro zdroj dat a název tabulky, kterou použijete v testovací metodě. Přesné informace v připojovacím řetězci se liší v závislosti na typu zdroje dat, který používáte. V tomto příkladu jsme použili databázi SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atribut DataSource má tři konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor s jedním parametrem používá informace o připojení, které jsou uloženy v souboru *App. config* pro řešení. *DataSourceSettingsName* je název elementu XML v konfiguračním souboru, který určuje informace o připojení.

Použití souboru *App. config* umožňuje změnit umístění zdroje dat bez provedení změn v samotném testu jednotek. Informace o tom, jak vytvořit a použít soubor *App. config* , najdete v tématu [Návod: použití konfiguračního souboru k definování zdroje dat.](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

Konstruktor `DataSource` se dvěma parametry Určuje připojovací řetězec pro zdroj dat a název tabulky, která obsahuje data pro testovací metodu.

Připojovací řetězce závisí na typu typu zdroje dat, ale měl by obsahovat element provider, který určuje neutrální název poskytovatele dat.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Pro přístup k datům použijte TestContext. DataRow.

Pro přístup k datům v tabulce `AddIntegersData` použijte indexer `TestContext.DataRow`. `DataRow` je objekt <xref:System.Data.DataRow>, takže načte hodnoty sloupce podle názvu indexu nebo sloupce. Vzhledem k tomu, že hodnoty jsou vráceny jako objekty, převeďte je na příslušný typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Spustit test a zobrazit výsledky

Po dokončení psaní testovací metody Sestavte projekt testů. Testovací metoda se zobrazí v **Průzkumníku testů** ve skupině **Nespuštěné testy** . Když spouštíte, píšete a znovu spustíte testy, **Průzkumník testů** zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**a **nespustí testy**. Výběrem možnosti **Spustit vše** můžete spustit všechny testy, nebo výběrem možnosti **Spustit** vyberte podmnožinu testů, které chcete spustit.

Pruh výsledků testu v horní části **Průzkumníka testů** je animovaný jako vaše testovací běhy. Na konci testovacího běhu bude pruh zelený, pokud všechny testy byly úspěšné nebo červené, pokud došlo k selhání některého testu. Souhrn testovacího běhu se zobrazí v podokně podrobností v dolní části okna **Průzkumníka testů** . Vyberte test pro zobrazení podrobností testu v dolním podokně.

> [!NOTE]
> Výsledkem je výsledek pro každý řádek dat a také jeden souhrnný výsledek. Pokud byl test úspěšný na každém řádku dat, zobrazí se souhrn, jak bylo **dokončeno**. Pokud se test nezdařil na žádném řádku dat, **zobrazí se souhrn.**

Pokud jste v našem příkladu spustili metodu `AddIntegers_FromDataSourceTest`, panel výsledků se změní na červenou a testovací metoda se přesune na **neúspěšné testy**. Test řízený daty se nezdařil, pokud dojde k chybě některé z iterací metod ze zdroje dat. Když v okně **Průzkumníka testů** zvolíte neúspěšný test řízený daty, v podokně podrobností se zobrazí výsledky každé iterace, která je identifikována indexem řádku dat. V našem příkladu se zobrazí, že algoritmus `AddIntegers` nezpracovává záporné hodnoty správně.

Při opravě testované metody a opětovném spuštění testu se pruh výsledků změní na zelený a testovací metoda je přesunuta do **předané testovací** skupiny.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Zápis testů jednotek pro .NET s využitím rozhraní testování částí společnosti Microsoft](../test/unit-test-your-code.md)
