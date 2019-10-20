---
title: Vizuální C# kód testování částí v aplikaci pro Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81876493d48407549237ed626fc6ec5d2175fcd7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659610"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Vizuální C# kód testování částí v aplikaci ze Storu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje jeden ze způsobů, jak vytvořit testování částí pro C# vizuální třídu v aplikaci pro Windows Store. Kořenová třída ukazuje Vague paměti mezních hodnot z calculus implementací funkce, která vypočítá odhad druhé odmocniny daného čísla. Aplikace matematiky potom může pomocí této funkce Zobrazit uživatele zábavné věci, které je možné provádět pomocí matematiky.

 Toto téma ukazuje, jak používat testování částí jako první krok vývoje. V tomto přístupu nejprve zapíšete testovací metodu, která ověří konkrétní chování v systému, který testujete, a pak napíšete kód, který projde testem. Provedením změn v pořadí následujících postupů můžete tuto strategii obrátit na první zápis kódu, který chcete testovat, a pak zapsat testy jednotek.

 Toto téma také vytvoří jedno řešení sady Visual Studio a samostatné projekty pro testování částí a knihovnu DLL, kterou chcete testovat. Můžete také zahrnout testy jednotek přímo do projektu knihovny DLL, nebo můžete vytvořit samostatná řešení pro testy jednotek a knihovnu DLL.

> [!NOTE]
> Visual Studio Community, Enterprise. a Professional poskytují další funkce pro testování částí.
>
> - Použijte libovolné rozhraní pro testování částí třetích stran a open source jednotky, které vytvořilo adaptér doplňku pro Microsoft Test Explorer. Pro testy můžete také analyzovat a zobrazit informace o pokrytí kódu.
>   - Spusťte testy po každém sestavení.
>   - VS Enterprise také obsahuje Microsoft napodobeniny, izolační rozhraní pro spravovaný kód, které vám umožní zaměřit se na vaše testy na vlastní kód nahrazením testovacího kódu pro systém a funkce třetích stran.
>
>   Další informace naleznete v tématu [ověřování kódu pomocí testů jednotek](https://msdn.microsoft.com/library/dd264975.aspx) v knihovně MSDN.

## <a name="BKMK_In_this_topic"></a>V tomto tématu
 [Vytvořit řešení a projekt testování částí](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Ověřte, zda jsou testy spuštěny v Průzkumníku testů](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Přidat třídu Rooter do projektu matematického typu](#BKMK_Add_the_Rooter_class_to_the_Maths_project)

 [Pár testovacích projektů s projektem aplikace](#BKMK_Couple_the_test_project_to_the_app_project)

 [Iterativní rozšíření testů a jejich předání](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Ladění neúspěšného testu](#BKMK_Debug_a_failing_test)

 [Refaktoring kódu](#BKMK_Refactor_the_code_)

## <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a>Vytvořit řešení a projekt testování částí

1. V nabídce **soubor** klikněte na příkaz **Nový**a zvolte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **nainstalovaná**, potom rozbalte **položku C# vizuál** a zvolte možnost **Windows Store**. Pak ze seznamu šablon projektu vyberte možnost **prázdná aplikace** .

3. Pojmenujte projekt `Maths` a ujistěte se, že je vybraná možnost **vytvořit adresář pro řešení** .

4. V Průzkumník řešení zvolte název řešení, v místní nabídce zvolte **Přidat** a pak zvolte **Nový projekt**.

5. V dialogovém okně **Nový projekt** rozbalte položku **nainstalovaná**, potom rozbalte **položku C# vizuál** a zvolte možnost **Windows Store** . Pak ze seznamu šablon projektů zvolte možnost **Knihovna testů jednotek (aplikace pro Windows Store)** .

     ![Vytvořit projekt testu jednotek](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")

6. Otevřete UnitTest1.cs v editoru sady Visual Studio.

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;
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

    1. Každý test je definován pomocí `[TestMethod]`. Testovací metoda musí vracet typ void a nemůže mít žádné parametry.

    2. Testovací metody musí být ve třídě dekorované pomocí atributu `[TestClass]`.

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v nespecifikovaném pořadí.

    3. Můžete definovat speciální metody, které jsou vyvolány před a za každým modulem, třídou nebo metodou. Další informace najdete v tématu [použití členů Microsoft. VisualStudio. TestTools. UnitTesting v rámci testování částí](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) v knihovně MSDN.

## <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a>Ověřte, zda jsou testy spuštěny v Průzkumníku testů

1. Vložte kód testu do `TestMethod1` souboru **UnitTest1.cs** :

    ```csharp

    [TestMethod]
    public void TestMethod1()
    {
        Assert.AreEqual(0, 0);
    }

    ```

     Všimněte si, že třída `Assert` poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

2. V nabídce **test** zvolte možnost **Spustit** a pak zvolte možnost **Spustit vše**.

     Testovací projekt se sestaví a spustí. Zobrazí se okno Průzkumník testů a test je uveden v části **prošlé testy**. Podokno Souhrn v dolní části okna poskytuje další podrobnosti o vybraném testu.

     ![Průzkumník testů](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a>Přidat třídu Rooter do projektu matematického typu

1. V Průzkumník řešení vyberte název projektu **matematické** názvy. V místní nabídce zvolte možnost **Přidat**a pak **Třída**.

2. Pojmenujte soubor třídy `Rooter.cs`

3. Do souboru **Rooter.cs** třídy root přidejte následující kód:

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

     Třída `Rooter` deklaruje konstruktor a metodu `SqareRoot` Estimator.

4. Metoda `SqareRoot` je pouze minimální implementace, stačí pouze k otestování základní struktury nastavení testování.

## <a name="BKMK_Couple_the_test_project_to_the_app_project"></a>Pár testovacích projektů s projektem aplikace

1. Přidejte odkaz na aplikaci matematické aplikace do projektu RooterTests.

   1. V Průzkumník řešení zvolte projekt **RooterTests** a pak zvolte **Přidat odkaz...** v místní nabídce.

   2. V dialogovém okně **Přidat odkaz – RooterTests** rozbalte položku **řešení** a vyberte možnost **projekty**. Pak vyberte položku **matematické** .

        ![Přidat odkaz na projekt Maths](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")

2. Přidejte příkaz using do souboru UnitTest1.cs:

   1. Otevřete **UnitTest1.cs**.

   2. Přidejte tento kód pod `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` řádek:

       ```csharp
       using Maths;
       ```

3. Přidejte test, který používá funkci root. Do **UnitTest1. cpp**přidejte následující kód:

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

    Nový test se zobrazí v Průzkumníku testů v uzlu **Nespuštěné testy** .

5. V Průzkumníku testů vyberte možnost **Spustit vše**.

    ![Základní test byl úspěšný.](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spouštět testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

## <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a>Iterativní rozšíření testů a jejich předání

1. Přidat nový test:

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
    > Doporučujeme neměnit testy, které byly úspěšné. Místo toho přidejte nový test, aktualizujte kód tak, aby byl test úspěšný, a poté přidejte další test atd.
    >
    >  Když uživatelé změní své požadavky, zakažte testy, které už nejsou správné. Zapište nové testy a zpřístupněte je po jednom, a to stejným přírůstkovým způsobem.

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

3. Test se nezdařil.

     ![RangeTest se nezdařila](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Ihned po jeho zápisu ověřte, že se každý test nezdařil. To pomáhá vyhnout se jednoduchému omylu při psaní testu, který se nikdy nezdařil.

4. Zvyšte testovaný kód, aby nový test prošl. Změňte funkci `SqareRoot` v **Rooter.cs** na tuto:

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

5. Sestavte řešení a potom v Průzkumníku testů zvolte možnost **Spustit vše**.

     Všechny tři testy jsou nyní passované.

> [!TIP]
> Vývoj kódu přidáním testů po jednom. Ujistěte se, že všechny testy proběhnou po každé iteraci.

## <a name="BKMK_Debug_a_failing_test"></a>Ladění neúspěšného testu

1. Přidejte další test do **UnitTest1.cs**:

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

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

    Test se nezdařil. V Průzkumníku testů vyberte název testu. Kontrolní výraz neúspěšného zpracování je zvýrazněný. Zpráva o selhání je zobrazena v podokně podrobností v Průzkumníku testů.

    ![NegativeRangeTests se nezdařilo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Chcete-li zjistit, proč se test nezdařil, postupujte podle této funkce:

   1. Nastavte zarážku na začátku `SquareRoot` funkce.

   2. V místní nabídce neúspěšného testu vyberte možnost **ladit vybrané testy**.

        Když se běh zastaví na zarážce, krokovat kód.

   3. Do metody root přidejte kód pro zachycení výjimky:

       ```csharp
       public double SquareRoot(double x)
       {
           if (x < 0.0)
           {
               throw new ArgumentOutOfRangeException();
       }

       ```

   1. V Průzkumníku testů vyberte možnost **Spustit vše** pro otestování opravené metody a ujistěte se, že jste nepředstavili regresi.

   Všechny testy jsou nyní passované.

   ![Všechny testy Pass](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="BKMK_Refactor_the_code_"></a>Refaktoring kódu
 **Zjednodušte si centrální výpočet ve funkci SquareRoot.**

1. Změna implementace výsledku

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Zvolením možnosti **Spustit vše** otestujte metodu refaktoringu a ujistěte se, že jste nepředstavili regresi.

> [!TIP]
> Stabilní sada dobrých testů jednotek dává jistotu, že jste při změně kódu nepředstavili chyby.

 **Refaktorujte testovací kód pro odstranění duplicitního kódu.**

 Všimněte si, že metoda `RangeTest` pevně zastavuje jmenovateli proměnné tolerance, která se používá v metodě `Assert`. Pokud plánujete přidat další testy, které používají stejný výpočet tolerance, použití pevně zakódované hodnoty na více místech může vést k chybám.

1. Přidejte soukromou metodu do třídy Unit1Test pro výpočet hodnoty tolerance a pak zavolejte tuto metodu místo toho.

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

2. Zvolením možnosti **Spustit vše** otestujte metodu refaktoringu a ujistěte se, že jste nezadali chybu.

> [!NOTE]
> Chcete-li přidat pomocnou metodu do třídy testu, nepřidávejte atribut `[TestMethod]` do metody. Průzkumník testů neregistruje metodu, která má být spuštěna.
