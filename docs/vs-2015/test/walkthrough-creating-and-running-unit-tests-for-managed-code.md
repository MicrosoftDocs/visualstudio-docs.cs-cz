---
title: 'Návod: vytváření a spouštění testů jednotek pro spravovaný kód | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 631a180789f5fff373799b78222c25a50ab32912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657093"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Postupy: Vytváření a spouštění testů jednotek pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vás provede vytvořením, spuštěním a přizpůsobením řady testů jednotek pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód a Průzkumníka testů sady Visual Studio. Začínáte s projektem C#, který je ve vývoji, vytváříte testy, které vykonávají svůj kód, spouštíte testy a prohlížíte výsledky. Pak můžete změnit kód projektu a znovu spustit testy.

 Toto téma obsahuje následující oddíly:

 [Příprava návodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [Vytvoření projektu testování částí](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [Vytvořit testovací třídu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

- [Požadavky na testovací třídu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

  [Vytvoření první testovací metody](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

- [Požadavky na testovací metodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

  [Sestavit a spustit test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

  [Opravte kód a znovu spusťte testy.](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

  [Použití jednotkových testů ke zlepšení kódu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
> Tento návod používá pro spravovaný kód rozhraní testování částí společnosti Microsoft. Průzkumník testů také může spouštět testy z rozhraní pro testování částí třetích stran, které mají adaptéry pro Průzkumník testů. Další informace najdete v tématu [instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md) .

> [!NOTE]
> Informace o tom, jak spustit testy z příkazového řádku, naleznete v tématu [Návod: použití nástroje pro testování z příkazového řádku](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Předpoklady

- Projekt banky. Prohlédněte si [ukázkový projekt pro vytváření testů jednotek](../test/sample-project-for-creating-unit-tests.md).

## <a name="prepare-the-walkthrough"></a><a name="BKMK_Prepare_the_walkthrough"></a> Příprava návodu

1. Otevřete sadu Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

    Zobrazí se dialogové okno **Nový projekt**.

3. V části **Nainstalované šablony**klikněte na položku **Visual C#**.

4. V seznamu typů aplikací klikněte na **Knihovna tříd**.

5. Do pole **název** zadejte `Bank` a pak klikněte na **OK**.

   > [!NOTE]
   > Pokud je název "banka" již použit, vyberte jiný název projektu.

    Vytvoří se nový bankový projekt, který se zobrazí v Průzkumník řešení se souborem Class1.cs otevřeným v editoru kódu.

   > [!NOTE]
   > Pokud soubor Class1.cs není otevřen v editoru kódu, otevřete ho tak, že dvakrát kliknete na soubor Class1.cs v Průzkumník řešení.

6. Zkopírujte zdrojový kód z [ukázkového projektu pro vytváření testů jednotek](../test/sample-project-for-creating-unit-tests.md).

7. Nahraďte původní obsah Class1.cs kódem z [ukázkového projektu pro vytváření testů jednotek](../test/sample-project-for-creating-unit-tests.md).

8. Uložit soubor jako BankAccount.cs

9. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   Nyní máte projekt s názvem bank. Obsahuje zdrojový kód pro testování a nástroje pro otestování pomocí. Obor názvů pro banku, **BankAccountNS**, obsahuje veřejnou třídu **BankAccount**, jejíž metody budete testovat v následujících postupech.

   V tomto rychlém startu se zaměříme na `Debit` metodu. Metoda MD je volána, když je peníze odebrán účet a obsahuje následující kód:

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

## <a name="create-a-unit-test-project"></a><a name="BKMK_Create_a_unit_test_project"></a> Vytvořit projekt testu jednotek
 **Předpoklad**: postupujte podle kroků v postupu a [Připravte návod](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).

#### <a name="to-create-a-unit-test-project"></a>Vytvoření projektu testu jednotek

1. V nabídce **soubor** klikněte na položku **Přidat**a poté zvolte možnost **Nový projekt...**.

2. V dialogovém okně Nový projekt rozbalte položku **nainstalované**, **Visual C#** a pak zvolte možnost **test**.

3. V seznamu šablon vyberte možnost **projekt testování částí**.

4. Do pole **název** zadejte BankTest a pak zvolte **OK**.

     Projekt **BankTests** se přidá do řešení **bank** .

5. V projektu **BankTests** přidejte odkaz na řešení **banky** .

     V Průzkumník řešení vyberte **odkazy** v projektu **BankTests** a pak zvolte **Přidat odkaz...** z kontextové nabídky.

6. V dialogovém okně Správce odkazů rozbalte položku **řešení** a poté zkontrolujte položku **banka** .

## <a name="create-the-test-class"></a><a name="BKMK_Create_the_test_class"></a> Vytvořit testovací třídu
 Pro ověření třídy potřebujeme testovací třídu `BankAccount` . Můžeme použít UnitTest1.cs, který byl vygenerován šablonou projektu, ale měli byste zadat výstižnější název souboru a třídy. To můžete provést v jednom kroku přejmenováním souboru v Průzkumník řešení.

 **Přejmenování souboru třídy**

 V Průzkumník řešení vyberte soubor UnitTest1.cs v projektu BankTests. V místní nabídce zvolte možnost **Přejmenovat**a potom přejmenujte soubor na BankAccountTests.cs. V dialogovém okně s dotazem, zda chcete přejmenovat všechny odkazy v projektu na prvek kódu ' UnitTest1 ', vyberte **Ano** . Tento krok změní název třídy na `BankAccountTest` .

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

 **Přidejte příkaz using do testovaného projektu**

 Do třídy můžeme také přidat příkaz using, který nám umožní zavolat do testovaného projektu bez použití plně kvalifikovaných názvů. V horní části souboru třídy přidejte:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a><a name="BKMK_Test_class_requirements"></a> Požadavky na testovací třídu
 Minimální požadavky na testovací třídu jsou následující:

- `[TestClass]`Atribut je vyžadován v rozhraní testování částí společnosti Microsoft pro spravovaný kód pro jakoukoliv třídu, která obsahuje metody testování částí, které chcete spustit v Průzkumníku testů.

- Každá testovací metoda, kterou má Průzkumník testů spustit, musí mít `[TestMethod]` atribut.

  Můžete mít jiné třídy v projektu testu jednotek, které nemají `[TestClass]` atribut, a můžete mít jiné metody v testovacích třídách, které nemají `[TestMethod]` atribut. Tyto další třídy a metody můžete použít v testovacích metodách.

## <a name="create-the-first-test-method"></a><a name="BKMK_Create_the_first_test_method"></a> Vytvoření první testovací metody
 V tomto postupu zapíšeme metody testování částí, abychom ověřili chování `Debit` metody `BankAccount` třídy. Metoda je uvedena výše.

 Analýzou testované metody určíme, že existuje alespoň tři chování, která je potřeba zkontrolovat:

1. Metoda vyvolá [ArgumentOutOfRangeException] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->), pokud je částka MD větší než zůstatek.

2. Vyvolá se také v `ArgumentOutOfRangeException` případě, že je částka MD menší než nula.

3. Pokud se kontrolují v části 1.) a 2.) jsou splněny, metoda odečte částku od zůstatku účtu.

   V našem prvním testu Ověřujeme, že platná částka (jedna, která je menší než zůstatek účtu a která je větší než nula) stáhne ze účtu správnou částku.

#### <a name="to-create-a-test-method"></a>Vytvoření testovací metody

1. Přidejte příkaz using `BankAccountNS;` do souboru BankAccountTests.cs.

2. Do této třídy přidejte následující metodu `BankAccountTests` :

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

   Metoda je spíše jednoduchá. Nastavíme nový `BankAccount` objekt s počátečním zůstatkem a pak odebereme platnou částku. Pro <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> ověření, že koncový zůstatek je to, co očekáváme, používáme metodu Microsoft Unit Test Framework pro spravovaný kód.

### <a name="test-method-requirements"></a><a name="BKMK_Test_method_requirements"></a> Požadavky na testovací metodu
 Testovací metoda musí splňovat následující požadavky:

- Metoda musí být upravena `[TestMethod]` atributem.

- Metoda musí vracet `void` .

- Metoda nemůže mít parametry.

## <a name="build-and-run-the-test"></a><a name="BKMK_Build_and_run_the_test"></a> Sestavit a spustit test

#### <a name="to-build-and-run-the-test"></a>Sestavení a spuštění testu

1. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

     V případě, že nejsou k dispozici žádné chyby, zobrazí se okno UnitTestExplorer s **Debit_WithValidAmount_UpdatesBalance** uvedeným ve skupině **Nespuštěné testy** . Pokud se Průzkumník testů nezobrazí po úspěšném sestavení, zvolte možnost **test** v nabídce a pak zvolte možnost **Windows**a pak zvolte možnost  **Průzkumník testů**.

2. Kliknutím na možnost **Spustit vše** spusťte test. Při spuštění testu se v horní části okna zobrazuje stavový řádek, který je animovaný. Na konci testovacího běhu se pruh změní na zelený, pokud jsou všechny testovací metody úspěšné, nebo červené, pokud některý z testů selže.

3. V tomto případě test selže. Testovací metoda je přesunuta do **neúspěšných testů**. . Vyberte metodu v Průzkumníku testů pro zobrazení podrobností v dolní části okna.

## <a name="fix-your-code-and-rerun-your-tests"></a><a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Opravte kód a znovu spusťte testy.
 **Analyzovat výsledky testu**

 Výsledek testu obsahuje zprávu s popisem chyby. V případě `AreEquals` metody zpráva zobrazuje, co se očekávalo ((<strong>očekávaný \<*XXX*> </strong>parametr) a co byl skutečně přijatý ( **skutečný \<*YYY*> ** parametr). Očekávali jsme, že zůstatek se má odmítnout od počátečního zůstatku, ale místo toho se zvýšil o částku případného stažení.

 Přezkoušení debetního kódu ukazuje, že testování částí bylo úspěšné při hledání chyby. Množství odčerpání se přidá k zůstatku účtu, pokud by se mělo odečíst.

 **Opravte chybu.**

 Chcete-li chybu opravit, jednoduše nahraďte řádek

```csharp
m_balance += amount;
```

 with

```csharp
m_balance -= amount;
```

 **Znovu spustit test**

 V Průzkumníku testů vyberte **Spustit vše** a spusťte test znovu. Červený/zelený pruh se změní na zelený a test se přesune do skupiny **předaných testů** .

## <a name="use-unit-tests-to-improve-your-code"></a><a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Použití jednotkových testů ke zlepšení kódu
 Tato část popisuje, jak iterativní proces analýzy, vývoje testování částí a refaktoring vám může usnadnit zvýšení a účinnost produkčního kódu.

 **Analýza problémů**

 Po vytvoření testovací metody pro potvrzení, že je platná hodnota v metodě správně odečtena `Debit` , můžeme v naší původní analýze zapnout zbývající případy:

1. Metoda vyvolá výjimku, `ArgumentOutOfRangeException` Pokud je částka MD větší než zůstatek.

2. Vyvolá se také v `ArgumentOutOfRangeException` případě, že je částka MD menší než nula.

   **Vytvoření testovacích metod**

   První pokus o vytvoření testovací metody, která řeší tyto problémy, se jeví jako slíbených:

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

 Atribut používáme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> k vyhodnocení, že byla vyvolána správná výjimka. Atribut způsobí selhání testu, pokud `ArgumentOutOfRangeException` není vyvolána výjimka. Spuštění testu s kladnými i zápornými `debitAmount` hodnotami a následná dočasná úprava testované metody, aby vyvolala obecnou <xref:System.ApplicationException> hodnotu, pokud je hodnota menší než nula ukazuje, že se test chová správně. Chcete-li otestovat případ, kdy je stažená částka větší než zůstatek, je nutné provést následující akce:

1. Vytvořte novou testovací metodu s názvem `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` .

2. Zkopírujte tělo metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nové metody.

3. Nastavte na `debitAmount` číslo větší než zůstatek.

   **Spuštění testů**

   Spuštění dvou metod s různými hodnotami pro `debitAmount` ukazuje, že testy odpovídajícím způsobem zpracovávají všechny zbývající případy. Spuštěním všech tří testů ověříte, že jsou všechny případy v naší původní analýze správně pokryté.

   **Pokračovat v analýze**

   Nicméně poslední dvě testovací metody jsou také trochu problematické. Nemůžeme určit, která podmínka v testovaném kódu se vyvolá při každém testovacím běhu. Některá z možností odlišení těchto dvou podmínek by byla užitečná. Vzhledem k tomu, že se problém týká, je zřejmé, že víte, která podmínka byla porušena, by zvýšila naši důvěru v testech. Tyto informace by také mohly být užitečné pro produkční mechanismus, který zpracovává výjimku, pokud je vyvolána zkoušenou metodou. Generování dalších informací, když by metoda vyvolala všechny obavy, ale `ExpectedException` atribut nemůže tyto informace dodat.

   Při opakovaném pokusu o použití metody test vidíte, že oba podmíněné příkazy používají `ArgumentOutOfRangeException` konstruktor, který jako parametr přebírá název argumentu:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 Při hledání knihovny MSDN zjistíme, že existuje konstruktor, který oznamuje mnohem rozsáhlejší informace. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` obsahuje název argumentu, hodnotu argumentu a uživatelem definovanou zprávu. Tuto metodu můžeme použít k refaktorování testované metody. Ještě lepší využitím veřejně dostupných členů typu můžete určit chyby.

 **Refaktoring testovaného kódu**

 Nejdřív definujeme dvě konstanty pro chybové zprávy v rozsahu třídy:

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 Pak upravíte dvě podmíněné příkazy v `Debit` metodě:

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

 **Refaktorujte testovací metody**

 V naší testovací metodě nejprve odebereme `ExpectedException` atribut. Na svém místě zachytíme vyvolanou výjimku a ověříme, že byla vyvolána v příkazu správné podmínky. Teď se ale musíte rozhodnout mezi dvěma možnostmi, jak ověřit zbývající podmínky. Například v `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` metodě můžeme provést jednu z následujících akcí:

- Vytvrzení, že `ActualValue` vlastnost výjimky (druhý parametr `ArgumentOutOfRangeException` konstruktoru) je větší než počáteční zůstatek. Tato možnost vyžaduje, abyste otestovali `ActualValue` vlastnost výjimky proti `beginningBalance` proměnné testovací metody a také vyžaduje, abyste ověřili, že `ActualValue` hodnota je větší než nula.

- Vyhodnotí, že zpráva (třetí parametr konstruktoru) obsahuje `DebitAmountExceedsBalanceMessage` definici definovanou ve `BankAccount` třídě.

  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>Metoda v rozhraní testování částí společnosti Microsoft nám umožňuje ověřit druhou možnost bez výpočtů, které jsou požadovány pro první možnost.

  Druhý pokus při revizi `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` může vypadat takto:

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

 **Znovu otestovat, přepsat a znovu analyzovat**

 Při Retestování testovacích metod s různými hodnotami se setkáme s následujícími skutečnostmi:

1. Pokud zachytíme správnou chybu pomocí kontrolního výrazu, kde `debitAmount` je větší než zůstatek, kontrolní výraz `Contains` projde, výjimka je ignorována a tak metoda testu projde. To je chování, které chceme.

2. Používá-li se hodnota `debitAmount` , která je menší než 0, kontrolní výraz se nezdaří, protože je vrácena nesprávná chybová zpráva. Vyhodnocení také selhává, pokud zavádíme dočasnou `ArgumentOutOfRange` výjimku v jiném bodě v metodě v cestě testovacího kódu. Tato moc je dobrá.

3. Pokud `debitAmount` je hodnota platná (tj. menší než zůstatek, ale větší než nula, není zachycena žádná výjimka, takže kontrolní výraz se nikdy nezachycuje. Testovací Metoda projde. To není dobré, protože chceme, aby testovací metoda nebyla úspěšná, pokud není vyvolána žádná výjimka.

   Třetí fakt je chyba v naší testovací metodě. Chcete-li se pokusit problém vyřešit, přidejte na <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> konci testovací metody vyhodnocení pro zpracování případu, kde není vyvolána žádná výjimka.

   Ale při přezkoušení se zobrazí, že test nyní selhává, pokud je zachycena správná výjimka. Příkaz catch obnoví výjimku a metoda pokračuje v provádění a při novém vyhodnocení selže. Pro vyřešení nového problému přidáme `return` příkaz za `StringAssert` . Po Retestování se potvrdí, že jsme vyřešili naše problémy. Konečná verze nástroje `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` vypadá takto:

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

 V této poslední části práce, kterou jsme zvýšili, vedli vylepšení testovacího kódu na robustnější a informativní testovací metody. Ale důležitější je, že dodatečná analýza také vedla k lepšímu kódu v testovaném projektu.
