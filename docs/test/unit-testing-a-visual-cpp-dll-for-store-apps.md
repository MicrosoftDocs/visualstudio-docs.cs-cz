---
title: Postup testování knihovny DLL C++ pro aplikace pro UWP
description: Naučte se, jak vytvořit testy částí pro knihovnu DLL C++ pro Univerzální platforma Windows aplikace pomocí Microsoft Test Framework pro C++.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: a7ae79ff4df783d3c4541720c9fef709087e7da6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330092"
---
# <a name="how-to-test-a-c-dll"></a>Postup testování knihovny DLL jazyka C++

Toto téma popisuje jeden ze způsobů, jak vytvořit testy jednotek pro knihovny DLL C++ pro aplikace Univerzální platforma Windows (UWP) s Microsoft Test Framework pro C++. RooterLib DLL ukazuje Vague paměti z calculus pomocí implementace funkce, která vypočítá odhad druhé odmocniny daného čísla. Knihovna DLL může být pak vložená do aplikace pro UWP, která uživatelům zobrazuje zábavné možnosti, které je možné provádět pomocí matematiky.

V tomto tématu se dozvíte, jak používat testování částí jako první krok vývoje. V tomto přístupu nejprve zapíšete testovací metodu, která ověří konkrétní chování v systému, který testujete, a pak napíšete kód, který projde testem. Provedením změn v pořadí následujících postupů můžete tuto strategii obrátit na první zápis kódu, který chcete testovat, a pak zapsat testy jednotek.

Toto téma také vytvoří jedno řešení sady Visual Studio a samostatné projekty pro testování částí a knihovnu DLL, kterou chcete testovat. Můžete také zahrnout testy jednotek přímo do projektu knihovny DLL, nebo můžete vytvořit samostatná řešení pro testy jednotek a. DLL. Tipy, které struktury se mají použít, najdete v tématu [Přidání testů jednotek do stávajících aplikací C++](../test/how-to-use-microsoft-test-framework-for-cpp.md) .

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a> Vytvořit řešení a projekt testování částí

::: moniker range="vs-2019"

Začněte vytvořením nového testovacího projektu. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. V dialogovém okně **vytvořit nový projekt** zadejte do vyhledávacího pole "test" a pak nastavte **jazyk** na C++. Pak ze seznamu šablon projektů zvolte možnost **aplikace pro testování jednotek (univerzální pro Windows)** .

   ![Vytvořit nový projekt testů UWP](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Začněte vytvořením nového testovacího projektu. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt**. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované**  >  **Visual C++** a vyberte možnost **univerzální pro systém Windows**. Pak ze seznamu šablon projektů zvolte možnost **aplikace pro testování jednotek (univerzální pro Windows)** .

::: moniker-end

1. V dialogovém okně Nový projekt rozbalte položku **nainstalované**  >  **Visual C++** a vyberte možnost **univerzální pro systém Windows**. Pak ze seznamu šablon projektů zvolte možnost **aplikace pro testování jednotek (univerzální pro Windows)** .

2. Pojmenujte projekt `RooterLibTests` , zadejte umístění, pojmenujte řešení `RooterLib` a ujistěte se, že je zaškrtnuté políčko **vytvořit adresář pro řešení** .

     ![Zadejte název řešení a název projektu a umístění](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. V novém projektu otevřete **UnitTest1. cpp**.

     ![UnitTest1. cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Poznámky:

    - Každý test je definován pomocí `TEST_METHOD(YourTestName){...}` .

         Nemusíte psát konvenční signaturu funkce. Podpis je vytvořen TEST_METHOD makra. Makro vygeneruje funkci instance, která vrací typ void. Také generuje statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují Průzkumníku testů najít metodu.

    - Testovací metody jsou seskupeny do tříd pomocí `TEST_CLASS(YourClassName){...}` .

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každým modulem, třídou nebo metodou. Další informace naleznete v tématu [using Microsoft. VisualStudio. TestTools. CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Ověřte, zda jsou testy spuštěny v Průzkumníku testů

1. Vložte nějaký kód testu:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Všimněte si, že `Assert` Třída poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

2. V nabídce **test** zvolte možnost **Spustit** a pak zvolte možnost **Spustit vše**.

     Testovací projekt se sestaví a spustí. Zobrazí se okno **Průzkumník testů** a test je uveden v části **prošlé testy**. Podokno **Souhrn** v dolní části okna poskytuje další podrobnosti o vybraném testu.

     ![Průzkumník testů](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a> Přidat projekt knihovny DLL do řešení

::: moniker range="vs-2019"

V **Průzkumník řešení** vyberte název řešení. V místní nabídce zvolte možnost **Přidat** a **Nový projekt**. V dialogovém okně **Přidat nový projekt** nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "dll". V seznamu výsledků vyberte možnost **aplikace pro testování částí (univerzální pro Windows-C++/CX)**.

![Vytvoření projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
V **Průzkumník řešení** vyberte název řešení. V místní nabídce zvolte možnost **Přidat** a **Nový projekt**.

![Vytvoření projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. V dialogovém okně **Přidat nový projekt** vyberte možnost **DLL (aplikace UWP)**.

2. Do souboru *RooterLib. h* přidejte následující kód:

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Komentáře vysvětlují blok ifdef nejen vývojářům knihovny DLL, ale každému, kdo odkazuje na knihovnu DLL ve svém projektu. Symbol ROOTERLIB_EXPORTS můžete přidat do příkazového řádku pomocí vlastností projektu knihovny DLL.

     `CRooterLib`Třída deklaruje konstruktor a `SqareRoot` metodu Estimator.

3. Přidejte symbol ROOTERLIB_EXPORTS do příkazového řádku.

    1. V **Průzkumník řešení** zvolte projekt **RooterLib** a pak v místní nabídce zvolte možnost **vlastnosti** .

         ![Přidání definice symbolu preprocesoru](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. V dialogovém okně **Stránka vlastností RooterLib** rozbalte položku **Vlastnosti konfigurace**, rozbalte položku **C++** a vyberte možnost **preprocesor**.

    3. Vyberte **\<Edit...>** ze seznamu **Definice preprocesoru** a pak ho přidejte `ROOTERLIB_EXPORTS` v dialogovém okně **definice** preprocesoru.

4. Přidejte minimální implementace deklarovaných funkcí. Otevřete *RooterLib. cpp* a přidejte následující kód:

    ```cpp
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a> Zviditelnit funkce knihovny DLL pro testovací kód

1. Přidejte RooterLib do projektu RooterLibTests.

   1. V **Průzkumník řešení** zvolte projekt **RooterLibTests** a pak zvolte **Přidat**  >  **odkaz** v místní nabídce.

   1. V dialogovém okně **Přidat odkaz** vyberte možnost **projekty**. Pak vyberte položku **RouterLib** .

2. Zahrňte hlavičkový soubor RooterLib do *UnitTest1. cpp*.

   1. Otevřete *UnitTest1. cpp*.

   2. Přidejte tento kód pod `#include "CppUnitTest.h"` řádek:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Přidejte test, který používá importovanou funkci. Do *UnitTest1. cpp* přidejte následující kód:

   ```cpp
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
       Assert::AreEqual(
           // Expected value:
           0.0,
           // Actual value:
           rooter.SquareRoot(0.0),
           // Tolerance:
           0.01,
           // Message:
           L"Basic test failed",
           // Line number - used if there is no PDB file:
           LINE_INFO());
   }
   ```

4. Sestavte řešení.

    Nový test se zobrazí v **Průzkumníku testů** v uzlu **Nespuštěné testy** .

5. V **Průzkumníku testů** vyberte možnost **Spustit vše**.

    ![Základní test byl úspěšný.](../test/media/ute_cpp_testexplorer_basictest.png)

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spouštět testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Iterativní rozšíření testů a jejich předání

1. Přidat nový test:

    ```cpp
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };
    ```

    > [!TIP]
    > Doporučujeme neměnit testy, které byly úspěšné. Místo toho přidejte nový test, aktualizujte kód tak, aby byl test úspěšný, a poté přidejte další test atd.
    >
    > Když uživatelé změní své požadavky, zakažte testy, které už nejsou správné. Zapište nové testy a zpřístupněte je po jednom, a to stejným přírůstkovým způsobem.

2. V **Průzkumníku testů** vyberte možnost **Spustit vše**.

3. Test se nezdařil.

     ![RangeTest se nezdařila](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, že se každý test nezdařil okamžitě po jeho zápisu. To pomáhá vyhnout se jednoduchému omylu při psaní testu, který se nikdy nezdařil.

4. Zvyšte testovaný kód, aby nový test prošl. Do *RooterLib. cpp* přidejte následující:

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        double result = v;
        double diff = v;
        while (diff > result/1000)
        {
            double oldResult = result;
            result = result - (result*result - v)/(2*result);
            diff = abs (oldResult - result);
        }
        return result;
    }

    ```

5. Sestavte řešení a potom v **Průzkumníku testů** zvolte možnost **Spustit vše**.

     Oba testy proběhnou.

> [!TIP]
> Vývoj kódu přidáním testů po jednom. Ujistěte se, že všechny testy proběhnou po každé iteraci.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a> Ladění neúspěšného testu

1. Přidejte další test do *UnitTest1. cpp*:

   ```cpp
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };
   ```

2. V **Průzkumníku testů** vyberte možnost **Spustit vše**.

    Test se nezdařil. V **Průzkumníku testů** vyberte název testu. Kontrolní výraz neúspěšného zpracování je zvýrazněný. Zpráva o selhání je zobrazena v podokně podrobností v **Průzkumníku testů**.

    ![NegativeRangeTests se nezdařilo](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Chcete-li zjistit, proč se test nezdařil, postupujte podle této funkce:

   1. Nastaví zarážku na začátku `SquareRoot` funkce.

   2. V místní nabídce neúspěšného testu vyberte možnost **ladit vybrané testy**.

        Když se běh zastaví na zarážce, krokovat kód.

   3. Přidejte kód do *RooterLib. cpp* pro zachycení výjimky:

       ```cpp
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1. V **Průzkumníku testů** vyberte možnost **Spustit vše** pro otestování opravené metody a ujistěte se, že jste nepředstavili regresi.

   Všechny testy jsou nyní passované.

   ![Všechny testy Pass](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a> Refaktoring kódu bez změny testů

1. Zjednodušení centrálního výpočtu ve `SquareRoot` funkci:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Zvolením možnosti **Spustit vše** otestujte metodu refaktoringu a ujistěte se, že jste nepředstavili regresi.

    > [!TIP]
    > Stabilní sada dobrých testů jednotek dává jistotu, že jste při změně kódu nepředstavili chyby.
    >
    > Udržujte refaktoring odděleně od jiných změn.
