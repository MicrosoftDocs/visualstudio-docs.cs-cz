---
title: Návod pro vývoj řízený testovacím prostředím
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566277"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Návod: Vývoj řízený testovacím prostředím pomocí Průzkumníka testů

Vytvořte testy jednotek, které vám pomůžou zajistit správné fungování kódu prostřednictvím přírůstkových změn kódu. Existuje několik architektur, které můžete použít pro psaní jednotkových testů, včetně některých vyvinutých třetími stranami. Některé testovací architektury jsou specializované pro testování v různých jazycích nebo platformách. Průzkumník testů poskytuje tak jednotné rozhraní pro testování částí v některém z těchto rozhraní. Další informace o **Průzkumníku testů**naleznete v tématu [spuštění testů jednotek pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md) a [nejčastějších dotazů Průzkumníka testů](test-explorer-faq.md).

Tento návod ukazuje, jak vyvíjet testovaný způsob v C# použití Microsoft Test Frameworku (MSTest). Můžete ji snadno přizpůsobit pro jiné jazyky nebo jiné testovací architektury, jako je například NUnit. Další informace najdete v tématu [nainstalovat rozhraní pro testování jednotky třetí strany](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Vytvoří test a vygeneruje kód.

1. C# Vytvořte projekt **knihovny tříd (.NET Standard)** . Tento projekt bude obsahovat kód, který chceme testovat. Pojmenujte projekt **MyMath**.

2. Ve stejném řešení přidejte nový projekt **testů MSTest (.NET Core)** . Pojmenujte projekt testů **MathTests**.

   ![Nové projekty kódu a testování](../test/media/test-driven-development-ide.png)

3. Napište jednoduchou testovací metodu, která ověří výsledek získaný pro konkrétní vstup. Do `UnitTest1` třídy přidejte následující kód:

   ```csharp
   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Vygeneruje typ z testovacího kódu.

   1. Umístěte kurzor na `Rooter`a potom v nabídce žárovky zvolte **generovat typ rooter** > **generovat nový typ**.

      ![Vytvořit novou rychlou akci typu](media/test-driven-development-generate-new-type.png)

   2. V dialogovém okně **generovat typ** nastavte možnost **projekt** na **MyMath**, projekt knihovny tříd a klikněte na **tlačítko OK**.

      ![Dialogové okno generovat typ v aplikaci Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Vygenerujte metodu z testovacího kódu. Umístěte kurzor na `SquareRoot`a potom v nabídce žárovky zvolte **generovat metodu root. SquareRoot**.

6. Spusťte Jednotkový test.

   1. Chcete-li otevřít **Průzkumníka testů**, v nabídce **test** vyberte možnost **Windows** > **Průzkumník testů**.

   2. V **Průzkumníku testů**klikněte na tlačítko **Spustit vše** a spusťte test.

   Řešení se sestaví a testovací běhy a selžou.

7. Vyberte název testu.

   Podrobnosti testu se zobrazí v podokně **Souhrn podrobností testu** .

   ![Souhrn podrobností testu v Průzkumníku testů](media/test-driven-development-test-detail-summary.png)

8. Vyberte horní odkaz v části **trasování zásobníku** a přejděte do umístění, kde se test nezdařil.

V tomto okamžiku jste vytvořili test a zástupnou proceduru, kterou lze upravit tak, aby test prošl.

## <a name="verify-a-code-change"></a>Ověření změny kódu

1. V souboru *Class1.cs* Vylepšete kód `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. V **Průzkumník testů**, zvolte **spustit všechny**.

   Řešení sestaví a spustí test a projde.

   ![Průzkumník testů ukazující procházející test](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Rozšiřování rozsahu vstupů

Chcete-li zlepšit naši jistotu, že kód funguje ve všech případech, přidejte testy, které vyzkouší širší rozsah vstupních hodnot.

> [!TIP]
> Neupravujte existující testy, které předávají. Místo toho přidejte nové testy. Existující testy měňte pouze v případě, že se změní požadavky uživatele. Tato zásada umožňuje zajistit, aby neztratili stávajících funkcí během rozšiřování kódu.

1. Ve třídě test přidejte následující test, který se pokusí o rozsah vstupních hodnot:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. V **Průzkumník testů**, zvolte **spustit všechny**.

   Nový test se nezdařil (i když první test stále projde). Chcete-li najít bod selhání, vyberte neúspěšný test a potom se podívejte na podrobnosti v podokně **Souhrn podrobností testu** .

3. Zkontrolujte, zda chcete zobrazit, co mohlo způsobit chybu testované metody. Upravte kód `SquareRoot` následujícím způsobem:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4. V **Průzkumník testů**, zvolte **spustit všechny**.

   Oba testy jsou nyní úspěšné.

## <a name="add-tests-for-exceptional-cases"></a>Přidejte testy výjimečných případů

1. Přidejte nový test pro záporné vstupy:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. V **Průzkumník testů**, zvolte **spustit všechny**.

   Metoda v testovacích cyklech a je nutné ji zrušit ručně.

3. Na panelu nástrojů v **Průzkumníku testů**klikněte na **tlačítko zrušit** .

   Test zastaví provádění.

4. Opravte kód `SquareRoot` přidáním následujícího příkazu `if` na začátku metody:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. V **Průzkumník testů**, zvolte **spustit všechny**.

   Všechny testy jsou úspěšné.

## <a name="refactor-the-code-under-test"></a>Refaktoring testovaného kódu

Refaktorujte kód, ale neměňte testy.

> [!TIP]
> *Refaktoring* je změna, která je určena k tomu, aby byl kód lépe nebo čitelnější. Refaktorování není zamýšleno změnit chování kódu, a proto testy zůstávají nezměněny.
>
> Doporučujeme provádět kroky refaktorování odděleně od kroků rozšiřujících funkčnost. Udržování testů v nezměněné podobě zajišťuje, že jste ještě kódu omylem zavedeny chyby během refaktoringu.

1. Změňte řádek, který vypočítá `result` v metodě `SquareRoot` následujícím způsobem:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }

        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
            previousResult = result;
            result = (result + input / result) / 2;
            //was: result = result - (result * result - input) / (2*result);
        }
        return result;
    }
    ```

2. Vyberte možnost **Spustit vše**a ověřte, zda všechny testy jsou stále průchodné.

   ![Průzkumník testů zobrazující 3 úspěšné testy](../test/media/test-driven-development-three-passed-tests.png)
