---
title: Jak otestovat dll C++ pro aplikace UPW
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 540ff59838343988e7a27f42f8a10d723de1f649
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77274457"
---
# <a name="how-to-test-a-c-dll"></a>Jak otestovat dll C++

Toto téma popisuje jeden způsob, jak vytvořit testy částí pro C++ DLL pro univerzální platformu Windows (UPW) aplikace s Microsoft Test Framework pro C ++. DLL RooterLib demonstruje vágní vzpomínky teorie limitů z počtu implementací funkce, která vypočítá odhad druhé odmocniny daného čísla. DLL pak může být součástí aplikace UPW, která zobrazuje uživateli zábavné věci, které lze provést s matematikou.

Toto téma ukazuje, jak používat testování částí jako první krok ve vývoji. V tomto přístupu nejprve napíšete testovací metodu, která ověří určité chování v systému, který testujete, a pak napíšete kód, který projde testem. Provedením změn v pořadí následujících postupů, můžete stornovat tuto strategii nejprve napsat kód, který chcete testovat a potom napište testy částí.

Toto téma také vytvoří jedno řešení sady Visual Studio a samostatné projekty pro testy částí a dll, které chcete testovat. Testy částí můžete také zahrnout přímo do projektu dll nebo můžete vytvořit samostatná řešení pro testy částí a . Knihovny dll. Tipy, na které struktury se mají použít, najdete v tématu [Přidání testů částí do existujících aplikací jazyka C++.](../test/how-to-use-microsoft-test-framework-for-cpp.md)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a>Vytvoření řešení a projektu testování částí

::: moniker range="vs-2019"

Začněte vytvořením nového testovacího projektu. V nabídce **Soubor** zvolte **Nový** > **projekt**. V **dialogovém** okně Vytvořit nový projekt zadejte do vyhledávacího pole "test" a nastavte **jazyk** na C++. Pak ze seznamu šablon projektů zvolte **Aplikace pro testování částí (Universal Windows).**

   ![Vytvoření nového testovacího projektu UPW](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Začněte vytvořením nového testovacího projektu. V nabídce **Soubor** zvolte **Nový** > **projekt**. V dialogovém okně **Nový projekt** rozbalte **možnost Nainstalovaný** > **visual c++** a zvolte **Windows Universal**. Pak ze seznamu šablon projektů zvolte **Aplikace pro testování částí (Universal Windows).**

::: moniker-end

1. V dialogovém okně Nový projekt rozbalte **možnost Nainstalovaný** > **visual c++** a zvolte **Windows Universal**. Pak ze seznamu šablon projektů zvolte **Aplikace pro testování částí (Universal Windows).**

2. Název projektu `RooterLibTests`; uveďte umístění; pojmenovat `RooterLib`řešení ; a ujistěte se, že je zaškrtnuto **políčko Vytvořit adresář pro řešení.**

     ![Určení řešení a názvu a umístění projektu](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. V novém projektu otevřete **unittest1.cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Poznámky:

    - Každý test je `TEST_METHOD(YourTestName){...}`definován pomocí .

         Není třeba psát konvenční funkce podpisu. Podpis je vytvořen TEST_METHOD makra. Makro generuje funkci instance, která vrací void. Generuje také statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují průzkumníkovi testů najít metodu.

    - Zkušební metody jsou seskupeny `TEST_CLASS(YourClassName){...}`do tříd pomocí .

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v neurčeném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a po každém modulu, třídě nebo metodě. Další informace naleznete [v tématu Using Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Ověření, zda jsou testy spuštěny v Průzkumníku testů

1. Vložte nějaký testovací kód:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Všimněte `Assert` si, že třída poskytuje několik statických metod, které můžete použít k ověření výsledků v testovacích metodách.

2. V nabídce **Test** zvolte **Spustit** a pak zvolte **Spustit vše**.

     Testovací projekt se staví a spouští. Zobrazí se okno **Průzkumník testů** a test je uveden v části **Předané testy**. Podokno **Souhrn** v dolní části okna obsahuje další podrobnosti o vybraném testu.

     ![Průzkumník testů](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a>Přidání projektu DLL do řešení

::: moniker range="vs-2019"

V **Průzkumníku řešení**zvolte název řešení. V místní nabídce zvolte **Přidat**a potom **Nový projekt**. V **dialogovém** okně Přidat nový projekt nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "DLL". V seznamu výsledků zvolte **Aplikace testování částí (Universal Windows - C++/CX)**.

![Vytvoření projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
V **Průzkumníku řešení**zvolte název řešení. V místní nabídce zvolte **Přidat**a potom **Nový projekt**.

![Vytvoření projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. V dialogovém okně **Přidat nový projekt** zvolte **DLL (aplikace UPW).**

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

     Komentáře vysvětlují ifdef blok nejen pro vývojáře dll, ale pro každého, kdo odkazuje na DLL v jejich projektu. Symbol ROOTERLIB_EXPORTS můžete přidat do příkazového řádku pomocí vlastností projektu knihovny DLL.

     Třída `CRooterLib` deklaruje konstruktor a metodu `SqareRoot` odhadu.

3. Přidejte symbol ROOTERLIB_EXPORTS do příkazového řádku.

    1. V **Průzkumníku řešení**zvolte projekt **RooterLib** a pak z místní nabídky zvolte **Vlastnosti.**

         ![Přidání definice symbolu preprocesoru](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. V dialogovém okně **Stránka vlastností RooterLib** **rozbalte položku Vlastnosti konfigurace**, rozbalte **c++** a zvolte **Preprocesor**.

    3. Ze seznamu Definice **preprocesoru** `ROOTERLIB_EXPORTS` zvolte ** \<Upravit... >** a pak přidejte do dialogového okna **Definice preprocesoru.**

4. Přidejte minimální implementace deklarovaných funkcí. Otevřete *RooterLib.cpp* a přidejte následující kód:

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

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a>Zviditelnění funkcí dll pro testovací kód

1. Přidejte RooterLib do projektu RooterLibTests.

   1. V **Průzkumníku řešení**zvolte projekt **RooterLibTests** a v místní nabídce zvolte **Přidat** > **odkaz.**

   1. V dialogovém okně **Přidat odkaz** zvolte **Projekty**. Pak vyberte položku **RouterLib.**

2. Zahrnout rooterLib hlavičkový soubor v *unittest1.cpp*.

   1. Otevřete *unittest1.cpp*.

   2. Přidejte tento kód `#include "CppUnitTest.h"` pod řádek:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Přidejte test, který používá importovnou funkci. Do *unittest1.cpp*přidejte následující kód :

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

    Nový test se zobrazí v **Průzkumníku testů** v uzlu **Nespustit testy.**

5. V **Průzkumníkovi testů**zvolte **Spustit vše**.

    ![Základní test prošel](../test/media/ute_cpp_testexplorer_basictest.png)

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spustit testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Iterativně rozšířit testy a učinit je projít

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
    > Doporučujeme neměnit testy, které prošly. Místo toho přidejte nový test, aktualizujte kód tak, aby test prošel, a pak přidejte další test a tak dále.
    >
    > Pokud uživatelé změní své požadavky, zakažte testy, které již nejsou správné. Psát nové testy a aby byly pracovat jeden po druhém, stejným přírůstkovým způsobem.

2. V **Průzkumníkovi testů**zvolte **Spustit vše**.

3. Test se nezdaří.

     ![RangeTest se nezdaří](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, zda se každý test nezdaří ihned po jeho napsání. To vám pomůže vyhnout se snadné chybě psaní testu, který nikdy neselže.

4. Vylepšete testovaný kód tak, aby nový test prošel. Do souboru *RooterLib.cpp*přidejte následující :

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

5. Sestavte řešení a potom v **Průzkumníkovi testů**zvolte **Spustit vše**.

     Oba testy jsou v pořádku.

> [!TIP]
> Vývoj kódu přidáním testů jeden po druhém. Ujistěte se, že všechny testy projít po každé iteraci.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a>Ladění neúspěšného testu

1. Přidejte další test *na unittest1.cpp*:

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

2. V **Průzkumníkovi testů**zvolte **Spustit vše**.

    Test se nezdaří. V **Průzkumníku testů**zvolte název testu . Kontrolní výraz se nezdařilo je zvýrazněna. Zpráva o selhání je viditelná v podokně podrobností **Průzkumníka testů**.

    ![Testy NegativeRangeSe se nezdařily.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Chcete-li zjistit, proč test selže, krokovat funkci:

   1. Nastavte zarážku na `SquareRoot` začátku funkce.

   2. V místní nabídce neúspěšného testu zvolte **Ladění vybraných testů**.

        Když se zastaví spuštění na zarážky, krokovat kód.

   3. Přidejte kód *rooterLib.cpp* zachytit výjimku:

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

   1. V **Průzkumníkovi testů**zvolte **Spustit vše,** abyste otestovali opravenou metodu a ujistili se, že jste nezavedli regresi.

   Všechny testy nyní probíhají.

   ![Všechny testy projdou](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a>Refaktorování kódu bez změny testů

1. Zjednodušte centrální výpočet `SquareRoot` ve funkci:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Zvolte **Spustit vše,** chcete-li otestovat refaktored metodu a ujistěte se, že jste nezavedli regrese.

    > [!TIP]
    > Stabilní sada dobrých testů částí dává jistotu, že jste nezavedli chyby při změně kódu.
    >
    > Udržujte refaktoring odděleně od ostatních změn.
