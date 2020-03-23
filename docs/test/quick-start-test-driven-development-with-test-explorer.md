---
title: Návod vývoje řízený testem
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566277"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Návod: Vývoj řízený testováním pomocí Průzkumníka testů

Vytvořte testy částí, které vám pomohou správně pracovat kód prostřednictvím přírůstkových změn kódu. Existuje několik rámců, které můžete použít k zápisu testování částí, včetně některých vyvinutých třetími stranami. Některé testovací architektury se specializují na testování v různých jazycích nebo platformách. Průzkumník testů poskytuje jediné rozhraní pro testování částí v některém z těchto rámců. Další informace o **Průzkumníkovi testů**naleznete v [tématu Spuštění testů částí pomocí nejčastějších](run-unit-tests-with-test-explorer.md) dotazů k průzkumníku testů a [Nejčastější dotazy k průzkumníku testů](test-explorer-faq.md).

Tento návod ukazuje, jak vyvinout testovky v c# pomocí Microsoft Test Framework (MSTest). Můžete snadno přizpůsobit pro jiné jazyky nebo jiné testovací architektury, jako je například NUnit. Další informace naleznete [v tématu Instalace rozhraní test ů částí jiných výrobců](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Vytvoření testu a generování kódu

1. Vytvořte projekt knihovny tříd jazyka C# **(.NET Standard).** Tento projekt bude obsahovat kód, který chceme testovat. Název projektu **MyMath**.

2. Ve stejném řešení přidejte nový projekt **testovacího projektu MSTest (.NET Core).** Pojmenujte testovací projekt **MathTests**.

   ![Nový kód a testovací projekty](../test/media/test-driven-development-ide.png)

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

4. Generovat typ z testovacího kódu.

   1. Umístěte kurzor `Rooter`na a pak z nabídky žárovky zvolte **Generovat typ 'Rooter'** > **Generovat nový typ**.

      ![Generovat rychlou akci nového typu](media/test-driven-development-generate-new-type.png)

   2. V dialogovém okně **Generovat typ** nastavte **Project** na **MyMath**, projekt knihovny tříd a pak zvolte **OK**.

      ![Dialogové okno Generovat typ v Visual Studiu 2019](media/test-driven-development-generate-type-dialog.png)

5. Generovat metodu z testovacího kódu. Umístěte kurzor `SquareRoot`na a pak z nabídky žárovky zvolte **Generovat metodu 'Rooter.SquareRoot'**.

6. Spusťte test jednotky.

   1. Chcete-li otevřít **Průzkumníka testů**, zvolte v nabídce **Test** **Explorer** **systému Windows** > .

   2. V **Průzkumníkovi testů**zvolte tlačítko **Spustit vše** a spusťte test.

   Řešení se staví a test běží a selže.

7. Vyberte název testu.

   Podrobnosti testu se zobrazí v podokně **Souhrn podrobností testu.**

   ![Souhrn podrobností testu v Průzkumníku testů](media/test-driven-development-test-detail-summary.png)

8. Vyberte horní odkaz v části **Trasování zásobníku** a přejděte do umístění, kde se test nezdařil.

V tomto okamžiku jste vytvořili test a se zakázaným inzerováním, které můžete upravit tak, aby test prošel.

## <a name="verify-a-code-change"></a>Ověření změny kódu

1. V *souboru Class1.cs* zlepšete kód `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Řešení sestaví a test běží a předá.

   ![Průzkumník testů zobrazující test](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Rozšíření rozsahu vstupů

Chcete-li zlepšit naši jistotu, že kód funguje ve všech případech, přidejte testy, které se snaží širší rozsah vstupních hodnot.

> [!TIP]
> Vyhněte se změně existující testy, které projdou. Místo toho přidejte nové testy. Stávající testy můžete změnit pouze v případě, že se změní požadavky uživatele. Tato zásada pomáhá zajistit, že neztratíte existující funkce při práci na rozšíření kódu.

1. Do testovací třídy přidejte následující test, který se pokusí rozsah vstupních hodnot:

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

2. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Nový test se nezdaří (i když první test stále prochází). Chcete-li najít bod selhání, vyberte neúspěšný test a pak se podívejte na podrobnosti v podokně **Souhrn podrobností testu.**

3. Zkontrolujte testovku, abyste zjistili, co může být špatně. Změňte `SquareRoot` kód takto:

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

4. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Oba testy nyní projít.

## <a name="add-tests-for-exceptional-cases"></a>Přidání testů pro výjimečné případy

1. Přidejte nový test negativních vstupů:

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

2. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Metoda v rámci zkoušené smyčky a musí být zrušena ručně.

3. Na panelu nástrojů **Průzkumníka testů**zvolte **Storno** .

   Test zastaví provádění.

4. Opravte `SquareRoot` kód přidáním `if` následujícího příkazu na začátek metody:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Všechny testy jsou v pořádku.

## <a name="refactor-the-code-under-test"></a>Refaktorovat testovaný kód

Refaktorovat kód, ale neměňte testy.

> [!TIP]
> *Refaktoring* je změna, která je určena k tomu, aby kód lépe nebo srozumitelněji. Není určen ke změně chování kódu, a proto testy nejsou změněny.
>
> Doporučujeme provést kroky refaktoringu odděleně od kroků, které rozšiřují funkce. Zachování testů beze změny vám dává jistotu, že jste omylem nezavedli chyby při refaktoringu.

1. Změňte řádek, `result` který `SquareRoot` se vypočítá v metodě takto:

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

2. Zvolte **Spustit vše**a ověřte, zda všechny testy stále projdou.

   ![Průzkumník testů ukazuje 3 prošlé testy](../test/media/test-driven-development-three-passed-tests.png)
