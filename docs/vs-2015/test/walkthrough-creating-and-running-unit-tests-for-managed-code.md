---
title: 'Návod: Vytváření a spouštění testů jednotek pro spravovaný kód | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50d8190f386a4923fd05cbfaec137791bd9f2b5a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874498"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Postupy: Vytváření a spouštění testů jednotek pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vás postupně provede vytváření, spouštění a přizpůsobením série jednotkových testů pomocí rozhraní pro testování jednotek Microsoft pro spravovaný kód a Visual Studio Test Explorer. Spustit u projektu C#, která je ve vývoji, vytvoříte testy, které testují jeho kód, spusťte testy a podívejte se na výsledky. Můžete změnit kód projektu a znovu spusťte testy.  
  
 Toto téma obsahuje následující oddíly:  
  
 [Příprava návodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Vytvoření projektu pro testování částí](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Vytvoření testovací třídy](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
- [Požadavky na testovací třídu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
  [Vytvoření první testovací metody](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
- [Požadavky na testovací metodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
  [Sestavení a spuštění testu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
  [Oprava kódu a znovu spustit testy](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
  [Použití jednotkových testů ke zlepšení kódu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
>  Tento návod používá rozhraní testování částí Microsoft pro spravovaný kód. Průzkumník testů může také spouštět testy z jednotky třetí strany rozhraní pro testování, které mají adaptéry pro Průzkumník testů. Další informace najdete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)  
  
> [!NOTE]
>  Informace o tom, ke spuštění testů z příkazového řádku najdete v tématu [návod: použití testování z příkazového řádku](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Projekt banky. Zobrazit [ukázkový projekt testování částí](../test/sample-project-for-creating-unit-tests.md).  
  
##  <a name="BKMK_Prepare_the_walkthrough"></a> Příprava návodu  
  
1. Otevřít Visual Studio.  
  
2. Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.  
  
    **Nový projekt** zobrazí se dialogové okno.  
  
3. V části **nainstalované šablony**, klikněte na tlačítko **Visual C#**.  
  
4. V seznamu typů aplikací, klikněte na tlačítko **knihovny tříd**.  
  
5. V **název** zadejte `Bank` a potom klikněte na tlačítko **OK**.  
  
   > [!NOTE]
   >  Pokud již název "Banka" používán, zvolte jiný název projektu.  
  
    Nový projekt banka se vytvoří a zobrazí v Průzkumníku řešení se soubor Class1.cs je otevřen v editoru kódu.  
  
   > [!NOTE]
   >  Pokud soubor Class1.cs není otevřen v editoru kódu, dvakrát klikněte na soubor Class1.cs v Průzkumníku řešení otevřete.  
  
6. Zkopírujte zdrojový kód z [ukázkový projekt pro vytvoření testů jednotek](../test/sample-project-for-creating-unit-tests.md).  
  
7. Nahraďte původní obsah souboru Class1.cs kódem z [ukázkový projekt pro vytvoření testů jednotek](../test/sample-project-for-creating-unit-tests.md).  
  
8. Uložte soubor jako BankAccount.cs  
  
9. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
   Nyní máte projekt s názvem banka. Obsahuje zdrojový kód pro testování a nástroje a otestovat ho s. Obor názvů pro banku, **BankAccountNS**, obsahuje veřejnou třídu **BankAccount**, jejíž metody budete testovat v následujících postupech.  
  
   V tomto rychlém startu se zaměříme na `Debit` metody. MD metoda je volána, když jsou peníze účtu a obsahuje následující kód:  
  
```csharp  
// method under test  
public void Debit(double amount)  
{  
    if(amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount");  
    }  
    m_balance += amount;  
}  
  
```  
  
##  <a name="BKMK_Create_a_unit_test_project"></a> Vytvořte projekt testu jednotek  
 **Požadovaný**: postupujte podle kroků v postupu [Příprava návodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Chcete-li vytvořit projekt testování částí  
  
1.  Na **souboru** nabídce zvolte **přidat**a klikněte na tlačítko **nový projekt...** .  
  
2.  V dialogovém okně Nový projekt rozbalte **nainstalováno**, rozbalte **Visual C#** a klikněte na tlačítko **Test**.  
  
3.  V seznamu šablon vyberte **projekt testu jednotek**.  
  
4.  V **název** pole, zadejte hodnotu BankTest a potom zvolte **OK**.  
  
     **BankTests** projekt je přidán do **Bank** řešení.  
  
5.  V **BankTests** projektu, přidejte odkaz na **Bank** řešení.  
  
     V Průzkumníku řešení vyberte **odkazy** v **BankTests** projektu a klikněte na tlačítko **přidat odkaz...**  v místní nabídce.  
  
6.  V dialogovém okně Správce odkazů rozbalte **řešení** a potom zaškrtněte políčko **Bank** položky.  
  
##  <a name="BKMK_Create_the_test_class"></a> Vytvoření testovací třídy  
 Potřebujeme třídu testu pro ověření `BankAccount` třídy. Můžeme použít UnitTest1.cs vygenerovanou šablonu projektu, ale jsme měli dát souboru a třídě více popisné názvy. Můžeme to udělat v jednom kroku přejmenováním souboru v Průzkumníku řešení.  
  
 **Přejmenování souboru třídy**  
  
 V Průzkumníku řešení zvolte soubor UnitTest1.cs v projektu BankTests. V místní nabídce zvolte **přejmenovat**a potom přejmenujte soubor na BankAccountTests.cs. Zvolte **Ano** v dialogovém okně s dotazem, jestli chcete přejmenování všech referencí v projektu na prvek kódu "UnitTest1". Tento krok změní název třídy, která se `BankAccountTest`.  
  
 Soubor BankAccountTests.cs nyní obsahuje následující kód:  
  
```csharp  
// unit test code  
using System;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
namespace BankTests  
{  
    [TestClass]  
    public class BankAccountTests  
    {  
        [TestMethod]  
        public void TestMethod1()  
        {  
        }  
    }  
}  
```  
  
 **Přidat sadu pomocí příkazu testovaného projektu**  
  
 Můžeme také přidat sadu pomocí příkazu do třídy a dejte nám chcete-li volat Testovaný projekt bez použití plně kvalifikovaných názvů. V horní části souboru třídy přidejte:  
  
```csharp  
using BankAccountNS;  
```  
  
###  <a name="BKMK_Test_class_requirements"></a> Požadavky na testovací třídu  
 Minimální požadavky na testovací třídu jsou následující:  
  
- `[TestClass]` Atribut je požadován v testování části Microsoft framework pro spravovaný kód pro libovolnou třídu obsahující metody jednotkového testu, které chcete spustit v aplikaci Test Explorer.  
  
- Každá testovací metoda, která má být spuštěna Průzkumníkem testů musí mít `[TestMethod]`atribut.  
  
  Můžete mít další třídy v projektu testů jednotek, které nemají `[TestClass]` atribut který může mít jiné metody v testovacích třídách, které nemají `[TestMethod]` atribut. Ve vašich testovacích metodách můžete použít tyto třídy a metody.  
  
##  <a name="BKMK_Create_the_first_test_method"></a> Vytvoření první testovací metody  
 V tomto postupu, napíšeme v testování částí, metody, které ověří chování `Debit` metodu `BankAccount` třídy. Metoda je uvedena výše.  
  
 Analýzou testované metody ověříme, že existují aspoň tři typy chování, které je potřeba zkontrolovat:  
  
1. Metoda vyvolá [ArgumentOutOfRangeException] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->) Pokud je hodnota debetní větší než zůstatek na účtu.  
  
2. Vyvolá také `ArgumentOutOfRangeException` Pokud debetní velikost je menší než nula.  
  
3. Pokud kontroly v 1.) a 2.) jsou splněny, metoda odečte požadovanou částku od zůstatku účtu.  
  
   V prvním testu ověříme, že platná částka (která je menší než zůstatek na účtu a je větší než nula) stáhne z účtu objektu správnou velikost.  
  
#### <a name="to-create-a-test-method"></a>Vytvoření testovací metody  
  
1. Přidat using `BankAccountNS;` příkazu do souboru BankAccountTests.cs.  
  
2. Přidejte následující metodu do `BankAccountTests` třídy:  
  
   ```csharp  
   // unit test code  
   [TestMethod]  
   public void Debit_WithValidAmount_UpdatesBalance()  
   {  
       // arrange  
       double beginningBalance = 11.99;  
       double debitAmount = 4.55;  
       double expected = 7.44;  
       BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
       // act  
       account.Debit(debitAmount);  
  
       // assert  
       double actual = account.Balance;  
       Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");  
   }  
   ```  
  
   Metoda je velmi jednoduchá. Doporučujeme nastavit nový `BankAccount` objekt s počáteční zůstatek a potom zrušit platnou částku. Používáme rozhraní testování částí Microsoft pro spravovaný kód <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metodu k ověření, že je konečný zůstatek, co očekávat.  
  
###  <a name="BKMK_Test_method_requirements"></a> Požadavky na testovací metodu  
 Testovací metoda musí splňovat následující požadavky:  
  
-   Metoda musí být doplněny pomocí `[TestMethod]` atribut.  
  
-   Metoda musí vracet `void`.  
  
-   Metoda nemůže mít parametry.  
  
##  <a name="BKMK_Build_and_run_the_test"></a> Sestavení a spuštění testu  
  
#### <a name="to-build-and-run-the-test"></a>Sestavte a spusťte test  
  
1.  Na **sestavení** nabídce zvolte **sestavit řešení**.  
  
     Pokud nejsou žádné chyby, zobrazí se okno UnitTestExplorer **Debit_WithValidAmount_UpdatesBalance** uvedené v **nespuštěné testy** skupiny. Pokud po úspěšném sestavení nezobrazí Průzkumník testů, zvolte **testovací** v nabídce klikněte na tlačítko **Windows**a klikněte na tlačítko **Průzkumník testů**.  
  
2.  Zvolte **spustit všechny** pro spuštění testu. Je jako test běží na stavovém řádku v horní části okna animovaný. Na konci testovacího běhu stavový řádek zezelená, pokud všechny testovací metody proběhly úspěšně nebo red Pokud selže některý z testů.  
  
3.  V tomto případě test selhal. Testovací metoda je přesunuta do **neúspěšné testy**. Skupina. Vyberte metodu v Průzkumníku testů k zobrazení podrobností v dolní části okna.  
  
##  <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Oprava kódu a znovu spustit testy  
 **Analýza výsledků testování**  
  
 Výsledek testu obsahuje zprávu s popisem chyby. Pro `AreEquals` metoda, zpráva zobrazí očekávaným ((<strong>očekávaná\<*XXX*></strong>parametr) a co vlastně přijatých ( **Skutečné\<*YYY* >** parametr). Očekávali jsme zůstatek zůstatku, ale místo toho se zvýšila množství stažení.  
  
 Přezkoumání kódu ukazuje, že Jednotkový test proběhl úspěšně chybu. Množství stažení se přidá do zůstatek na účtu, když by měl být odečtena.  
  
 **Oprava chyby**  
  
 Chcete-li opravit chybu, jednoduše nahraďte řádek  
  
```csharp  
m_balance += amount;  
```  
  
 with  
  
```csharp  
m_balance -= amount;  
```  
  
 **Opětovné provedení testu**  
  
 V Průzkumníku testů zvolte **spustit všechny** na opětovné spuštění testu. Červeného/zeleného stavového řádku se změní na zelenou a test je přesunut do **úspěšné testy** skupiny.  
  
##  <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Použití jednotkových testů ke zlepšení kódu  
 Tato část popisuje, jak může iterativní proces analýzy, vývoj jednotkových testů a refaktoring pomoci vám robustnějšího a efektivnějšího produkčního kódu.  
  
 **Analýza problémů**  
  
 Po vytvoření testovací metody pro potvrzení, že platná částka se správně odečte v `Debit` metody jsme můžete zapnout zbývajícími případy původní analýzy:  
  
1. Metoda vyvolá `ArgumentOutOfRangeException` Pokud debetní velikost je větší než zůstatek na účtu.  
  
2. Vyvolá také `ArgumentOutOfRangeException` Pokud debetní velikost je menší než nula.  
  
   **Vytvoření testovacích metod**  
  
   První pokus o vytvoření testovací metody pro řešení těchto problémů, vypadá slibně:  
  
```csharp  
//unit test method  
[TestMethod]  
[ExpectedException(typeof(ArgumentOutOfRangeException))]  
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = -100.00;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    account.Debit(debitAmount);  
  
    // assert is handled by ExpectedException  
}  
  
```  
  
 Používáme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut k vyhodnocení, že byla vyvolána správná výjimka. Atribut způsobí, že se test nezdaří, pokud `ArgumentOutOfRangeException` je vyvolána výjimka. Spuštění testu s kladnými i negativní `debitAmount` hodnoty a následná dočasná změna testované vyvolána obecná výjimka metody <xref:System.ApplicationException> když velikost je menší než nula ukazuje správné chování testu. K otestování případu, kdy vybíraná hodnota je větší než zůstatek, vše, co musíme udělat je:  
  
1. Vytvořit novou testovací metodu s názvem `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2. Zkopírovat tělo metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nové metody.  
  
3. Nastavte `debitAmount` na číslo větší než zůstatek na účtu.  
  
   **Spustit testy**  
  
   Spuštění těchto dvou metod s různými hodnotami parametru `debitAmount` ukazuje, že testy vhodně ověřují zbývající případy. Spuštění všech tří testů potvrzuje, že všechny případy původní analýzy jsou správně pokryty.  
  
   **Pokračování analýzy**  
  
   Dvě poslední metody testování jsou však také poněkud problematické. Není možné si být určité která podmínka testovaného kódu byla vyvolána při provádění těchto testů. Nějaký způsob odlišení těchto dvou podmínek by být užitečné. Jako jsme přemýšlení o tomto problému další, je zřejmé, že znalost, která podmínka porušení by zvýšila důvěru v testech. Tyto informace by také pravděpodobně mohla být užitečná pro produkční mechanismus, který zpracovává výjimku vyvolanou testovanou metodou. Generování dalších informací, vyvolá metoda výjimku pomáhá všech zúčastněných, ale `ExpectedException` atribut nedokáže s takovou informací...  
  
   Testované metody znova podíváme, vidíme oba podmíněné příkazy používají `ArgumentOutOfRangeException` konstruktor, který přebírá název argumentu, který jako parametr:  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 Pomocí hledání v knihovně MSDN zjistíme, že existuje konstruktor poskytující mnohem bohatší informace. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` obsahuje název argumentu, hodnotu argumentu a uživatelsky definovanou zprávu. Možné provést refaktoring testované používala tento konstruktor metody. Ještě lepší můžeme použít veřejně dostupné členy typů ke specifikaci chyb.  
  
 **Refaktoring testovaného kódu**  
  
 Nejprve definujte dvě konstanty pro chybové zprávy v oboru třídy:  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Poté upravíme dva podmíněné příkazy v `Debit` metody:  
  
```csharp  
// method under test  
// ...  
    if (amount > m_balance)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);  
    }  
  
    if (amount < 0)  
    {  
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);  
    }  
// ...  
```  
  
 **Refaktoring testovacích metod**  
  
 V testovací metodě nejprve odeberte `ExpectedException` atribut. Místo toho jsme zachyťte vyvolanou výjimku a ověřte, že byla vyvolána ve správném podmíněném příkazu. Však musí nyní rozhodneme mezi dvěma možnostmi, jak ověřit zbývající podmínky. Například v `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` metodu, můžete provést jednu z následujících akcí:  
  
- Vyhodnotit, že `ActualValue` vlastnosti výjimky (druhý parametr `ArgumentOutOfRangeException` konstruktoru) je větší než počáteční zůstatek. Tato možnost vyžaduje otestování `ActualValue` vlastnosti výjimky proti `beginningBalance` proměnných testovací metody a taky vyžaduje pak ověřte, že `ActualValue` je větší než nula.  
  
- Vyhodnocení, že zpráva (třetí parametr konstruktoru) obsahuje `DebitAmountExceedsBalanceMessage` definované v `BankAccount` třídy.  
  
  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda v rozhraní testování částí Microsoft umožňuje ověřit druhou možnost bez nutnosti výpočtů potřebných v první možnosti.  
  
  Druhý pokus revize metody `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` může vypadat například takto:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
    }  
}  
```  
  
 **Opětovné testování, revize a analýza**  
  
 Při opakovaném testování testovacích metod s různými hodnotami, dojde k následujícím skutečnostem:  
  
1. Pokud jsme zachycení správné chyby pomocí assert kde `debitAmount` , který je větší než zůstatek na účtu `Contains` předá assert, výjimka bude ignorována a proto testovací metoda skončí úspěchem. Toto je chování, které chceme.  
  
2. Při použití `debitAmount` , která je menší než 0, vyhodnocení selže, protože je vrácena nesprávná chybová zpráva. Vyhodnocení také selže, pokud je zavedena dočasná `ArgumentOutOfRange` výjimky na jiném místě testované metody. Toto chování je také vhodné.  
  
3. Pokud `debitAmount` je hodnota platná (to znamená, menší než zůstatek, ale větší než nula, žádná výjimka je zachycena, proto nikdy zachycuje assert. Testovací metoda skončí úspěchem. To není správné, protože chceme, aby testovací metoda selhat, pokud není vyvolána žádná výjimka.  
  
   Třetí fakt je chybou v testovací metodě. Pokus o vyřešení problému se nám přidat <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> uplatnit na konci testovací metody pro zpracování případu, kdy není vyvolána žádná výjimka.  
  
   Ale opakované ukazuje, že test nyní selže, pokud k zachycení správné výjimky. Příkaz catch zruší výjimku a metoda pokračuje v provádění, selhání nově přidaného. Chcete-li vyřešit tento problém, přidáme `return` příkazem za `StringAssert`. Opakované potvrdí, že jsme vyřešili naše problémy. Konečná verze `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` vypadá následovně:  
  
```csharp  
[TestMethod]  
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()  
{  
    // arrange  
    double beginningBalance = 11.99;  
    double debitAmount = 20.0;  
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);  
  
    // act  
    try  
    {  
        account.Debit(debitAmount);  
    }  
    catch (ArgumentOutOfRangeException e)  
    {  
        // assert  
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);  
        return;  
    }  
    Assert.Fail("No exception was thrown.");  
}  
  
```  
  
 V této závěrečné sekci vedlo pracovní, vylepšení testovacího kódu k robustnějším a informativnějším testovací metody. Ale důležitější je, že další analýza také vedla k vylepšení kódu testovaného projektu.



