---
title: Vytvořit testy jednotek řízených daty
ms.date: 05/08/2019
ms.topic: conceptual
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
ms.openlocfilehash: f50dad637d9efa2db347ff9f1b4828abf8c733af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589185"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Postup: Vytvoření testu částí řízených daty

K nastavení metody testování částí pro načtení hodnot ze zdroje dat můžete použít rozhraní Microsoft pro testování částí pro spravovaný kód. Metoda je spuštěna postupně pro každý řádek ve zdroji dat, což usnadňuje testování různých vstupů pomocí jediné metody.

Vytvoření testování částí řízených daty zahrnuje následující kroky:

1. Vytvořte zdroj dat, který obsahuje hodnoty, které používáte v testovací metodě. Zdrojem dat může být libovolný typ, který je registrován v počítači, který spustí test.

2. Přidejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> soukromé pole `TestContext` a veřejnou vlastnost do testovací třídy.

3. Vytvořte metodu testování <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> částí a přidejte do ní atribut.

4. Pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> vlastnosti indexeru načtěte hodnoty, které používáte v testu.

## <a name="the-method-under-test"></a>Zkoušená metoda

Jako příklad předpokládejme, že máte:

1. Řešení s `MyBank` názvem, které přijímá a zpracovává transakce pro různé typy účtů.

2. Projekt v `MyBank` `BankDb` volání, který spravuje transakce pro účty.

3. Třída `Maths` volaná `BankDb` v projektu, která provádí matematické funkce, aby bylo zajištěno, že každá transakce je výhodná pro banku.

4. Projekt testování částí `BankDbTests` volána k `BankDb` testování chování komponenty.

5. Jednotka testovací třídy volána `MathsTests` k `Maths` ověření chování třídy.

Otestujeme `Maths` metodu, která přidá dvě celá čísla pomocí smyčky:

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

Chcete-li `AddIntegers` metodu otestovat, vytvořte zdroj dat, který určuje rozsah hodnot pro parametry a součet, který očekáváte, že bude vrácen. V tomto příkladu vytvoříme databázi `MathsData` SQL Compact `AddIntegersData` s názvem a tabulku s názvem obsahující následující názvy sloupců a hodnoty

|První číslo|Druhé číslo|Součet|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Přidejte TestContext do testovací třídy

Rozhraní testování částí `TestContext` vytvoří objekt pro uložení informací o zdroji dat pro test řízený daty. Rámec pak nastaví tento objekt `TestContext` jako hodnotu vlastnosti, kterou vytvoříte.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

V testovací metodě přístup k `DataRow` datům prostřednictvím `TestContext`indexeru vlastnost .

> [!NOTE]
> Rozhraní .NET Core nepodporuje atribut [DataSource.](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) Pokud se pokusíte o přístup k testovacím datům tímto způsobem v projektu testování částí .NET Core nebo UPW, zobrazí se chyba podobná **"'TestContext' neobsahuje definici pro 'DataRow' a žádná přístupná rozšiřující metoda 'DataRow' přijetí prvního argumentu typu "TestContext" by mohl být nalezen (chybí vám using directive nebo odkaz na sestavení?)"**.

## <a name="write-the-test-method"></a>Napište testovací metodu

Zkušební metoda `AddIntegers` pro je poměrně jednoduchá. Pro každý řádek ve zdroji `AddIntegers` dat volejte s hodnotami sloupce **FirstNumber** a **SecondNumber** jako parametry a ověřte vrácenou hodnotu oproti hodnotě sloupce **Sum:**

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

Metoda `Assert` obsahuje zprávu, která `x` `y` zobrazuje hodnoty a neúspěšné iterace. Ve výchozím nastavení jsou `expected` uplatně hodnoty - a `actual` - již zahrnuty v podrobnostech neúspěšného testu.

### <a name="specify-the-datasourceattribute"></a>Určení atributu Zdroje dat

Atribut `DataSource` určuje připojovací řetězec pro zdroj dat a název tabulky, kterou používáte v testovací metodě. Přesné informace v připojovacím řetězci se liší v závislosti na tom, jaký druh zdroje dat používáte. V tomto příkladu jsme použili databázi SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Atribut DataSource má tři konstruktory.

```csharp
[DataSource(dataSourceSettingName)]
```

Konstruktor s jedním parametrem používá informace o připojení, které jsou uloženy v souboru *app.config* pro řešení. *DataSourceSettingsName* je název elementu Xml v konfiguračním souboru, který určuje informace o připojení.

Použití souboru *app.config* umožňuje změnit umístění zdroje dat bez provedení změn v samotném testu jednotky. Informace o vytvoření a použití souboru *app.config* naleznete v [tématu Návod: Definování zdroje dat pomocí konfiguračního souboru](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

Konstruktor `DataSource` se dvěma parametry určuje připojovací řetězec pro zdroj dat a název tabulky, která obsahuje data pro testovací metodu.

Připojovací řetězce závisí na typu typu zdroje dat, ale měl by obsahovat prvek Provider, který určuje nevariantní název zprostředkovatele dat.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Použití testContext.DataRow pro přístup k datům

Chcete-li získat `AddIntegersData` přístup k `TestContext.DataRow` datům v tabulce, použijte indexer. `DataRow`je <xref:System.Data.DataRow> objekt, takže načtěte hodnoty sloupců podle názvů indexů nebo sloupců. Protože jsou hodnoty vráceny jako objekty, převeďte je na příslušný typ:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Spuštění testu a zobrazení výsledků

Po dokončení psaní testovací metody vytvořte testovací projekt. Testovací metoda se zobrazí v **Průzkumníku testů** ve skupině **Nespustit testy.** Při spuštění, zápisu a opětovném spuštění testů **průzkumník testů** zobrazí výsledky ve skupinách **neúspěšných testů**, **Předané testy**a **Nespouštět testy**. Můžete zvolit **Spustit vše** pro spuštění všech testů nebo zvolte **Spustit** a zvolte podmnožinu testů, které chcete spustit.

Panel výsledků testů v horní části **Průzkumníka testů** je animován při spuštění testu. Na konci testu bude pruh zelený, pokud všechny testy prošly, nebo červeně, pokud některý z testů selhal. Souhrn testovacího běhu se zobrazí v podokně podrobností v dolní části okna **Průzkumníka testů.** Vyberte test pro zobrazení podrobností tohoto testu v dolním podokně.

> [!NOTE]
> Existuje výsledek pro každý řádek dat a také jeden souhrnný výsledek. Pokud test prošel na každém řádku dat, souhrnné spuštění se zobrazí jako **Předáno**. Pokud se test nezdařil na libovolném řádku dat, souhrnné spuštění se zobrazí jako **Neúspěšné**.

Pokud jste `AddIntegers_FromDataSourceTest` spustili metodu v našem příkladu, panel výsledků se změní na červenou a testovací metoda se přesune na **neúspěšné testy**. Test řízený daty se nezdaří, pokud se nezdaří některá z iterovaných metod ze zdroje dat. Když zvolíte neúspěšný test řízený daty v okně **Průzkumník testů,** podokno podrobností zobrazí výsledky každé iterace, která je identifikována indexem řádků dat. V našem příkladu `AddIntegers` se zdá, že algoritmus nezpracovává záporné hodnoty správně.

Při korekci testované metody a opakování testu se panel výsledků změní na zelenou a zkušební metoda se přesune do skupiny **Předátek testu.**

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)
- [Zápis testů částí pro rozhraní .NET pomocí architektury testování částí společnosti Microsoft](../test/unit-test-your-code.md)
