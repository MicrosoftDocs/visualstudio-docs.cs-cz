---
title: 'Postupy: Vytvoření testu jednotek řízené daty | Dokumentace Microsoftu'
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
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: eeb7efb0c7faa9a2493cfd3f91f6cc4e72408f4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889357"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Postupy: Testy jednotek řízené daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí rozhraní pro testování jednotek Microsoft pro spravovaný kód, můžete nastavit metodu testovací jednotky tak, k načtení hodnoty použité v testovací metodě ze zdroje dat. Metoda se spouští postupně pro každý řádek ve zdroji dat, která usnadňuje testování celé škály vstup pomocí jedné metody.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Testované metody](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
- [Vytvoření zdroje dat](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
- [Přidání TestContext pro třídu testu](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
- [Zápis testovací metody](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
  -   [Zadání atribut](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
  -   [Pomocí TestContext.DataRow pro přístup k datům](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
- [Spuštění testu a zobrazení výsledků](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
  Vytvoření testu jednotek řízené daty zahrnuje následující kroky:  
  
1.  Vytvořte zdroj dat, který obsahuje hodnoty, které můžete použít testovací metody. Zdroj dat může být libovolný typ, který je registrován v počítači, na kterém běží test.  
  
2.  Přidat soukromé <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole a veřejnou `TestContext` vlastnost testovací třídy.  
  
3.  Vytvořit metodu testovací jednotky a přidejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> atribut k němu.  
  
4.  Použít <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> vlastnost indexeru pro načtení hodnoty, které můžete použít v rámci testu.  
  
##  <a name="BKMK_The_method_under_test"></a> Testované metody  
 Jako příklad předpokládejme, že jsme vytvořili:  
  
1. Volá se řešení `MyBank` , který přijme a zpracuje transakce pro různé typy účtů.  
  
2. Projekt v `MyBank` volá `BankDb` , který spravuje transakce pro účty.  
  
3. Třída nazývá `Maths` v `DbBank` projekt, který provádí matematické funkce zajistit, že všechny transakce je výhodné banky.  
  
4. Projekt s názvem testování částí `BankDbTests` otestovat chování `BankDb` komponenty.  
  
5. Testování částí třídu s názvem `MathsTests` ověření chování `Maths` třídy.  
  
   Testujeme metody v `Maths` , který přidá dvou celých čísel pomocí smyčka:  
  
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
  
##  <a name="BKMK_Creating_a_data_source"></a> Vytvoření zdroje dat  
 K testování `AddIntegers` metoda, vytvoříme zdroj dat, která určuje rozsah hodnot pro parametry a součet, který očekáváte, že má být vrácen. V našem příkladu vytvoříme s názvem databáze Sql Compact `MathsData` a tabulku s názvem `AddIntegersData` , který obsahuje následující názvy sloupců a hodnot  
  
|Prvníčíslo|Druhéčíslo|Součet|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Přidání TestContext pro třídu testu  
 Vytvoří rozhraní testování částí `TestContext` objekt pro uložení informace o zdroji dat pro test řízený daty. Tento objekt rozhraní pak nastaví jako hodnotu `TestContext` vlastnost, kterou vytvoříme.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 V testovací metodě, získáte přístup k datům prostřednictvím `DataRow` vlastnost indexer `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Zápis testovací metody  
 Testovací metody pro `AddIntegers` je docela jednoduché. Pro každý řádek ve zdroji dat, říkáme `AddIntegers` s **Prvníčíslo** a **Druhéčíslo** sloupec hodnoty jako parametry a ověříme návratovou hodnotu proti **součet**hodnota sloupce:  
  
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
  
 Všimněte si, že `Assert` metoda obsahuje zprávu, která se zobrazí `x` a `y` hodnoty selhání iterace. Ve výchozím nastavení s potvrzením hodnoty `expected` a `actual`, jsou již zahrnuty podrobnosti o selhání testu.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Zadání atribut  
 `DataSource` Atribut určuje připojovací řetězec pro zdroj dat a název tabulky, který používáte v testovací metodě. Přesné informace v připojovacím řetězci se liší v závislosti na tom, jaký druh zdroje dat, kterou používáte. V tomto příkladu jsme použili SqlServerCe databáze.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Atribut zdroje dat má tři konstruktory.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Konstruktor s jedním parametrem používá informace o připojení, která je uložena v souboru app.config pro řešení. *DataSourceSettingsName* je název elementu Xml v konfiguračním souboru, který určuje informace o připojení.  
  
 Pomocí souboru app.config umožňuje změnit umístění zdroje dat bez změn samotného testu. Informace o tom, jak vytvořit a použít soubor app.config, naleznete v tématu [návod: použití konfiguračního souboru k definování zdroje dat](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 `DataSource` Konstruktor se dvěma parametry Určuje připojovací řetězec pro zdroj dat a název tabulky, která obsahuje data pro testovací metodu.  
  
 Připojovací řetězce závisí na typu zdroje dat, ale měl by obsahovat element zprostředkovatele, který určuje výchozí název zprostředkovatele dat.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Pomocí TestContext.DataRow pro přístup k datům  
 Pro přístup k datům v `AddIntegersData` tabulky, použijte `TestContext.DataRow` indexeru. `DataRow` je <xref:System.Data.DataRow> objektu, tak se nám načíst hodnoty sloupců podle názvů index nebo sloupec. Protože hodnoty jsou vráceny jako objekty, potřebujeme je převést na typ odpovídající:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Spuštění testu a zobrazení výsledků  
 Po dokončení zápisu testovací metody vytvoření testovacího projektu. Testovací metoda se zobrazí v okně Průzkumníka testů v **nespuštěné testy** skupiny. Jak spustit, zápis a znovu spouštěny, zobrazuje Průzkumník testů výsledky ve skupinách **neúspěšné testy**, **úspěšné testy**, a **nespuštěné testy**. Můžete zvolit **spustit všechny** chcete spustit všechny testy, nebo zvolte **spuštění...**  vybrat podmnožinu testů ke spuštění.  
  
 Panel výsledků testu v horní části stránky Průzkumníka je animovaný při spuštění testu. Na konci testovacího běhu panelu budou zelené, pokud všechny testy prošly nebo red Pokud některé testy selhaly. Přehled testovacího běhu se zobrazí v podokně podrobností v dolní části okna Průzkumníka testů. Vyberte test, chcete-li zobrazit podrobnosti o testu v dolním podokně.  
  
 Pokud jste spustili `AddIntegers_FromDataSourceTest` metoda v našem příkladu, na panelu výsledků na červenou a testovací metoda je přesunuta do **neúspěšné testy** test řízený daty selže, pokud iterovaném metod z dat zdroje se nezdaří. Když vyberete selhání testu s daty v okně Průzkumník testů, zobrazí v podokně podrobností výsledky každé iterace, která je identifikovaná index řádku dat. V našem příkladu zdá se, `AddIntegers` algoritmus nezpracovává záporné hodnoty správně.  
  
 Při nápravě testované metody a test spustit znovu, výsledky panel zbarví zeleně a testovací metoda je přesunuta do **předaný testování** skupiny.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Postupy: vytváření a spouštění testování částí](http://msdn.microsoft.com/en-us/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Testování částí kódu](../test/unit-test-your-code.md)   
 [Spouštění testů jednotek pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)   
 [Zápis testů částí pro rozhraní .NET Framework s infrastrukturou pro testování částí Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)



