---
title: Testování částí Visual C++ DLL pro aplikace pro Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d5f86eb40e1401f98a4c66d0b971fb006762cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659698"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Testování částí Visual C++ DLL pro aplikace pro Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje jeden ze způsobů, jak vytvořit testy jednotek pro knihovnu DLL C++ pro aplikace pro Windows Store. knihovna RooterLib DLL ukazuje Vague paměti mezních hodnot z calculusy implementací funkce, která vypočítá odhad druhé odmocniny daného čísla. Knihovna DLL může být pak zahrnuta v aplikaci pro Windows Store, která uživatelům zobrazuje zábavné možnosti, které je možné provádět pomocí matematiky.

 V tomto tématu se dozvíte, jak používat testování částí jako první krok vývoje. V tomto přístupu nejprve zapíšete testovací metodu, která ověří konkrétní chování v systému, který testujete, a pak napíšete kód, který projde testem. Provedením změn v pořadí následujících postupů můžete tuto strategii obrátit na první zápis kódu, který chcete testovat, a pak zapsat testy jednotek.

 Toto téma také vytvoří jedno řešení sady Visual Studio a samostatné projekty pro testování částí a knihovnu DLL, kterou chcete testovat. Můžete také zahrnout testy jednotek přímo do projektu knihovny DLL, nebo můžete vytvořit samostatná řešení pro testy jednotek a. DLL. Tipy, které struktury se mají použít, najdete v tématu [Přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 Toto téma vás provede následujícími úlohami:

 [Vytvořit řešení a projekt testování částí](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Ověřte, zda jsou testy spuštěny v Průzkumníku testů](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Přidat projekt knihovny DLL do řešení](#BKMK_Add_the_DLL_project_to_the_solution)

 [Spojit projekt testů s projektem knihovny DLL](#BKMK_Couple_the_test_project_to_the_dll_project)

 [Iterativní rozšíření testů a jejich předání](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Ladění neúspěšného testu](#BKMK_Debug_a_failing_test)

 [Refaktoring kódu bez změny testů](#BKMK_Refactor_the_code_without_changing_tests)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Vytvořit řešení a projekt testování částí

1. V nabídce **soubor** klikněte na příkaz **Nový**a zvolte možnost **Nový projekt**.

2. V dialogovém okně Nový projekt rozbalte položku **nainstalovaná**a potom rozbalte položku **Visual C++** a zvolte možnost **Windows Store**. Pak ze seznamu šablon projektů zvolte možnost **Knihovna testů jednotek (aplikace pro Windows Store)** .

     ![Vytvoření knihovny testů jednotek&#43;&#43; v jazyce C](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")

3. Pojmenujte projekt `RooterLibTests` , zadejte umístění, pojmenujte řešení `RooterLib` a ujistěte se, že je zaškrtnuté políčko **vytvořit adresář pro řešení** .

     ![Zadejte název řešení a název projektu a umístění](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")

4. V novém projektu otevřete **UnitTest1. cpp**.

     ![UnitTest1. cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")

     Poznámky:

    - Každý test je definován pomocí `TEST_METHOD(YourTestName){...}` .

         Nemusíte psát konvenční signaturu funkce. Podpis je vytvořen TEST_METHOD makra. Makro vygeneruje funkci instance, která vrací typ void. Také generuje statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují Průzkumníku testů najít metodu.

    - Testovací metody jsou seskupeny do tříd pomocí `TEST_CLASS(YourClassName){...}` .

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každým modulem, třídou nebo metodou. Další informace naleznete v tématu [použití Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) v knihovně MSDN.

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Ověřte, zda jsou testy spuštěny v Průzkumníku testů

1. Vložte nějaký kód testu:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Všimněte si, že `Assert` Třída poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

2. V nabídce **test** zvolte možnost **Spustit** a pak zvolte možnost **Spustit vše**.

     Testovací projekt se sestaví a spustí. Zobrazí se okno Průzkumník testů a test je uveden v části **prošlé testy**. Podokno Souhrn v dolní části okna poskytuje další podrobnosti o vybraném testu.

     ![Průzkumník testů](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="add-the-dll-project-to-the-solution"></a><a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Přidat projekt knihovny DLL do řešení

1. V Průzkumník řešení vyberte název řešení. V místní nabídce zvolte možnost **Přidat**a pak **Přidat nový projekt**.

     ![Vytvoření projektu RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")

2. V dialogovém okně **Přidat nový projekt** vyberte možnost **DLL (aplikace pro Windows Store)**.

3. Do souboru **RooterLib. h** přidejte následující kód:

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

4. Přidejte symbol ROOTERLIB_EXPORTS do příkazového řádku.

    1. V Průzkumník řešení zvolte projekt **RooterLib** a pak v místní nabídce zvolte možnost **vlastnosti** .

         ![Přidání definice symbolu preprocesoru](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")

    2. V dialogovém okně Stránka vlastností RooterLib rozbalte položku **Vlastnosti konfigurace**, rozbalte položku **C++** a vyberte možnost **preprocesor**.

    3. Vyberte **\<Edit...>** ze seznamu **Definice preprocesoru** a pak ho přidejte `ROOTERLIB_EXPORTS` v dialogovém okně Definice preprocesoru.

5. Přidejte minimální implementace deklarovaných funkcí. Otevřete **RooterLib. cpp** a přidejte následující kód:

    ```
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

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Spojit projekt testů s projektem knihovny DLL

1. Přidejte RooterLib do projektu RooterLibTests.

   1. V Průzkumník řešení zvolte projekt **RooterLibTests** a pak zvolte **odkazy...** v místní nabídce.

   2. V dialogovém okně Vlastnosti projektu RooterLib rozbalte položku **společné vlastnosti** a vyberte možnost **Architektura a odkazy**.

   3. Zvolit **Přidat nový odkaz...**

   4. V dialogovém okně **Přidat odkaz** rozbalte položku **řešení** a pak zvolte možnost **projekty**. Pak vyberte položku **RouterLib** .

2. Zahrňte hlavičkový soubor RooterLib do **UnitTest1. cpp**.

   1. Otevřete **UnitTest1. cpp**.

   2. Přidejte tento kód pod `#include "CppUnitTest.h"` řádek:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Přidejte test, který používá importovanou funkci. Do **UnitTest1. cpp**přidejte následující kód:

   ```
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

    Nový test se zobrazí v Průzkumníku testů v uzlu **Nespuštěné testy** .

5. V Průzkumníku testů vyberte možnost **Spustit vše**.

    ![Základní test byl úspěšný.](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spouštět testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Iterativní rozšíření testů a jejich předání

1. Přidat nový test:

    ```
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
    >  Když uživatelé změní své požadavky, zakažte testy, které už nejsou správné. Zapište nové testy a zpřístupněte je po jednom, a to stejným přírůstkovým způsobem.

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

3. Test se nezdařil.

     ![RangeTest se nezdařila](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Ověřte, že se každý test nezdařil okamžitě po jeho zápisu. To pomáhá vyhnout se jednoduchému omylu při psaní testu, který se nikdy nezdařil.

4. Zvyšte testovaný kód, aby nový test prošl. Do **RooterLib. cpp**přidejte následující:

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

5. Sestavte řešení a potom v Průzkumníku testů zvolte možnost **Spustit vše**.

     Oba testy proběhnou.

> [!TIP]
> Vývoj kódu přidáním testů po jednom. Ujistěte se, že všechny testy proběhnou po každé iteraci.

## <a name="debug-a-failing-test"></a><a name="BKMK_Debug_a_failing_test"></a> Ladění neúspěšného testu

1. Přidejte další test do **UnitTest1. cpp**:

   ```
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

2. V Průzkumníku testů vyberte možnost **Spustit vše**.

    Test se nezdařil. V Průzkumníku testů vyberte název testu. Kontrolní výraz neúspěšného zpracování je zvýrazněný. Zpráva o selhání je zobrazena v podokně podrobností v Průzkumníku testů.

    ![NegativeRangeTests se nezdařilo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Chcete-li zjistit, proč se test nezdařil, postupujte podle této funkce:

   1. Nastaví zarážku na začátku `SquareRoot` funkce.

   2. V místní nabídce neúspěšného testu vyberte možnost **ladit vybrané testy**.

        Když se běh zastaví na zarážce, krokovat kód.

   3. Přidejte kód do **RooterLib. cpp** pro zachycení výjimky:

       ```
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

   1. V Průzkumníku testů vyberte možnost **Spustit vše** pro otestování opravené metody a ujistěte se, že jste nepředstavili regresi.

   Všechny testy jsou nyní passované.

   ![Všechny testy Pass](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="refactor-the-code-without-changing-tests"></a><a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refaktoring kódu bez změny testů

1. Zjednodušení centrálního výpočtu ve `SquareRoot` funkci:

    ```
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Zvolením možnosti **Spustit vše** otestujte metodu refaktoringu a ujistěte se, že jste nepředstavili regresi.

    > [!TIP]
    > Stabilní sada dobrých testů jednotek dává jistotu, že jste při změně kódu nepředstavili chyby.
    >
    >  Udržujte refaktoring odděleně od jiných změn.
