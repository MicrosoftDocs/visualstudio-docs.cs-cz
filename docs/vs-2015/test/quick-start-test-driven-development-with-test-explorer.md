---
title: 'Rychlé zprovoznění: Vývoj řízený testováním pomocí Průzkumníka testů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eae08427e9ec61c34a98f3581355909317b69559
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672262"
---
# <a name="quick-start-test-driven-development-with-test-explorer"></a>Rychlý začátek: Vývoj řízený testy s použitím Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doporučujeme vytvořit testy jednotek, které vám pomůžou zajistit správnou funkčnost kódu prostřednictvím mnoha přírůstkových kroků vývoje. Existuje několik platforem, které můžete použít k zápisu jednotkových testů, včetně některých vyvinutých třetími stranami. Některé testovací architektury jsou specializované na testování v různých jazycích nebo platformách. Průzkumník testů poskytuje jedno rozhraní pro testování částí v kterékoli z těchto rozhraní. Adaptéry jsou k dispozici pro nejčastěji používaná rozhraní a můžete napsat vlastní adaptéry pro jiné architektury.

 Průzkumník testů nahrazuje testovací okna jednotek nalezené v předchozích edicích sady Visual Studio. Zahrnuje tyto výhody:

- Spusťte rozhraní .NET, nespravované, databázové a jiné druhy testů pomocí jediného rozhraní.

- Použijte systém pro testování částí dle vašeho výběru, jako jsou NUnit nebo MSTest Framework.

- Všechny informace, které potřebujete, najdete v části v jednom okně.

## <a name="using-test-explorer"></a>Použití Průzkumníka testů
 ![Průzkumník testů jednotek zobrazující tlačítko spustit vše](../test/media/unittestexplorer-beta.png "UnitTestExplorer (beta verze)")

#### <a name="to-run-unit-tests-by-using-test-explorer"></a>Spuštění testů jednotek pomocí Průzkumníka testů

1. Vytvořte testy jednotek, které používají testovací architektury podle vašeho výběru.

    Například pro vytvoření testu, který používá MSTest Framework:

   1. Vytvořte testovací projekt.

        V dialogovém okně **Nový projekt** rozbalte položku **Visual Basic**, **Visual C#** nebo **Visual C++** a pak zvolte možnost **test**.

        Vyberte **projekt testování částí**.

   2. Každý test jednotky napište jako metodu. Každou testovací metodu zaprefixujte s `[TestMethod]` atributem.

2. Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí tlačítka ![ustit&#95;parallelicon&#45;malého](../test/media/ute-parallelicon-small.png "UTE_parallelicon – malý") přepínacího tlačítka na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

3. Na panelu nabídek vyberte možnost **test**, **Spustit testy jednotek**, **všechny testy**.

    Řešení vytvoří a spustí testy.

    Průzkumník testů otevře a zobrazí souhrn výsledků.

   **Úplný seznam testů zobrazíte takto:** Vyberte možnost **Zobrazit vše** v libovolné kategorii.

   **Chcete-li zobrazit podrobnosti o výsledku testu:** Vyberte test v Průzkumníku testů pro zobrazení podrobností, jako jsou například zprávy o výjimce v podokně podrobností.

   **Pro přechod na kód testu:** Dvakrát klikněte na test v Průzkumníku testů nebo v místní nabídce vyberte **Otevřít test** .

   **Ladění testu:** Otevřete místní nabídku pro jeden nebo více testů a pak zvolte možnost **ladit vybrané testy**.

> [!IMPORTANT]
> Výsledky, které se zobrazí, jsou pro poslední spuštění. Panel barevných výsledků zobrazuje pouze výsledky testů, které byly spuštěny. Například pokud spustíte několik testů a některé z nich dojde k selhání a potom spustíte pouze úspěšné testy, bude pruh výsledků zobrazen zeleně.

> [!NOTE]
> Pokud se nezobrazí žádný test, ujistěte se, že jste nainstalovali adaptér pro připojení Průzkumníka testů k testovacímu rozhraní, které používáte. Další informace naleznete v tématu [použití jiného testovacího rozhraní](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

## <a name="walkthrough-using-unit-tests-to-develop-a-method"></a><a name="walkthrough"></a> Návod: použití jednotkových testů pro vývoj metody
 Tento návod ukazuje, jak vyvíjet testovaný způsob v jazyce C# pomocí rozhraní testování částí společnosti Microsoft. Můžete ji snadno upravit pro jiné jazyky a použít jiné testovací architektury, jako je NUnit. Další informace naleznete v tématu [použití jiného testovacího rozhraní](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

#### <a name="creating-the-test-and-method"></a>Vytvoření testu a metody

1. Vytvořte projekt knihovny tříd jazyka Visual C#. Tento projekt bude obsahovat kód, který chceme dodat. V tomto příkladu je pojmenována `MyMath`.

2. Vytvořte testovací projekt.

   - V dialogovém okně **Nový projekt** zvolte **Visual C#**, **test** a pak zvolte **projekt testování částí**.

        ![Nový kód a projekty testů](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")

3. Napište základní testovací metodu. Ověřte výsledek získaný pro konkrétní vstup:

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
     Assert.AreEqual(expectedResult, actualResult,
         delta: expectedResult / 100);
   }
   ```

4. Vygenerujte metodu z testu.

   1. Umístěte kurzor na `Rooter` a potom v místní nabídce zvolte **Generovat**, **nový typ**.

   2. V dialogovém okně **generovat nový typ** nastavte **projekt** na projekt knihovny tříd. V tomto příkladu je to `MyMath`.

   3. Umístěte kurzor na `SquareRoot` a potom v místní nabídce zvolte **Generovat**, **Metoda stub**.

5. Spusťte test jednotky.

   1. V nabídce **test** vyberte možnost **Spustit testy jednotek**, **všechny testy**.

        Řešení se sestavuje a spustí.

        Otevře se Průzkumník testů a zobrazí výsledky.

        Test se zobrazí v části **nezdařené testy**.

6. Vyberte název testu.

    Podrobnosti testu se zobrazí v dolní části Průzkumníka testů.

7. Vyberte položky v části **trasování zásobníku** , abyste viděli, kde se test nezdařil.

   ![Průzkumník testů jednotek ukazující neúspěšný test.](../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")

   V tomto okamžiku jste vytvořili test a zástupnou proceduru, kterou upravíte, takže test projde.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Po každé změně proveďte všechny testy Pass

1. V nástroji `MyMath\Rooter.cs` zvyšte kód `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

     Kód sestaví a spustí testovací běhy.

     Test byl úspěšný.

     ![Průzkumník testů jednotek znázorňující předávání testu.](../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Přidání testů pro rozšiřování rozsahu vstupů

1. Chcete-li zvýšit jistotu, že váš kód funguje ve všech případech, přidejte testy, které vyzkouší širší rozsah vstupních hodnot.

    > [!TIP]
    > Vyhněte se změnám stávajících testů, které jsou absolvované. Místo toho přidejte nové testy. Existující testy změňte pouze v případě, že se změní požadavky uživatele. Tato zásada pomáhá zajistit, že při rozšiřování kódu nepřijdete o existující funkce.

     Do své testovací třídy přidejte následující test, který se pokusí o rozsah vstupních hodnot:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Try a range of values:
      for (double expectedResult = 1e-8;
          expectedResult < 1e+8;
          expectedResult = expectedResult * 3.2)
      {
        RooterOneValue(rooter, expectedResult);
      }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
      double input = expectedResult * expectedResult;
      double actualResult = rooter.SquareRoot(input);
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 1000);
    }
    ```

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

     Nový test se nezdařil, i když první test stále projde.

     Chcete-li najít bod selhání, vyberte neúspěšný test a potom v dolní části Průzkumníka testů vyberte horní položku **trasování zásobníku**.

3. Zkontrolujte testovaný test a podívejte se, co může být chybné. Ve `MyMath.Rooter` třídě přepište kód:

    ```
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

4. V Průzkumníku testů vyberte možnost **Spustit vše**.

     Oba testy jsou nyní passované.

#### <a name="add-tests-for-exceptional-cases"></a>Přidat testy pro výjimečné případy

1. Přidejte test pro záporné vstupy:

    ```csharp
    [TestMethod]
     public void RooterTestNegativeInputx()
     {
         Rooter rooter = new Rooter();
         try
         {
             rooter.SquareRoot(-10);
         }
         catch (ArgumentOutOfRangeException e)
         {
             return;
         }
         Assert.Fail();
     }
    ```

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

     Metoda v testovacích cyklech a je nutné ji zrušit ručně.

3. Klikněte na **tlačítko Storno**.

     Test se zastaví po 10 sekundách.

4. Opravte kód metody:

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5. V Průzkumníku testů vyberte možnost **Spustit vše**.

     Všechny testy jsou passované.

#### <a name="refactor-without-changing-tests"></a>Refaktoring bez změny testů

1. Zjednodušte kód, ale neměňte testy.

    > [!TIP]
    > *Refaktoring* je změna, která je určena k tomu, aby byl kód lépe vylepší nebo aby bylo snazší pochopit kód. Není určen pro změnu chování kódu, a proto testy nejsou změněny.
    >
    >  Doporučujeme provést kroky refaktoringu nezávisle na krocích, které rozšiřuje funkčnost. Zachování nezměněných testů vám poskytne jistotu, že jste omylem nepředstavili chyby během refaktoringu.

    ```csharp
    public class Rooter
    {
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
    }
    ```

2. Vyberte **Spustit vše**.

     Všechny testy jsou stále průchodné.

     ![Průzkumník testů jednotek zobrazující 3 úspěšné testy.](../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")
