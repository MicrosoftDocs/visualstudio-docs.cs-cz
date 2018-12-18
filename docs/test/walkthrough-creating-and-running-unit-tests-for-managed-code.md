---
title: Vytváření a spouštění testů jednotek pro spravovaný kód
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 13488619b38f5fd974d793d56f6a8d8cf86f15c1
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469110"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Návod: Vytváření a spouštění testů jednotek pro spravovaný kód

Tento článek vás provede vytvořením, spuštěný, a přizpůsobením série jednotky testů pomocí rozhraní pro testování jednotek Microsoft pro spravovaný kód a Visual Studio **Průzkumníka testů**. Spustit u projektu C#, která je ve vývoji, vytvoříte testy, které testují jeho kód, spusťte testy a podívejte se na výsledky. Můžete změnit kód projektu a znovu spusťte testy.

> [!NOTE]
> Tento návod používá rozhraní testování částí Microsoft pro spravovaný kód. **Průzkumník testů** může také spouštět testy z jednotky třetí strany, které mají adaptéry pro rozhraní pro testování **Průzkumníka testů**. Další informace najdete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](../test/install-third-party-unit-test-frameworks.md)

Informace o tom, ke spuštění testů z příkazového řádku najdete v tématu [možnosti příkazového řádku VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Požadavky

- Projekt banky. Zobrazit [ukázkový projekt testování částí](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Vytvoření projektu pro testování

1. Otevřít Visual Studio.

2. Na **souboru** nabídce vyberte možnost **nový** > **projektu**.

   **Nový projekt** zobrazí se dialogové okno.

3. V části **nainstalované šablony**, klikněte na tlačítko **Visual C#**.

4. V seznamu typů aplikací, klikněte na tlačítko **knihovny tříd**.

5. V **název** zadejte **Bank** a potom klikněte na tlačítko **OK**.

   Nový projekt banka se vytvoří a zobrazí v **Průzkumníka řešení** s *Class1.cs* soubor je otevřen v editoru kódu.

   > [!NOTE]
   > Pokud *Class1.cs* nelze otevřít v editoru kódu, dvakrát klikněte na soubor *Class1.cs* v **Průzkumníka řešení** ho otevřete.

6. Zkopírujte zdrojový kód z [ukázkový projekt testování částí](../test/sample-project-for-creating-unit-tests.md)a nahraďte původní obsah *Class1.cs* zkopírovaný kód.

7. Uložte soubor jako *BankAccount.cs*.

8. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

Nyní máte projekt s názvem banka. Obsahuje zdrojový kód pro testování a nástroje a otestovat ho s. Obor názvů pro banku, BankAccountNS, obsahuje veřejnou třídu BankAccount, jejíž metody budete testovat v následujících postupech.

V tomto článku se testy zaměřit na metodu MD. MD metoda je volána, když jsou peníze z účtu. Tady je způsob definice:

```csharp
// Method to be tested.
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

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testů jednotek

1. Na **souboru** nabídce vyberte možnost **přidat** > **nový projekt**.

2. V **nový projekt** dialogového okna rozbalte **nainstalováno**, rozbalte **Visual C#** a klikněte na tlačítko **Test**.

3. V seznamu šablon vyberte **projekt testu jednotek**.

4. V **název** zadejte `BankTests`a pak vyberte **OK**.

   **BankTests** projekt je přidán do **Bank** řešení.

5. V **BankTests** projektu, přidejte odkaz na **Bank** projektu.

   V **Průzkumníka řešení**vyberte **odkazy** v **BankTests** projektu a klikněte na tlačítko **přidat odkaz** v místní nabídce.

6. V **správce odkazů** dialogového okna rozbalte **řešení** a potom zaškrtněte políčko **Bank** položky.

## <a name="create-the-test-class"></a>Vytvoření testovací třídy

Vytvořte třídu testu k ověření `BankAccount` třídy. Můžete použít *UnitTest1.cs* soubor, který se vygeneroval pomocí šablony projektu, ale dát souboru a třídě více popisné názvy. Můžete to udělat v jednom kroku přejmenováním souboru v **Průzkumníka řešení**.

### <a name="rename-a-class-file"></a>Přejmenování souboru třídy

V **Průzkumníka řešení**, vyberte *UnitTest1.cs* soubor v projektu BankTests. V místní nabídce zvolte **přejmenovat**a potom přejmenujte soubor, který má *BankAccountTests.cs*. Zvolte **Ano** v dialogovém okně s dotazem, jestli chcete přejmenovat všechny odkazy na prvek kódu `UnitTest1` v projektu.

Tento krok změní název třídy, která se `BankAccountTests`. *BankAccountTests.cs* soubor nyní obsahuje následující kód:

```csharp
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

### <a name="add-a-using-statement-to-the-project-under-test"></a>Přidat sadu pomocí příkazu testovaného projektu

Můžete také přidat `using` prohlášení do třídy bude možné volat Testovaný projekt bez použití plně kvalifikovaných názvů. V horní části souboru třídy přidejte:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Požadavky na testovací třídu

Minimální požadavky na testovací třídu jsou:

- `[TestClass]` Atribut je požadován v testování části Microsoft framework pro spravovaný kód pro libovolnou třídu obsahující metody jednotkového testu, které chcete spustit v aplikaci Test Explorer.

- Každá testovací metoda, která má být spuštěna Průzkumníkem testů musí mít `[TestMethod]` atribut.

Můžete mít další třídy v projektu testů jednotek, které nemají `[TestClass]` atribut který může mít jiné metody v testovacích třídách, které nemají `[TestMethod]` atribut. Ve vašich testovacích metodách můžete použít tyto třídy a metody.

## <a name="create-the-first-test-method"></a>Vytvoření první testovací metody

V tomto postupu budete psát testování částí, metody, které ověří chování `Debit` metodu `BankAccount` třídy. `Debit` Metoda je uvedené dříve v tomto článku.

Existují nejméně tři typy chování, které je potřeba zkontrolovat:

- Metoda vyvolá <xref:System.ArgumentOutOfRangeException> Pokud debetní velikost je větší než zůstatek na účtu.

- Metoda vyvolá <xref:System.ArgumentOutOfRangeException> Pokud debetní velikost je menší než nula.

- Pokud je hodnota debetní platný, metoda odečte MD částku od zůstatku účtu.

> [!TIP]
> Můžete odstranit výchozí `TestMethod1` metody, protože nebudeme je používat v tomto názorném postupu.

### <a name="to-create-a-test-method"></a>Vytvoření testovací metody

První test ověří, že platná částka (to znamená, že tu je menší než zůstatek na účtu a větší než nula) stáhne z účtu objektu správnou velikost. Přidejte následující metodu do `BankAccountTests` třídy:

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Tato metoda je jednoduchý: nastaví nový `BankAccount` objekt s počáteční zůstatek a potom stáhne platnou částku. Používá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metodu k ověření, že je konečný zůstatek podle očekávání.

### <a name="test-method-requirements"></a>Požadavky na testovací metodu

Testovací metoda musí splňovat následující požadavky:

- Je doplněn `[TestMethod]` atribut.

- Vrátí `void`.

- Nemůže mít parametry.

## <a name="build-and-run-the-test"></a>Sestavení a spuštění testu

1. Na **sestavení** nabídce zvolte **sestavit řešení**.

   Pokud zde nejsou žádné chyby **Průzkumník testů** se zobrazí s **Debit_WithValidAmount_UpdatesBalance** uvedené v **nespuštěné testy** skupiny.

   > [!TIP]
   > Pokud **Průzkumník testů** po úspěšném sestavení nezobrazí, zvolte **testovací** v nabídce klikněte na tlačítko **Windows**a klikněte na tlačítko **Průzkumník testů**.

2. Zvolte **spustit všechny** pro spuštění testu. Když je spuštěn test, je stavového řádku v horní části okna animovaný. Na konci testovacího běhu stavový řádek zezelená, pokud všechny testovací metody proběhly úspěšně nebo red Pokud selže některý z testů.

3. V tomto případě test se nezdaří. Testovací metoda je přesunuta do **neúspěšné testy** skupiny. Vyberte metodu v **Průzkumník testů** k zobrazení podrobností v dolní části okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Oprava kódu a znovu spustit testy

### <a name="analyze-the-test-results"></a>Analýza výsledků testování

Výsledek testu obsahuje zprávu s popisem chyby. Pro `AreEqual` metoda, zpráva se zobrazí, co byl očekáván ( **očekávaná\<*hodnotu* >**  parametr) a co vlastně přijatých ( **Skutečné\<*hodnotu* >** parametr). Očekáván snížení zůstatku, ale místo toho zvětšit velikost o stažení.

Testování částí vyplynul chybu: stažení je *přidali* k zůstatku, ale měla by být *odečtena*.

### <a name="correct-the-bug"></a>Oprava chyby

Chcete-li chybu opravit, nahraďte řádek:

```csharp
m_balance += amount;
```

Pomocí:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Opětovné provedení testu

V **Průzkumníka testů**, zvolte **spustit všechny** na opětovné spuštění testu. Barva červeného/zeleného panel zbarví zeleně k označení, že test proběhl úspěšně a test je přesunut do **úspěšné testy** skupiny.

## <a name="use-unit-tests-to-improve-your-code"></a>Použití jednotkových testů ke zlepšení kódu

Tato část popisuje, jak může iterativní proces analýzy, vývoj jednotkových testů a refaktoring pomoci vám robustnějšího a efektivnějšího produkčního kódu.

### <a name="analyze-the-issues"></a>Analýza problémů

Vytvoření testovací metody pro potvrzení, správně odečtení platné částky v `Debit` metody. Nyní, ověřte, že metoda vyvolá <xref:System.ArgumentOutOfRangeException> Pokud je tato hodnota debetní buď:

- větší než zůstatek, nebo
- menší než nula.

### <a name="create-the-test-methods"></a>Vytvoření testovacích metod

Vytvořte testovací metodu k ověření správné chování při debetní velikost je menší než nula:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Použití <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atribut k vyhodnocení, že byla vyvolána správná výjimka. Atribut způsobí, že se test nezdaří, pokud <xref:System.ArgumentOutOfRangeException> je vyvolána výjimka. Pokud upravíte dočasně testované vyvolat další obecné metody <xref:System.ApplicationException> při MD částka menší než nula, správné chování testu&mdash;tedy selže.

K otestování případu, kdy vybíraná hodnota je větší než zůstatek, proveďte následující kroky:

1. Vytvořit novou testovací metodu s názvem `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Zkopírovat tělo metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nové metody.

3. Nastavte `debitAmount` na číslo větší než zůstatek na účtu.

### <a name="run-the-tests"></a>Spustit testy

Spuštění těchto dvou metod testu ukazuje, že testy správně fungovat.

### <a name="continue-the-analysis"></a>Pokračování analýzy

Dvě poslední metody testování jsou však také problematické. Můžete nemůže být určité která podmínka testované metody vyvolá výjimku, když je buď testovací běh. Nějaký způsob odlišení těchto dvou podmínek, který je částka negativní debetní nebo hodnota větší než zůstatek, zvýší vaši důvěru v tyto testy.

Podívejte se na testované metody znovu a Všimněte si, že oba podmíněné příkazy používají `ArgumentOutOfRangeException` konstruktor, který právě přebírá název argumentu, který jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Je můžete použít konstruktor, který mnohem bohatší informace: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> obsahuje název argumentu, hodnotu argumentu a uživatelsky definovanou zprávu. Možné provést refaktoring testované používala tento konstruktor metody. Navíc můžete použít veřejně dostupné členy typů ke specifikaci chyb.

### <a name="refactor-the-code-under-test"></a>Refaktoring testovaného kódu

Nejprve definujte dvě konstanty pro chybové zprávy v oboru třídy. Vložte ve třídě v rámci testu, BankAccount:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Změňte dva podmíněné příkazy v `Debit` metody:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Refaktoring testovacích metod

Odeberte `ExpectedException` testu atribut method a místo toho zachyťte vyvolanou výjimku a ověřte její přidružené zprávy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda poskytuje možnost k porovnání dvou řetězců.

Nyní `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` může vypadat třeba takto:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Opětovné testování, revize a analýza

Předpokládejme je chyba v metodě v rámci testu a `Debit` i metoda nevyvolá <xref:System.ArgumentOutOfRangeException>, nevermind výstup správné zprávy s výjimkou. Testovací metoda není v současné době zpracovávat tento případ. Pokud `debitAmount` je hodnota platná (to znamená menší než zůstatek, ale větší než nula), žádná výjimka je zachycena, takže assert nikdy aktivuje. Zatím testovací metoda skončí úspěchem. To není správné, protože chcete, aby testovací metoda selhat, pokud není vyvolána žádná výjimka.

Jedná se o chybu v testovací metodě. Chcete-li problém vyřešit, přidejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> uplatnit na konci testovací metody pro zpracování případu, kdy není vyvolána žádná výjimka.

Znovu spustit test se zobrazuje, který test nyní *selže* Pokud zachycení správné výjimky. `catch` Bloku zachytí výjimku, ale metoda pokračuje v provádění a ona selže na novou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> kontrolní výraz. Chcete-li tento problém vyřešit, přidejte `return` příkazem za `StringAssert` v `catch` bloku. Znovu spustit test potvrdí, že je tento problém vyřešili. Konečná verze `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` vypadá přibližně takto:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Vylepšení testovacího kódu vedla k robustnějším a informativnějším testovací metody. Ale důležitější je, taky vylepšené testovaného kódu.
