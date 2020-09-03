---
title: Vytváření testů jednotek řízených daty
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 936c6b2ee9e05d059c09c2aa074829b35b6ca5fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287984"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Postupy: vytvoření testu jednotek řízených daty

Pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód můžete nastavit metodu testování částí pro načtení hodnot ze zdroje dat. Metoda je postupně spouštěna pro každý řádek ve zdroji dat, což usnadňuje testování různých vstupů pomocí jediné metody.

Vytváření testu jednotek řízených daty zahrnuje následující kroky:

1. Vytvořte zdroj dat, který obsahuje hodnoty, které použijete v testovací metodě. Zdroj dat může být jakýkoli typ, který je zaregistrován na počítači, který spouští test.

2. Přidejte soukromé <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole a veřejnou `TestContext` vlastnost do třídy testu.

3. Vytvořte metodu testování částí a přidejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> do ní atribut.

4. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A>K načtení hodnot, které používáte v testu, použijte vlastnost indexer.

## <a name="the-method-under-test"></a>Testovaný způsob

Předpokládejme například, že máte následující:

1. Řešení s názvem `MyBank` , které přijímá a zpracovává transakce pro různé typy účtů.

2. Projekt s `MyBank` názvem `BankDb` , který spravuje transakce pro účty.

3. Třída volaná `Maths` v `BankDb` projektu, která provádí matematické funkce, aby zajistila, že je každá transakce pro banku výhodná.

4. Projekt testu jednotek volal `BankDbTests` k otestování chování `BankDb` komponenty.

5. Třída testu jednotek volaná `MathsTests` pro ověření chování `Maths` třídy.

Otestujeme metodu v `Maths` , která přidá dvě celá čísla pomocí smyčky:

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

Chcete-li otestovat `AddIntegers` metodu, vytvořte zdroj dat, který určuje rozsah hodnot pro parametry a součet, který chcete vrátit. V tomto příkladu vytvoříme databázi SQL Compact s názvem `MathsData` a tabulku s názvem `AddIntegersData` , která obsahuje následující názvy a hodnoty sloupců.

|Prvníčíslo|Druhéčíslo|Součet|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Přidat TestContext do testovací třídy

Rozhraní testování částí vytvoří `TestContext` objekt pro uložení informací o zdroji dat pro test řízený daty. Rozhraní potom nastaví tento objekt jako hodnotu `TestContext` vlastnosti, kterou vytvoříte.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

V testovací metodě získáte přístup k datům prostřednictvím `DataRow` vlastnosti indexeru `TestContext` .

> [!NOTE]
> .NET Core nepodporuje atribut [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) . Pokud se pokusíte získat přístup k datům testu tímto způsobem v projektu testu jednotek .NET Core nebo UWP, zobrazí se chybová zpráva podobná této **: "TestContext" neobsahuje definici pro vlastnost ' DataRow ' a nebyla nalezena žádná přístupná metoda rozšíření ' DataRow ', která by přijímala první argument typu ' TestContext ' (nechybí Direktiva using nebo odkaz na sestavení?)**.

## <a name="write-the-test-method"></a>Zapsat testovací metodu

Testovací metoda pro `AddIntegers` je poměrně jednoduchá. Pro každý řádek ve zdroji dat zavolejte `AddIntegers` hodnoty sloupce **Prvníčíslo** a **druhéčíslo** jako parametry a ověřte návratovou hodnotu oproti hodnotě sloupce **Sum** :

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

`Assert`Metoda obsahuje zprávu, která zobrazuje `x` `y` hodnoty a neúspěšné iterace. Ve výchozím nastavení jsou hodnoty s přívýrazem () `expected` `actual` již zahrnuty v podrobnostech o neúspěšném testu.

### <a name="specify-the-datasourceattribute"></a>Zadejte DataSourceAttribute

`DataSource`Atribut určuje připojovací řetězec pro zdroj dat a název tabulky, kterou použijete v testovací metodě. Přesné informace v připojovacím řetězci se liší v závislosti na typu zdroje dat, který používáte. V tomto příkladu jsme použili databázi SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atribut DataSource má tři konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor s jedním parametrem používá informace o připojení, které jsou uloženy v souboru *app.config* pro řešení. *DataSourceSettingsName* je název elementu XML v konfiguračním souboru, který určuje informace o připojení.

Použití *app.config* souboru umožňuje změnit umístění zdroje dat bez provedení změn v samotném testu jednotek. Informace o tom, jak vytvořit a použít soubor *app.config* , najdete v tématu [Návod: použití konfiguračního souboru k definování zdroje dat.](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

`DataSource`Konstruktor se dvěma parametry Určuje připojovací řetězec pro zdroj dat a název tabulky, která obsahuje data pro testovací metodu.

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

Pro přístup k datům v `AddIntegersData` tabulce použijte `TestContext.DataRow` indexer. `DataRow` je <xref:System.Data.DataRow> objekt, takže načte hodnoty sloupce podle názvu indexu nebo sloupce. Vzhledem k tomu, že hodnoty jsou vráceny jako objekty, převeďte je na příslušný typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Spustit test a zobrazit výsledky

Po dokončení psaní testovací metody Sestavte projekt testů. Testovací metoda se zobrazí v **Průzkumníku testů** ve skupině **Nespuštěné testy** . Když spouštíte, píšete a znovu spustíte testy, **Průzkumník testů** zobrazí výsledky ve skupinách **neúspěšných testů**, **úspěšných testů**a **nespustí testy**. Výběrem možnosti **Spustit vše** můžete spustit všechny testy, nebo výběrem možnosti **Spustit** vyberte podmnožinu testů, které chcete spustit.

Pruh výsledků testu v horní části **Průzkumníka testů** je animovaný jako vaše testovací běhy. Na konci testovacího běhu bude pruh zelený, pokud všechny testy byly úspěšné nebo červené, pokud došlo k selhání některého testu. Souhrn testovacího běhu se zobrazí v podokně podrobností v dolní části okna **Průzkumníka testů** . Vyberte test pro zobrazení podrobností testu v dolním podokně.

> [!NOTE]
> Výsledkem je výsledek pro každý řádek dat a také jeden souhrnný výsledek. Pokud byl test úspěšný na každém řádku dat, zobrazí se souhrn, jak bylo **dokončeno**. Pokud se test nezdařil na žádném řádku dat, **zobrazí se souhrn.**

Pokud jste `AddIntegers_FromDataSourceTest` v našem příkladu spustili metodu, pruh výsledků se změní na červenou a testovací metoda se přesune na **neúspěšné testy**. Test řízený daty se nezdařil, pokud dojde k chybě některé z iterací metod ze zdroje dat. Když v okně **Průzkumníka testů** zvolíte neúspěšný test řízený daty, v podokně podrobností se zobrazí výsledky každé iterace, která je identifikována indexem řádku dat. V našem příkladu se zobrazí, že `AddIntegers` algoritmus nezpracovává záporné hodnoty správně.

Při opravě testované metody a opětovném spuštění testu se pruh výsledků změní na zelený a testovací metoda je přesunuta do **předané testovací** skupiny.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Zápis testů jednotek pro .NET s využitím rozhraní testování částí společnosti Microsoft](../test/unit-test-your-code.md)
