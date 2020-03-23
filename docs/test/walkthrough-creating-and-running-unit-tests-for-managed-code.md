---
title: Kurz testování částí jednotky jazyka C#
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 4d5878e2c5950e45f65f8d56efdf53cd7b2e89ea
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094678"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Návod: Vytváření a spouštění testů jednotek pro spravovaný kód

Tento článek vás provede vytvořením, spuštěním a přizpůsobením řady testů částí pomocí architektury testování částí společnosti Microsoft pro spravovaný kód a **Průzkumník a průzkumníka testů**sady Visual Studio . Můžete začít s c# projektu, který je ve vývoji, vytvořit testy, které vykonávají jeho kód, spusťte testy a zkontrolujte výsledky. Potom změníte kód projektu a znovu spusťte testy.



## <a name="create-a-project-to-test"></a>Vytvoření projektu k testování

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

2. V nabídce **Soubor** vyberte **Nový** > **Projekt**.

   Zobrazí se dialogové okno **Nový projekt**.

3. V kategorii **Visual C#** > **.NET Core** zvolte šablonu projektu **Konzola Aplikace (.NET Core).**

4. Pojmenujte projekt **Bank**a klepněte na tlačítko **OK**.

   Projekt Banky je vytvořen a zobrazen v **Průzkumníku řešení** s *Program.cs* soubor emitovaný v editoru kódu.

   > [!NOTE]
   > Pokud *Program.cs* v editoru není otevřené, poklepejte na soubor *Program.cs* v **Průzkumníku řešení** a otevřete jej.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Vyhledejte a vyberte šablonu projektu konzoly C# **Console App (.NET Core)** a klepněte na tlačítko **Další**.

4. Pojmenujte projekt **Bank**a klepněte na tlačítko **Vytvořit**.

   Projekt Banky je vytvořen a zobrazen v **Průzkumníku řešení** s *Program.cs* soubor emitovaný v editoru kódu.

   > [!NOTE]
   > Pokud *Program.cs* v editoru není otevřené, poklepejte na soubor *Program.cs* v **Průzkumníku řešení** a otevřete jej.

::: moniker-end

5. Nahraďte obsah *Program.cs* následujícím kódem jazyka C#, který definuje třídu *BankAccount*:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Přejmenujte soubor na *BankAccount.cs* klepnutím pravým tlačítkem myši a výběrem **možnosti Přejmenovat** v **Průzkumníku řešení**.

7. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

Nyní máte projekt s metodami, které můžete testovat. V tomto článku se testy `Debit` zaměřují na metodu. Metoda `Debit` se nazývá, když jsou peníze vybrány z účtu.

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

1. V nabídce **Soubor** vyberte **Přidat** > **nový projekt**.

   > [!TIP]
   > Můžete také kliknout pravým tlačítkem myši na řešení v **Průzkumníku řešení** a zvolit **Přidat** > **nový projekt**.

::: moniker range="vs-2017"

2. V dialogovém okně **Nový projekt** rozbalte **položku Nainstalováno**, rozbalte **položku Visual C#** a pak zvolte **Testovat**.

3. Ze seznamu šablon vyberte **Testovací projekt MSTest (.NET Core)**.

4. Do pole **Název** `BankTests`zadejte a pak vyberte **OK**.

   Projekt **BankTests** je přidán do řešení **Banky.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Vyhledejte a vyberte šablonu projektu **C# MSTest Test Project (.NET Core)** a klepněte na tlačítko **Další**.

3. Název projektu **BankTests**.

4. Klikněte na **Vytvořit**.

   Projekt **BankTests** je přidán do řešení **Banky.**

::: moniker-end

5. V projektu **BankTests** přidejte odkaz na projekt **Banky.**

   V **Průzkumníku řešení**vyberte **závislosti** v projektu **BankTests** a pak z nabídky po kliknutí pravým tlačítkem myši **zvolte Přidat odkaz.**

6. V dialogovém okně **Správce odkazů** rozbalte **položku Projekty**, vyberte **Řešení**a zaškrtněte položku **Banka.**

7. Vyberte **OK**.

## <a name="create-the-test-class"></a>Vytvoření testovací třídy

Vytvořte testovací třídu `BankAccount` k ověření třídy. Můžete použít *soubor UnitTest1.cs,* který byl vygenerován šablonou projektu, ale dát soubora a třídy více popisné názvy.

### <a name="rename-a-file-and-class"></a>Přejmenování souboru a třídy

1. Chcete-li soubor přejmenovat, vyberte v **Průzkumníku řešení** *UnitTest1.cs* soubor v projektu BankTests. V nabídce po kliknutí pravým tlačítkem myši zvolte **Přejmenovat**a potom soubor přejmenujte na *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Chcete-li třídu přejmenovat, zvolte **Ano** v dialogovém okně, které se objeví, a zeptá se, zda chcete také přejmenovat odkazy na prvek kódu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Chcete-li třídu přejmenovat, `UnitTest1` umístěte kurzor do editoru kódu, klikněte pravým tlačítkem myši a pak zvolte **Přejmenovat**. Zadejte **příkaz BankAccountTests** a stiskněte **klávesu Enter**.

::: moniker-end

Soubor *BankAccountTests.cs* nyní obsahuje následující kód:

```csharp
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

### <a name="add-a-using-statement"></a>Přidání příkazu using

Přidejte [ `using` příkaz](/dotnet/csharp/language-reference/keywords/using-statement) do testovací třídy, abyste mohli volat do testovaní projektu bez použití plně kvalifikovaných názvů. V horní části souboru třídy přidejte:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Požadavky na zkušební třídu

Minimální požadavky na zkušební třídu jsou:

- Atribut `[TestClass]` je vyžadován pro všechny třídy, která obsahuje metody testování částí, které chcete spustit v Průzkumníku testů.

- Každá testovací metoda, kterou má Průzkumník `[TestMethod]` testů rozpoznat, musí mít atribut.

Můžete mít jiné třídy v projektu testování `[TestClass]` částí, které nemají atribut a můžete mít jiné `[TestMethod]` metody v testovacítřídy, které nemají atribut. Můžete volat tyto jiné třídy a metody z testovacích metod.

## <a name="create-the-first-test-method"></a>Vytvořit první zkušební metodu

V tomto postupu zapíšete metody testování částí k `Debit` ověření `BankAccount` chování metody třídy.

Existují alespoň tři chování, které je třeba zkontrolovat:

- Metoda vyvolá, <xref:System.ArgumentOutOfRangeException> pokud je částka Má dáti větší než zůstatek.

- Metoda vyvolá, <xref:System.ArgumentOutOfRangeException> pokud je částka Má dáti menší než nula.

- Pokud je částka Má dáti platná, metoda odečte částku Má dáti od zůstatku na účtu.

> [!TIP]
> Výchozí `TestMethod1` metodu můžete odstranit, protože ji v tomto návodu nebudete používat.

### <a name="to-create-a-test-method"></a>Vytvoření zkušební metody

První test ověří, zda platná částka (tj. částka, která je menší než zůstatek na účtu a větší než nula) vybere správnou částku z účtu. Do této `BankAccountTests` třídy přidejte následující metodu:

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

Metoda je jednoduchá: nastaví `BankAccount` nový objekt s počátečním zůstatkem a pak vybere platnou částku. Používá metodu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> k ověření, že konečný zůstatek je podle očekávání.

### <a name="test-method-requirements"></a>Požadavky na zkušební metodu

Zkušební metoda musí splňovat tyto požadavky:

- Je to zdobené `[TestMethod]` atributem.

- Vrátí `void`.

- Nemůže mít parametry.

## <a name="build-and-run-the-test"></a>Sestavení a spuštění testu

1. V nabídce **Build** zvolte **Build Solution**.

2. Pokud **Průzkumník testů** není otevřený, otevřete ho tak, že z horního řádku nabídek zvolíte **Testovat** > **Průzkumníka testů** **systému Windows.** > 

3. Chcete-li spustit test, zvolte **Spustit vše.**

   Při spuštění testu je animován stavový řádek v horní části okna **Průzkumníka testů.** Na konci testovacího běhu se pruh změní na zelenou, pokud všechny zkušební metody projdou, nebo červená, pokud některý z testů selže.

   V tomto případě se test nezdaří.

4. Vyberte metodu v **Průzkumníkovi testů** a zobrazte podrobnosti v dolní části okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Oprava kódu a opětovné spuštění testů

Výsledek testu obsahuje zprávu, která popisuje selhání. Pro `AreEqual` metodu se zobrazí, co bylo očekáváno a co bylo skutečně přijato. Očekávali jste, že se zůstatek sníží, ale místo toho se zvýšil o částku výběru.

Test částí odhalil chybu: částka výběru je *přidána* k zůstatku na účtu, když by měla být *odečtena*.

### <a name="correct-the-bug"></a>Opravit chybu

Chcete-li chybu opravit, nahraďte v *souboru BankAccount.cs* řádek:

```csharp
m_balance += amount;
```

textem:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Znovu spustit test

V **Průzkumníkovi testů**zvolte **Spustit vše,** chcete-li znovu spustit test. Červený/zelený pruh se změní na zelený, což znamená, že test prošel.

![Průzkumník testů ve Visual Studiu 2019 ukazuje prošlý test](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Vylepšování kódu pomocí testů částí

Tato část popisuje, jak iterativní proces analýzy, vývoj testování částí a refaktoring uvázne, aby byl produkční kód robustnější a efektivnější.

### <a name="analyze-the-issues"></a>Analýza problémů

Vytvořili jste testovací metodu, která potvrzuje, že platná `Debit` částka je správně odečtena v metodě. Nyní ověřte, že <xref:System.ArgumentOutOfRangeException> metoda vyvolá, pokud je částka Má dáti buď:

- větší než zůstatek, nebo
- menší než nula.

### <a name="create-and-run-new-test-methods"></a>Vytvořit a spustit nové zkušební metody

Vytvořte testovací metodu k ověření správného chování, pokud je částka Má dáti menší než nula:

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

Pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metody tvrdit, že byla vyvolána správná výjimka. Tato metoda způsobí selhání testu, <xref:System.ArgumentOutOfRangeException> pokud je vyvolána. Pokud dočasně upravit testovku vyvolat <xref:System.ApplicationException> obecnější, pokud je částka Má dáti&mdash;menší než nula, test se chová správně, že je, se nezdaří.

Chcete-li otestovat případ, kdy je stažená částka větší než zůstatek, proveďte následující kroky:

1. Vytvořte novou zkušební `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`metodu s názvem .

2. Zkopírujte tělo `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` metody z do nové metody.

3. Nastavte `debitAmount` číslo větší než zůstatek.

Spuštění dvou testů a ověřte, zda projdou.

### <a name="continue-the-analysis"></a>Pokračovat v analýze

Testovky lze dále zlepšit. Při současné implementaci nemáme žádný způsob, jak`amount > m_balance` `amount < 0`zjistit, která podmínka (nebo ) vedla k vyvolání výjimky během testu. Jen víme, `ArgumentOutOfRangeException` že byl hozen někde v metodě. Bylo by lepší, kdybychom mohli `BankAccount.Debit` říct, který stav`amount > m_balance` v `amount < 0`způsobil výjimku, která má být vyvolána ( nebo ), takže můžeme být jisti, že naše metoda je příčetnost-kontrola jeho argumenty správně.

Podívejte se na metodu`BankAccount.Debit`testován ( ) znovu, `ArgumentOutOfRangeException` a všimněte si, že oba podmíněné příkazy používají konstruktor, který právě bere název argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Existuje konstruktor, který může být určen <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> k tomu, aby senami mnohem bohatší informace: obsahuje název argumentu, hodnotu argumentu a uživatelem definovanou zprávu. Můžete refaktorovat testovku metody pro použití tohoto konstruktoru. Ještě lepší je, můžete použít veřejně dostupné členy typu k určení chyby.

### <a name="refactor-the-code-under-test"></a>Refaktorovat testovaný kód

Nejprve definujte dvě konstanty pro chybové zprávy v oboru třídy. Dejte tyto ve třídě `BankAccount`v testu, :

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Potom upravte dva podmíněné `Debit` příkazy v metodě:

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Refaktorování zkušebních metod

Refaktorovat zkušební metody odebráním <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>volání . Zalomit `Debit()` volání `try/catch` do bloku, zachytit konkrétní výjimku, která je očekává, a ověřte jeho přidružené zprávy. Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> poskytuje možnost porovnat dva řetězce.

`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` Teď, může vypadat takto:

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Přezkoušení, přepis a přeanalýza

Předpokládejme, že je chyba v metodě testované a `Debit` <xref:System.ArgumentOutOfRangeException> metoda ani vyvolat bez ohledu na výstup správnou zprávu s výjimkou. V současné době testovací metoda nezpracovává tento případ. Pokud `debitAmount` je hodnota platná (to znamená menší než zůstatek a větší než nula), není zachycena žádná výjimka, takže assert nikdy nevyvolá. Přesto zkušební metoda projde. To není dobré, protože chcete, aby testovací metoda selhala, pokud není vyvolána žádná výjimka.

Toto je chyba v testovací metodě. Chcete-li problém vyřešit, přidejte assert <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> na konci zkušební metody pro zpracování případu, kde není vyvolána žádná výjimka.

Opětovné spuštění testu ukazuje, že test nyní *selže,* pokud je zachycena správná výjimka. Blok `catch` zachytí výjimku, ale metoda pokračuje v provádění <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> a selže na nové assert. Chcete-li tento problém `return` vyřešit, přidejte příkaz za `StringAssert` v `catch` bloku. Opětovné spuštění testu potvrzuje, že jste tento problém opravili. Konečná verze `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` vypadá takto:

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Závěr

Vylepšení testovacího kódu vedlo k robustnějším a informativnějším zkušebním metodám. Ale co je důležitější, také vylepšili testovaný kód.

> [!TIP]
> Tento návod používá rozhraní Microsoft testování částí pro spravovaný kód. **Průzkumník testů** můžete také spustit testy z rozhraní testování částí jiných výrobců, které mají adaptéry pro **Průzkumníka testů**. Další informace naleznete [v tématu Instalace rozhraní test ů částí jiných výrobců](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Viz také

Informace o spuštění testů z příkazového řádku naleznete v [tématu Možnosti příkazového řádku nástroje VSTest.Console.exe](vstest-console-options.md).
