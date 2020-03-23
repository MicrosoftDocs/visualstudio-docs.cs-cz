---
title: Kód visual c# testování částí
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590862"
---
# <a name="unit-test-c-code"></a>Test jednotek kódu C#

Tento článek popisuje jeden způsob, jak vytvořit testy částí pro třídu C# v aplikaci UPW.

**Rooter** třída, která je třída testovaná, implementuje funkci, která vypočítá odhad druhou odmocninu daného čísla.

Tento článek ukazuje *vývoj řízený testem*. V tomto přístupu nejprve napíšete test, který ověří konkrétní chování v systému, který testujete, a pak napíšete kód, který projde testem.

## <a name="create-the-solution-and-the-unit-test-project"></a>Vytvoření řešení a projektu testování částí

1. V nabídce **Soubor** zvolte **Nový** > **projekt**.

2. Vyhledejte a vyberte šablonu projektu **Blank App (Universal Windows).**

3. Název projektu **Matematika**.

4. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a zvolte **Přidat** > **nový projekt**.

5. Vyhledejte a vyberte šablonu projektu **Aplikace testování částí (Universal Windows).**

6. Pojmenujte testovací projekt **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Ověření, zda jsou testy spuštěny v Průzkumníku testů

1. Vložte nějaký testovací kód do **metody TestMethod1** do souboru *UnitTest.cs:*

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Třída <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> poskytuje několik statických metod, které můžete použít k ověření výsledků v testovacích metodách.

::: moniker range="vs-2017"

2. V nabídce **Test** zvolte **Spustit** > **všechny testy**.

::: moniker-end

::: moniker range=">=vs-2019"

2. V nabídce **Test** zvolte **Spustit všechny testy**.

::: moniker-end

   Testovací projekt se staví a spouští. Buďte trpěliví, protože to může chvíli trvat. Zobrazí se okno **Průzkumník testů** a test je uveden v části **Předané testy**. Podokno **Souhrn** v dolní části okna obsahuje další podrobnosti o vybraném testu.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Přidání třídy Rooter do projektu Matematika

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt **Matematika** a pak zvolte **Přidat** > **třídu**.

2. Pojmenujte soubor třídy *Rooter.cs*.

3. Přidejte do souboru *třídy* **Rooter** Rooter.cs následující kód:

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

   **Rooter** třída deklaruje konstruktor a **SquareRoot** odhadmetody. **SquareRoot** Metoda je pouze minimální implementace, jen tolik k testování základní struktury nastavení testování.

4. Přidejte `public` klíčové slovo do deklarace třídy **Rooter,** aby k němu měl přístup testovací kód.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Přidání odkazu na projekt

1. Přidejte odkaz z projektu RooterTests do aplikace Matematika.

    1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt **RooterTests** a pak zvolte **Přidat** > **odkaz**.

    2. V dialogovém **okně Přidat odkaz - RooterTests** rozbalte **řešení** a zvolte **Projekty**. Vyberte projekt **Matematika.**

        ![Přidání odkazu na projekt Matematika](../test/media/ute_cs_windows_addreference.png)

2. Přidejte `using` příkaz do *souboru UnitTest.cs:*

    1. Otevřít *UnitTest.cs*.

    2. Přidejte tento `using Microsoft.VisualStudio.TestTools.UnitTesting;` kód pod řádek:

       ```csharp
       using Maths;
       ```

3. Přidejte test, který používá funkci **Rooter.** Do *UnitTest.cs*přidejte následující kód :

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

   Nový test se zobrazí v **Průzkumníku testů** v uzlu **Nespustit testy.**

4. Chcete-li se vyhnout chybě "Datová část obsahuje dva nebo více souborů se stejnou cílovou cestou", rozbalte v **Průzkumníku řešení**uzel **Vlastnosti** v rámci projektu **Matematika** a odstraňte soubor *Default.rd.xml.*

::: moniker range="vs-2017"

6. V **Průzkumníkovi testů**zvolte **Spustit vše**.

   Sestavení řešení a testy spustit a předat.

   ![BasicTest prošel v Průzkumníku testů](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. V **Průzkumníkovi testů**zvolte **Spustit všechny testy**.

   Sestavení řešení a testy spustit a předat.

   ![Základní test prošel v Průzkumníku testů](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Nastavili jste projekty testů a aplikací a ověřili jste, že můžete spustit testy, které volají funkce v projektu aplikace. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iterativně rozšířit testy a učinit je projít

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
   > Doporučujeme neměnit testy, které prošly. Místo toho přidejte nový test.

2. Spusťte test **RangeTest** a ověřte, zda se nezdaří.

   ![RangeTest se nezdaří](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Ihned po napsání testu jej spusťte a ověřte, zda se nezdaří. To vám pomůže vyhnout se snadné chybě psaní testu, který nikdy neselže.

3. Vylepšete testovaný kód tak, aby nový test prošel. Změňte funkci **SquareRoot** v *Rooter.cs* na toto:

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

4. V **Průzkumníkovi testů**zvolte **Spustit vše**.

::: moniker-end

::: moniker range=">=vs-2019"

4. V **Průzkumníkovi testů**zvolte **Spustit všechny testy**.

::: moniker-end

   Všechny tři testy nyní projdou.

> [!TIP]
> Vývoj kódu přidáním testů jeden po druhém. Ujistěte se, že všechny testy projít po každé iteraci.

## <a name="refactor-the-code"></a>Refaktorovat kód

V této části refaktorujete kód aplikace i testovacího kódu a pak znovu spusťte testy, abyste se ujistili, že stále projdou.

### <a name="simplify-the-square-root-estimation"></a>Zjednodušení odhadu druhou odmocninou

1. Zjednodušte centrální výpočet ve funkci **SquareRoot** změnou jednoho řádku kódu takto:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Spusťte všechny testy a ujistěte se, že jste nezavedli regresi. Všichni by měli projít.

> [!TIP]
> Stabilní sada dobrých testů částí dává jistotu, že jste nezavedli chyby při změně kódu.

### <a name="eliminate-duplicated-code"></a>Odstranění duplicitního kódu

Metoda **RangeTest** pevně kóduje jmenovatele *proměnné tolerance,* která <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> je předána metodě. Pokud máte v plánu přidat další testy, které používají stejný výpočet tolerance, použití pevně zakódované hodnoty ve více umístěních ztěžuje údržbu kódu.

1. Přidejte soukromou pomocnou metodu do třídy **UnitTest1** pro výpočet hodnoty tolerance a pak tuto metodu ozvěte z **RangeTest**.

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

2. Spusťte **RangeTest** ujistěte se, že stále prochází.

> [!TIP]
> Pokud přidáte pomocnou metodu do testovací třídy a nechcete, aby se zobrazovala <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> v **Průzkumníkovi testů**, nepřidávejte atribut do metody.

## <a name="see-also"></a>Viz také

- [Návod: Vývoj řízený testováním pomocí Průzkumníka testů](quick-start-test-driven-development-with-test-explorer.md)
