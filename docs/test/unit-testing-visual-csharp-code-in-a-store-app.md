---
title: Testování částí kódu v jazyce Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590862"
---
# <a name="unit-test-c-code"></a>Test jednotek kódu C#

Tento článek popisuje jeden ze způsobů, jak vytvořit testování částí pro třídu jazyka C# v aplikaci UWP.

**Kořenová** třída, která je zkoušenou třídou, implementuje funkci, která vypočítá odhad druhé odmocniny daného čísla.

Tento článek ukazuje *Vývoj řízený testováním*. V tomto přístupu nejprve zapíšete test, který ověří konkrétní chování v systému, který testujete, a potom napíšete kód, který projde testem.

## <a name="create-the-solution-and-the-unit-test-project"></a>Vytvořit řešení a projekt testování částí

1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**.

2. Vyhledejte a vyberte šablonu projektu **prázdná aplikace (univerzální pro Windows)** .

3. Pojmenujte **matematiky**projektu.

4. V **Průzkumník řešení**klikněte pravým tlačítkem na řešení a vyberte možnost **Přidat**  >  **Nový projekt**.

5. Vyhledejte a vyberte šablonu projektu **aplikace pro testování jednotek (univerzální pro Windows)** .

6. Pojmenujte projekt testů **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Ověřte, zda jsou testy spuštěny v Průzkumníku testů

1. Do souboru *UnitTest.cs* Vložte nějaký kód testu do **TestMethod1** :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Třída poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

::: moniker range="vs-2017"

2. V nabídce **test** vyberte možnost **Spustit** > **všechny testy**.

::: moniker-end

::: moniker range=">=vs-2019"

2. V nabídce **test** vyberte možnost **Spustit všechny testy**.

::: moniker-end

   Testovací projekt se sestaví a spustí. Být pacient, protože může chvíli trvat. Zobrazí se okno **Průzkumník testů** a test je uveden v části **prošlé testy**. Podokno **Souhrn** v dolní části okna poskytuje další podrobnosti o vybraném testu.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Přidat třídu Rooter do projektu matematického typu

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **matematického** typu a pak zvolte **Přidat**  >  **třídu**.

2. Pojmenujte soubor třídy *Rooter.cs*.

3. Do souboru *Rooter.cs* třídy **root** přidejte následující kód:

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

   Třída **Rooter** deklaruje konstruktor a metodu **SquareRoot** Estimator. Metoda **SquareRoot** je pouze minimální implementace, stačí pouze k otestování základní struktury nastavení testování.

4. Přidejte `public` klíčové slovo do deklarace třídy **Rooter** , aby k němu mohl přistupovat testovací kód.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

1. Přidejte odkaz z projektu RooterTests do aplikace Maths.

    1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **RooterTests** a pak zvolte **Přidat**  >  **odkaz**.

    2. V dialogovém okně **Přidat odkaz – RooterTests** rozbalte položku **řešení** a vyberte možnost **projekty**. Vyberte projekt **matematiky** .

        ![Přidat odkaz na projekt Maths](../test/media/ute_cs_windows_addreference.png)

2. Přidejte `using` příkaz do souboru *UnitTest.cs* :

    1. Otevřete *UnitTest.cs*.

    2. Přidejte tento kód pod `using Microsoft.VisualStudio.TestTools.UnitTesting;` řádek:

       ```csharp
       using Maths;
       ```

3. Přidejte test, který používá funkci **root** . Do *UnitTest.cs*přidejte následující kód:

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

   Nový test se zobrazí v **Průzkumníku testů** v uzlu **Nespuštěné testy** .

4. Aby nedošlo k chybě "datová část obsahuje dva nebo více souborů se stejnou cílovou cestou", v **Průzkumník řešení**rozbalte uzel **vlastnosti** v projektu **matematické** řetězce a pak odstraňte soubor *Default.rd.xml* .

::: moniker range="vs-2017"

6. V **Průzkumníku testů**vyberte možnost **Spustit vše**.

   Řešení se sestaví a spustí a projde testy.

   ![BasicTest předané v Průzkumníku testů](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. V **Průzkumníku testů**vyberte možnost **Spustit všechny testy**.

   Řešení se sestaví a spustí a projde testy.

   ![V Průzkumníku testů byl úspěšný základní test.](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Nastavili jste projekty testů a aplikací a ověřili, že můžete spouštět testy, které volají funkce v projektu aplikace. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iterativní rozšíření testů a jejich předání

1. Přidejte nový test s názvem **RangeTest**:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Doporučujeme neměnit testy, které byly úspěšné. Místo toho přidejte nový test.

2. Spusťte test **RangeTest** a ověřte, zda se nezdařila.

   ![RangeTest se nezdařila](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Ihned po zápisu testu spusťte jej a ověřte, zda se nezdařila. To pomáhá vyhnout se jednoduchému omylu při psaní testu, který se nikdy nezdařil.

3. Zvyšte testovaný kód, aby nový test prošl. Změňte funkci **SquareRoot** v *Rooter.cs* na tuto:

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

::: moniker range="vs-2017"

4. V **Průzkumníku testů**vyberte možnost **Spustit vše**.

::: moniker-end

::: moniker range=">=vs-2019"

4. V **Průzkumníku testů**vyberte možnost **Spustit všechny testy**.

::: moniker-end

   Všechny tři testy jsou nyní passované.

> [!TIP]
> Vývoj kódu přidáním testů po jednom. Ujistěte se, že všechny testy proběhnou po každé iteraci.

## <a name="refactor-the-code"></a>Refaktoring kódu

V této části provedete refaktorování aplikace a testovací kód, potom znovu spustíte testy, abyste se ujistili, že jsou stále předávány.

### <a name="simplify-the-square-root-estimation"></a>Zjednodušení čtvercového odhadu

1. Zjednodušte centrální výpočet ve funkci **SquareRoot** , a to tak, že změníte jeden řádek kódu, a to takto:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Spusťte všechny testy a ujistěte se, že jste nepředstavili regresi. Všechny by měly být passované.

> [!TIP]
> Stabilní sada dobrých testů jednotek dává jistotu, že jste při změně kódu nepředstavili chyby.

### <a name="eliminate-duplicated-code"></a>Eliminovat duplicitní kód

Metoda **RangeTest** pevně vystaví jmenovatel proměnné *tolerance* , která je předána <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodě. Pokud plánujete přidat další testy, které používají stejný výpočet tolerance, použití pevně zakódované hodnoty ve více umístěních usnadňuje údržbu kódu.

1. Přidejte soukromou pomocnou metodu do třídy **UnitTest1** pro výpočet hodnoty tolerance a pak zavolejte tuto metodu z **RangeTest**.

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
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Spusťte **RangeTest** a ujistěte se, že se pořád ještě projde.

> [!TIP]
> Pokud přidáte pomocnou metodu do třídy testu a nechcete, aby se zobrazila v **Průzkumníku testů**, nepřidávejte <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut do metody.

## <a name="see-also"></a>Viz také

- [Návod: Vývoj řízený testovacím prostředím pomocí Průzkumníka testů](quick-start-test-driven-development-with-test-explorer.md)
