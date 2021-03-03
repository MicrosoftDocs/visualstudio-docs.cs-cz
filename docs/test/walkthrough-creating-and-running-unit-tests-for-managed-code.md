---
title: Kurz pro testování částí v jazyce C#
description: Naučte se vytvářet, spouštět a přizpůsobovat řadu testů jednotek pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód a Průzkumníka testů sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: a6ab205b7f651f8bb5954bee4998602c79fd78e7
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683921"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Návod: Vytváření a spouštění testů jednotek pro spravovaný kód

Tento článek vás provede vytvořením, spuštěním a přizpůsobením řady testů jednotek pomocí rozhraní Microsoft Unit Test Framework pro spravovaný kód a **Průzkumníka testů** sady Visual Studio. Začínáte s projektem C#, který je ve vývoji, vytváříte testy, které vykonávají svůj kód, spouštíte testy a prohlížíte výsledky. Pak změníte kód projektu a znovu spustíte testy.



## <a name="create-a-project-to-test"></a>Vytvořit projekt k otestování

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

2. V nabídce **Soubor** vyberte **Nový** > **Projekt**.

   Zobrazí se dialogové okno **Nový projekt**.

3. V kategorii **Visual C#** > **.NET Core** vyberte šablonu projektu **Konzolová aplikace (.NET Core)** .

4. Pojmenujte projektový **bank** a pak klikněte na **OK**.

   Projekt banky se vytvoří a zobrazí v **Průzkumník řešení** se souborem *program.cs* otevřeným v editoru kódu.

   > [!NOTE]
   > Pokud v editoru *program.cs* není, otevřete ho tak, že dvakrát kliknete na soubor *program.cs* v **Průzkumník řešení** .

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Vyhledejte a vyberte šablonu projektu **Konzolová aplikace** v jazyce C# pro .NET Core a potom klikněte na tlačítko **Další**.

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .

4. Pojmenujte projektový **bank** a pak klikněte na **Další**.

   Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.

   Projekt banky se vytvoří a zobrazí v **Průzkumník řešení** se souborem *program.cs* otevřeným v editoru kódu.

   > [!NOTE]
   > Pokud v editoru *program.cs* není, otevřete ho tak, že dvakrát kliknete na soubor *program.cs* v **Průzkumník řešení** .

::: moniker-end

5. Nahraďte obsah *program.cs* následujícím kódem jazyka C#, který definuje třídu, *BankAccount*:

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

6. Přejmenujte soubor na *BankAccount.cs* tak, že kliknete pravým tlačítkem a zvolíte **Přejmenovat** v **Průzkumník řešení**.

7. V nabídce **sestavení** klikněte na **Sestavit řešení** (nebo stiskněte klávesy **CTRL**  +  **SHIFT**  +  **B**).

Nyní máte projekt s metodami, které můžete testovat. V tomto článku se testy zaměřují na `Debit` metodu. `Debit`Metoda je volána, když je peníze odebráno z účtu.

## <a name="create-a-unit-test-project"></a>Vytvoření projektu testů jednotek

1. V nabídce **soubor** vyberte **Přidat**  >  **Nový projekt**.

   > [!TIP]
   > Můžete také kliknout pravým tlačítkem na řešení v **Průzkumník řešení** a zvolit **Přidat**  >  **Nový projekt**.

::: moniker range="vs-2017"

2. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované**, **Visual C#** a pak zvolte možnost **test**.

3. V seznamu šablon vyberte **projekt testů MSTest (.NET Core)**.

4. Do pole **název** zadejte `BankTests` a pak vyberte **OK**.

   Projekt **BankTests** se přidá do řešení **bank** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Do vyhledávacího pole zadejte **test jednotek** , jako jazyk vyberte **c#** a potom vyberte **Projekt test jednotek** c# pro šablonu .NET Core a pak klikněte na **Další**.

   > [!NOTE]
   > Počínaje verzí Visual Studio 2019 verze 16,9 se název šablony projektu MSTest změnil z **projektu testu jednotek MSTest (.NET Core)** na **test jednotek projektu**.

3. Pojmenujte projekt **BankTests** a klikněte na **Další**.

4. Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.

   Projekt **BankTests** se přidá do řešení **bank** .

::: moniker-end

5. V projektu **BankTests** přidejte odkaz na projekt **banky** .

   V **Průzkumník řešení** vyberte **závislosti** v rámci projektu **BankTests** a pak zvolte **Přidat odkaz** z nabídky kliknutím pravým tlačítkem myši.

6. V dialogovém okně **Správce odkazů** rozbalte položku **projekty**, vyberte možnost **řešení** a poté zkontrolujte položku **banka** .

7. Vyberte **OK**.

## <a name="create-the-test-class"></a>Vytvořit testovací třídu

Vytvořte testovací třídu pro ověření `BankAccount` třídy. Můžete použít soubor *UnitTest1.cs* , který byl vygenerován šablonou projektu, ale přidělte souboru a třídě výstižnější názvy.

### <a name="rename-a-file-and-class"></a>Přejmenovat soubor a třídu

1. Chcete-li přejmenovat soubor, v **Průzkumník řešení** vyberte soubor *UnitTest1.cs* v projektu BankTests. V nabídce klikněte pravým tlačítkem myši na položku **Přejmenovat** (nebo stiskněte **F2**) a pak soubor přejmenujte na *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Chcete-li přejmenovat třídu, v dialogovém okně, které se zobrazí, vyberte možnost **Ano** a dotaz, zda chcete také přejmenovávat odkazy na prvek kódu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Chcete-li přejmenovat třídu, umístěte kurzor na pozici `UnitTest1` v editoru kódu, klikněte pravým tlačítkem myši a zvolte možnost **Přejmenovat** (nebo stiskněte **F2**). Zadejte **BankAccountTests** a potom stiskněte klávesu **ENTER**.

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

### <a name="add-a-using-statement"></a>Přidat příkaz using

Přidejte [ `using` příkaz](/dotnet/csharp/language-reference/keywords/using-statement) do třídy testu, abyste mohli volat do testovaného projektu bez použití plně kvalifikovaných názvů. V horní části souboru třídy přidejte:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Požadavky na testovací třídu

Minimální požadavky pro testovací třídu jsou:

- `[TestClass]`Atribut je vyžadován na jakékoli třídě, která obsahuje metody testování částí, které chcete spustit v Průzkumníku testů.

- Každá testovací metoda, kterou má Průzkumník testů rozpoznat, musí mít `[TestMethod]` atribut.

Můžete mít jiné třídy v projektu testu jednotek, které nemají `[TestClass]` atribut, a můžete mít jiné metody v testovacích třídách, které nemají `[TestMethod]` atribut. Tyto další třídy a metody můžete volat z testovacích metod.

## <a name="create-the-first-test-method"></a>Vytvoření první testovací metody

V tomto postupu zapíšete metody testování částí, abyste ověřili chování `Debit` metody `BankAccount` třídy.

Je třeba zkontrolovat alespoň tři chování:

- Metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> Pokud je částka MD větší než zůstatek.

- Metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> Pokud je hodnota MD menší než nula.

- Pokud je částka MD platná, metoda odečte MD částku od zůstatku účtu.

> [!TIP]
> Výchozí metodu můžete odstranit `TestMethod1` , protože ji v tomto průvodci nebudete používat.

### <a name="to-create-a-test-method"></a>Vytvoření testovací metody

První test ověří, že platná částka (tj. jedna, která je nižší než zůstatek účtu a větší než nula) stáhne správné množství účtu. Do této třídy přidejte následující metodu `BankAccountTests` :

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

Metoda je jednoduchá: nastaví nový `BankAccount` objekt se počátečním zůstatkem a pak odvolá platnou částku. Používá <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> metodu k ověření, že koncový zůstatek je očekávaný.

### <a name="test-method-requirements"></a>Požadavky na testovací metodu

Testovací metoda musí splňovat následující požadavky:

- Je upravena `[TestMethod]` atributem.

- Vrátí `void` .

- Nemůže mít parametry.

## <a name="build-and-run-the-test"></a>Sestavit a spustit test

1. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení** (nebo stiskněte klávesy **CTRL**  +  **SHIFT**  +  **B**).

2. Pokud není **Průzkumník testů** otevřený, otevřete ho výběrem příkazu **test**  >    >  **Průzkumník testů** z horního řádku nabídky (nebo stiskněte klávesu **CTRL +**  +  , **T**).

3. Kliknutím na možnost **Spustit vše** spusťte test (nebo stiskněte klávesovou **zkratku CTRL**  +  **R**, **V**).

   Při běhu testu je stavový řádek v horní části okna **Průzkumník testů** animovaný. Na konci testovacího běhu se pruh změní na zelený, pokud jsou všechny testovací metody úspěšné, nebo červené, pokud některý z testů selže.

   V tomto případě se test nezdařil.

4. Vyberte metodu v **Průzkumníku testů** pro zobrazení podrobností v dolní části okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Opravte kód a znovu spusťte testy.

Výsledek testu obsahuje zprávu s popisem chyby. V případě `AreEqual` metody zpráva zobrazuje, co bylo očekáváno a co bylo skutečně přijato. Očekávali jste rovnováhu, který se má snížit, ale místo toho se zvýšilo o velikost odnětí.

Test jednotky zjistil chybu: množství odčerpání je *přidáno* k zůstatku účtu, pokud by mělo být *odečteno*.

### <a name="correct-the-bug"></a>Opravte chybu.

Chcete-li chybu opravit, v souboru *BankAccount.cs* nahraďte řádek:

```csharp
m_balance += amount;
```

textem:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Znovu spustit test

V **Průzkumníku testů** kliknutím na možnost **Spustit vše** spusťte test znovu (nebo stiskněte klávesu **CTRL**  +  **R**, **V**). Červený/zelený pruh se změní na zelenou, aby označoval, že test proběhl úspěšně.

![Průzkumník testů v aplikaci Visual Studio 2019 zobrazující úspěšný test](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Použití jednotkových testů ke zlepšení kódu

Tato část popisuje, jak iterativní proces analýzy, vývoje testování částí a refaktoring vám může usnadnit zvýšení a účinnost produkčního kódu.

### <a name="analyze-the-issues"></a>Analýza problémů

Vytvořili jste testovací metodu pro potvrzení, že je platná hodnota správně odečtena v `Debit` metodě. Nyní ověřte, zda metoda vyvolá výjimku, <xref:System.ArgumentOutOfRangeException> Pokud je částka MD buď:

- větší než zůstatek, nebo
- menší než nula.

### <a name="create-and-run-new-test-methods"></a>Vytvoření a spuštění nových testovacích metod

Vytvořte testovací metodu pro ověření správného chování v případě, že je částka MD menší než nula:

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

Použijte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metodu k vyhodnocení, že byla vyvolána správná výjimka. Tato metoda způsobí selhání testu, pokud <xref:System.ArgumentOutOfRangeException> není vyvolána výjimka. Pokud dočasně upravíte metodu v rámci testu, aby vyvolal obecnější v případě, že <xref:System.ApplicationException> je částka MD menší než nula, test se chová správně, &mdash; což znamená, že se nezdařil.

Chcete-li otestovat případ, kdy je stažená částka větší než zůstatek, proveďte následující kroky:

1. Vytvořte novou testovací metodu s názvem `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` .

2. Zkopírujte tělo metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nové metody.

3. Nastavte na `debitAmount` číslo větší než zůstatek.

Spuštění dvou testů a ověření, zda jsou splněna.

### <a name="continue-the-analysis"></a>Pokračovat v analýze

Testovaná metoda se dá ještě zlepšit. S aktuální implementací neexistuje způsob, jak zjistit, která podmínka ( `amount > m_balance` nebo `amount < 0` ) vedla k výjimce vyvolané během testu. Právě víme, že `ArgumentOutOfRangeException` v metodě byl vyvolána výjimka. Bylo by lepší, pokud nám poznáte, která podmínka v `BankAccount.Debit` důsledku způsobila vyvolání výjimky (nebo), abychom si mohli `amount > m_balance` `amount < 0` být jistí, že naše metoda je správnostiá a správně kontroluje argumenty.

Podívejte se na metodu, která je testována ( `BankAccount.Debit` ) znovu, a Všimněte si, že oba podmíněné příkazy používají `ArgumentOutOfRangeException` konstruktor, který pouze přebírá název argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

K dispozici je konstruktor, který oznamuje mnohem rozsáhlejší informace: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> obsahuje název argumentu, hodnotu argumentu a uživatelem definovanou zprávu. Chcete-li použít tento konstruktor, lze metodu Refaktorovat v testovaném testu. Ještě lepší využitím veřejně dostupných členů typu můžete určit chyby.

### <a name="refactor-the-code-under-test"></a>Refaktoring testovaného kódu

Nejprve definujte dvě konstanty pro chybové zprávy v oboru třídy. Umístěte je do testované třídy, `BankAccount` :

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Pak upravte dva podmíněné příkazy v `Debit` metodě:

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

### <a name="refactor-the-test-methods"></a>Refaktorujte testovací metody

Refaktorujte testovací metody odebráním volání <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> . Zabalte volání do `Debit()` `try/catch` bloku, Zachyťte očekávanou konkrétní výjimku a ověřte její přidruženou zprávu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>Metoda poskytuje možnost porovnat dva řetězce.

Nyní `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` může vypadat takto:

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

### <a name="retest-rewrite-and-reanalyze"></a>Znovu otestovat, přepsat a znovu analyzovat

V současné době testovací metoda nezpracovává všechny případy, kdy by měla. Pokud metoda, která je testována, `Debit` nezdařila vyvolání metody, <xref:System.ArgumentOutOfRangeException> Když `debitAmount` byla větší než zůstatek (nebo menší než nula), metoda testu projde. To není dobré, protože chcete, aby testovací metoda nebyla úspěšná, pokud není vyvolána žádná výjimka.

Jedná se o chybu v testovací metodě. Chcete-li vyřešit tento problém, přidejte na <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> konec testovací metody kontrolní výraz pro zpracování případu, kde není vyvolána žádná výjimka.

Po spuštění testu se zobrazí, že test nyní *selhává* , pokud je zachycena správná výjimka. `catch`Blok zachytí výjimku, ale metoda pokračuje v provádění a v novém kontrolním výrazu se nezdařila <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> . Chcete-li tento problém vyřešit, přidejte `return` příkaz za `StringAssert` `catch` blok. Po spuštění testu se potvrdí, že jste vyřešili tento problém. Finální verze `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` vypadá takto:

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

Vylepšení testovacího kódu vedla k robustnějším a informativním testovacím metodám. Ale důležitější je, že také vylepšili testovaný kód.

> [!TIP]
> Tento návod používá pro spravovaný kód rozhraní testování částí společnosti Microsoft. **Průzkumník testů** může také spouštět testy z rozhraní pro testování částí třetích stran, které mají adaptéry pro **Průzkumník testů**. Další informace najdete v tématu [instalace rozhraní pro testování částí třetích stran](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Viz také

Informace o tom, jak spustit testy z příkazového řádku, najdete v tématu [VSTest.Console.exe možností příkazového řádku](vstest-console-options.md).
