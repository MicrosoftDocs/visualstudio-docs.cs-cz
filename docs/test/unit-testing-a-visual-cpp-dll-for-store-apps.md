---
title: Testování knihovny DLL jazyka C++ pro aplikace pro UPW
description: Naučte se vytvářet testy jednotek pro knihovnu DLL jazyka C++ Univerzální platforma Windows aplikací pomocí rozhraní Microsoft Test Framework pro C++.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: f1981b3876d2e42e992ef261738da2443edfc114
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042909"
---
# <a name="how-to-test-a-c-dll"></a>Testování knihovny DLL jazyka C++

Toto téma popisuje jeden způsob, jak vytvořit testy jednotek pro knihovnu DLL jazyka C++ pro aplikace Univerzální platforma Windows (UPW) pomocí rozhraní Microsoft Test Framework for C++. RooterLib DLL demonstruje vagní paměti teorie limitů z počtu implementací funkce, která vypočítá odhad odmocniny daného čísla. Knihovna DLL pak může být součástí aplikace pro UPW, která uživateli ukáže zábavné věci, které je možné s matematikou dělat.

Toto téma ukazuje, jak použít testování částí jako první krok ve vývoji. Při tomto přístupu nejprve napíšete testovací metodu, která ověří konkrétní chování v systému, který testujete, a pak napíšete kód, který testem projde. Provedením změn v pořadí následujících postupů můžete tuto strategii vrátit zpět, abyste nejprve napsali kód, který chcete otestovat, a pak napsat testy jednotek.

Toto téma také vytvoří jedno Visual Studio řešení a samostatné projekty pro testy jednotek a knihovnu DLL, kterou chcete testovat. Testy jednotek můžete zahrnout také přímo do projektu knihovny DLL nebo můžete vytvořit samostatná řešení pro testy jednotek a .DLL. Tipy [k použití struktury najdete v](../test/how-to-use-microsoft-test-framework-for-cpp.md) tématu Přidání testů jednotek do existujících aplikací C++.

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a> Vytvoření řešení a projektu testování částí

::: moniker range=">=vs-2019"

Začněte vytvořením nového projektu testů. V **nabídce File (Soubor)** zvolte New Project   >  **(Nový projekt).** V dialogovém **okně Create a New Project** (Vytvořit nový projekt) zadejte do vyhledávacího pole "test" a jazyk **nastavte** na C++. Pak ze seznamu šablon projektů zvolte **Unit Test App (Universal Windows).**

   ![Vytvoření nového projektu testů UPW](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Začněte vytvořením nového projektu testů. V **nabídce File (Soubor)** zvolte New Project   >  **(Nový projekt).** V dialogovém **okně Nový projekt** rozbalte položku   >  **Nainstalováno Visual C++** zvolte **Univerzální pro Windows.** Pak ze seznamu šablon projektů zvolte **Unit Test App (Universal Windows).**

::: moniker-end

1. V dialogovém okně Nový projekt rozbalte **položku**  >  **Nainstalováno Visual C++** zvolte **Univerzální pro Windows.** Pak ze seznamu šablon projektů zvolte **Unit Test App (Universal Windows).**

2. Pojmete projekt , zadejte umístění, pojmete řešení a ujistěte se, že je `RooterLibTests` `RooterLib` **zaškrtnuté** políčko Vytvořit adresář pro řešení.

     ![Zadání názvu a umístění řešení a projektu](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. V novém projektu otevřete **soubor unittest1.cpp.**

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Poznámky:

    - Každý test je definován pomocí `TEST_METHOD(YourTestName){...}` .

         Není zapisovat signaturu konvenční funkce. Podpis je vytvořen pomocí TEST_METHOD. Makro vygeneruje funkci instance, která vrací void. Generuje také statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují průzkumníku testů najít metodu .

    - Testovací metody jsou seskupené do tříd pomocí `TEST_CLASS(YourClassName){...}` .

         Při spuštění testů se vytvoří instance každé testovací třídy. Testovací metody jsou volány v neurčeném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každým modulem, třídou nebo metodou. Další informace najdete v tématu [Použití Microsoft.VisualStudio.TestTools.CppUnitTestFramework.](how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Ověření spuštění testů v Průzkumníku testů

1. Vložte nějaký testovací kód:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Všimněte `Assert` si, že třída poskytuje několik statických metod, které můžete použít k ověření výsledků v testovacích metodách.

2. V **nabídce Test** zvolte Spustit **a** pak zvolte **Spustit vše.**

     Projekt testů se sestaví a spustí. Zobrazí **se okno Průzkumník** testů a test je uvedený v části Passed Tests **(Úspěšně prošly testy).** V **podokně** Souhrn v dolní části okna najdete další podrobnosti o vybraném testu.

     ![Průzkumník testů](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a> Přidání projektu knihovny DLL do řešení

::: moniker range=">=vs-2019"

V **Průzkumník řešení** zvolte název řešení. V místní nabídce zvolte **Přidat a** pak **Nový projekt**. V dialogovém **okně Přidat nový projekt** nastavte **Jazyk** na C++ a do vyhledávacího pole zadejte "DLL". V seznamu výsledků zvolte Unit **Test App (Universal Windows - C++/CX).**

![Vytvoření projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
V **Průzkumník řešení** zvolte název řešení. V místní nabídce zvolte **Přidat a** pak **Nový projekt**.

![Vytvoření projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. V dialogovém **okně Přidat nový** projekt zvolte KNIHOVNA DLL **(aplikace pro UPW).**

2. Do souboru *RooterLib.h* přidejte následující kód:

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

     Komentáře vysvětlují blok ifdef nejen vývojáři knihovny DLL, ale také každému, kdo odkazuje na knihovnu DLL ve svém projektu. K přidání symbolu ROOTERLIB_EXPORTS na příkazový řádek můžete použít vlastnosti projektu knihovny DLL.

     Třída `CRooterLib` deklaruje konstruktor a `SqareRoot` metodu estimátoru.

3. Přidejte ROOTERLIB_EXPORTS na příkazový řádek.

    1. V **Průzkumník řešení** projektu **RooterLib** a pak **v** místní nabídce zvolte Vlastnosti.

         ![Přidání definice symbolu preprocesoru](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. V dialogovém **okně Stránka vlastností RooterLib** rozbalte **Vlastnosti konfigurace,** rozbalte **C++** a zvolte **Preprocesor**.

    3. Zvolte **\<Edit...>** ze seznamu Definice **preprocesoru** a pak přidejte do `ROOTERLIB_EXPORTS` **dialogového okna Definice preprocesoru.**

4. Přidejte minimální implementace deklarovaných funkcí. Otevřete *soubor RooterLib.cpp* a přidejte následující kód:

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

   1. V **Průzkumník řešení** projektu **RooterLibTests** a pak **v** místní nabídce zvolte Přidat  >   odkaz.

   1. V dialogovém **okně Přidat** odkaz zvolte **Projekty.** Pak vyberte položku **RouterLib.**

2. Do souboru *unittest1.cpp* zahrřte hlavičkový soubor RooterLib.

   1. Otevřete *soubor unittest1.cpp.*

   2. Pod řádek přidejte tento `#include "CppUnitTest.h"` kód:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Přidejte test, který používá importované funkce. Do souboru *unittest1.cpp* přidejte následující kód:

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

    Nový test se zobrazí v **Průzkumníku testů** v **uzlu Nespouštět** testy.

5. V **Průzkumníku testů** zvolte **Spustit vše.**

    ![Základní test byl úspěšně](../test/media/ute_cpp_testexplorer_basictest.png)

   Nastavili jste projekty testů a kódu a ověřili jste, že můžete spouštět testy, které spouštěli funkce v projektu kódu. Teď můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Iterativní většování testů a jejich průchod

1. Přidejte nový test:

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
    > Doporučujeme, abyste testy, které prošly, neměňte. Místo toho přidejte nový test, aktualizujte kód tak, aby byl test úspěšně, a pak přidejte další test atd.
    >
    > Když uživatelé změní své požadavky, zakažte testy, které už nejsou správné. Napište nové testy a zajistěte, aby postupně fungovaly postupně.

2. V **Průzkumníku testů** zvolte **Spustit vše.**

3. Test se nezdaří.

     ![RangeTest selže](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, že každý test selže ihned po jeho napsání. To vám pomůže vyhnout se jednoduché chybě při psaní testu, který nikdy neskoní.

4. Vylepšete testový kód tak, aby nový test projde. Do souboru *RooterLib.cpp přidejte následující* kód:

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

5. Sestavte řešení a pak v **Průzkumníku testů** zvolte **Spustit vše.**

     Oba testy projdou.

> [!TIP]
> Vývoj kódu přidáváním testů po jednom Ujistěte se, že všechny testy projdou po každé iteraci.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a> Ladění neúspěšného testu

1. Přidejte další test do *unittest1.cpp:*

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

2. V **Průzkumníku testů** zvolte **Spustit vše.**

    Test se nezdaří. V Průzkumníku testů zvolte **název testu.** Kontrolní výraz, který selhal, je zvýrazněný. Zpráva o selhání se zobrazí v podokně podrobností **Průzkumníka testů.**

    ![NegativeRangeTests selhalo](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Pokud chcete zobrazit, proč test selže, projděte funkci :

   1. Na začátku funkce nastavte `SquareRoot` zarážku.

   2. V místní nabídce neúspěšných testů zvolte **Ladit vybrané testy.**

        Když se spuštění zastaví na zarážce, prohlédněte si kód.

   3. Přidejte kód *do souboru RooterLib.cpp,* který výjimku zachytí:

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

   1. V **Průzkumníku** testů zvolte **Spustit** vše a otestujte opravenou metodu a ujistěte se, že jste nezaváděli regresi.

   Všechny testy teď projdou.

   ![Všechny testy jsou v pořádku.](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a> Refaktoring kódu beze změny testů

1. Zjednodušení centrálního výpočtu ve `SquareRoot` funkci:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Zvolte **Spustit vše** a otestujte refaktorované metody a ujistěte se, že jste nezaváděli regresi.

    > [!TIP]
    > Stabilní sada dobrých testů jednotek dává jistotu, že jste při změně kódu nezavázaní chyby.
    >
    > Udržujte refaktoring oddělený od ostatních změn.
