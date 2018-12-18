---
title: Testování jednotek kódu Visual C#
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 76c20fb987bb1380cb4d3f00e078aac81f26e89f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064851"
---
# <a name="unit-testing-visual-c-code"></a>Testování jednotek kódu Visual C#

Tento článek popisuje jeden ze způsobů vytvoření testů jednotek pro třídy Visual C# v aplikaci UWP. Třída Rooter ukazuje vágní paměti limit teorie z calculus implementací funkce, která vypočítá odhad odmocninu daného čísla. Matematické výrazy aplikace pak pomocí této funkce můžete zobrazit uživateli zábavných věcí, které lze provést s matematickým výrazem.

Tento článek ukazuje, jak používat jako první krok při vývoji testování částí. V takovém případě napíšete testovací metoda, která ověřuje konkrétní chování v systému, který testujete a potom napíšete kód, který projde testem. Tím, že změny v pořadí podle následujících postupů lze zrušit tuto strategii první zapisovat kód, který chcete otestovat a teprve pak píšete jednotkové testy.

Tento článek vytvoří také jedno řešení sady Visual Studio a samostatné projekty pro testy jednotky a knihovny DLL, který chcete testovat. Můžete také zahrnout jednotkové testy přímo do projektu knihovny DLL, nebo můžete vytvořit samostatné řešení pro testování částí a knihovny DLL.

## <a name="create-the-solution-and-the-unit-test-project"></a>Vytvoření řešení a projektu testování částí

1. Na **souboru** nabídce zvolte **nový** > **projektu**.

2. V **nový projekt** dialogového okna rozbalte **nainstalováno** > **Visual C#** a zvolte **Windows Universal**. Klikněte na tlačítko **prázdnou aplikaci** ze seznamu šablon projektu.

3. Pojmenujte projekt `Maths` a ujistěte se, že **vytvořit adresář pro řešení** zaškrtnuto.

4. V **Průzkumníka řešení**vyberte název řešení, vyberte **přidat** z místní nabídky a klikněte na tlačítko **nový projekt**.

5. V **nový projekt** dialogového okna rozbalte **nainstalováno**, potom rozbalte **Visual C#** a zvolte **Windows Universal**. Klikněte na tlačítko **aplikace testů jednotek (Universal Windows)** ze seznamu šablon projektu.

6. Otevřít *UnitTest1.cs* v editoru sady Visual Studio.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   Všimněte si, že:

   - Každý test se definuje pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut. Testovací metoda musí vracet typ void a nemůže mít žádné parametry.

   - Testovací metody musí být ve třídě dekorován <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atribut.

        Při spuštění testů, je vytvořena instance každé testovací třídy. Testovací metody jsou zavolány v nespecifikovaném pořadí.

   - Můžete definovat speciální metody, které jsou vyvolány před a za každého modulu, třídy nebo metody. Další informace najdete v tématu [použít rozhraní MSTest při testech jednotek](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Ověřte, že testy spustit v Průzkumníku testů

1. Vložte kód testu v TestMethod1 v *UnitTest1.cs* souboru:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Všimněte si, že <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> třída poskytuje několik statických metod, které slouží k ověření výsledků v testovacích metod.

2. Na **testovací** nabídce zvolte **spustit** a klikněte na tlačítko **spustit všechny**.

   Testovací projekt vytvoří a spustí. **Průzkumníka testů** okno a test je uvedený v části **úspěšné testy**. **Souhrn** poskytuje další podrobnosti o vybrané testovací podokno v dolní části okna.

   ![Průzkumník testů](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Přidat třídu Rooter matematické výrazy projektu

1. V **Průzkumníka řešení**, zvolte **matematické výrazy** název projektu. V místní nabídce zvolte **přidat**a potom **třídy**.

2. Název souboru třídy *Rooter.cs*.

3. Přidejte následující kód do třídy Rooter *Rooter.cs* souboru:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   `Rooter` Třída deklaruje konstruktor a `SquareRoot` estimator metody.

4. `SquareRoot` Pouze minimální implementaci, je metoda právě takové, aby test základní struktura nastavení testování.

## <a name="couple-the-test-project-to-the-app-project"></a>Několik testů projektu do projektu aplikace

1. Přidáte odkaz na aplikaci matematické výrazy RooterTests projektu.

    1. V **Průzkumníka řešení**, zvolte **RooterTests** projektu a klikněte na tlačítko **přidat odkaz** v místní nabídce.

    2. V **přidat odkaz - RooterTests** dialogového okna rozbalte **řešení** a zvolte **projekty**. Vyberte **matematické výrazy** položky.

        ![Přidat odkaz na projekt matematické výrazy](../test/media/ute_cs_windows_addreference.png)

2. Přidat sadu pomocí příkazu *UnitTest1.cs* souboru:

    1. Otevřít *UnitTest1.cs*.

    2. Přidejte tento kód níže `using Microsoft.VisualStudio.TestTools.UnitTesting;` řádku:

       ```csharp
       using Maths;
       ```

3. Přidáte test, který používá funkci Rooter. Přidejte následující kód, který *UnitTest1.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

4. Sestavte řešení.

   Nový test se zobrazí v **Průzkumníka testů** v **nespuštěné testy** uzlu.

5. V **Průzkumník testů**, zvolte **spustit všechny**.

   ![Základní Test proběhl úspěšně](../test/media/ute_cpp_testexplorer_basictest.png)

Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Využívejte iterativní posílit testy a daly se předat

1. Přidáte nový test:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = ToleranceHelper(expected);
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Doporučujeme neměňte testy, které prošly. Místo toho přidat nový test, aktualizovat kód tak, aby byl test úspěšný a pak přidejte jiného testu, a tak dále.
   >
   > Pokud uživatelé změní své požadavky, zakážete testy, které už nejsou správné. Psát nové testy a jejich fungování postupně, přírůstkové stejně.

2. V **Průzkumník testů**, zvolte **spustit všechny**.

3. Test se nezdaří.

   ![RangeTest selže](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Ihned poté, co jste ho napsali, ověřte, že každý test se nezdaří. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.

4. Vylepšete testovaného kódu tak, aby nový test byl úspěšný. Změnit `SquareRoot` fungovat v *Rooter.cs* tomuto:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

5. Sestavte řešení a potom v **Průzkumník testů**, zvolte **spustit všechny**.

   Všechny tři testy jsou nyní úspěšné.

> [!TIP]
> Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.

## <a name="debug-a-failing-test"></a>Ladit test chybou

1. Přidat jiného testu k *UnitTest1.cs*:

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. V **Průzkumník testů**, zvolte **spustit všechny**.

   Test se nezdaří. Zvolte název testu v **Průzkumníka testů**. Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je viditelný v podokně podrobností **Průzkumník testů**.

   ![NegativeRangeTests se nezdařilo](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Chcete-li zjistit, proč se test nezdaří, kroku pomocí funkce:

    1. Nastavit zarážku na začátku `SquareRoot` funkce.

    2. V místní nabídce neúspěšných testů, zvolte **ladit vybrané testy**.

        Při spuštění se zastaví na zarážce, krokovat kód.

    3. Přidejte kód do metody Rooter pro zachycení výjimky:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. V **Průzkumníka testů**, zvolte **spustit všechny** testovací metoda opravené a ujistěte se, že nebyla zavedena regrese.

Všechny testy jsou nyní úspěšné.

![Všechny testy byly úspěšné](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Refaktorování kódu

**Zjednodušení centrální výpočtu ve funkci SquareRoot.**

1. Změňte implementaci výsledek

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Zvolte **spustit všechny** testovací metoda refaktorovaný a ujistěte se, že nebyla zavedena regrese.

> [!TIP]
> Se spouští stabilní sada testů jednotek dobré poskytuje jistotu, že nebyly zavedeny chyby při změně kódu.

**Testovací kód Refaktorujte k vyloučení duplicitním kódem.**

Všimněte si, že `RangeTest` metoda pevné kódů jmenovatele `tolerance` proměnné, která je předána <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metoda. Pokud budete chtít přidat další testy, které používají stejný výpočet proti chybám, použijte hodnotu pevně zakódované v několika umístěních může vést k chybám.

1. Přidejte privátní metodu do třídy Unit1Test pro výpočet hodnoty proti chybám a místo toho volejte tuto metodu.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. Zvolte **spustit všechny** testovací metoda refaktorovaný a ujistěte se, že nebyla zavedena chybu.

> [!NOTE]
> Pokud přidáte pomocnou metodu na testovací třídu, která nechcete, aby se zobrazí v **Průzkumníka testů**, nepřidávejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut do metody.