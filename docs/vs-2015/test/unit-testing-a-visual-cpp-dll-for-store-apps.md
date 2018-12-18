---
title: Testování knihovny DLL Visual C++ pro aplikace pro Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: e3cce1fcda4ccc9a4e61b5a02d719e1ceaa1d77d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816492"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Testování knihovny DLL Visual C++ pro aplikace pro Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje jeden ze způsobů vytvoření testů jednotek pro knihovny DLL C++ pro Windows Store apps knihovna DLL RooterLib ukazuje vágní paměti limit teorie z calculus implementací funkce, která vypočítá odhad odmocninu daného čísla. Knihovna DLL může potom bude zahrnutý v aplikaci Windows Store, který zobrazuje uživatele zábavných věcí, které lze provést s matematickým výrazem.  
  
 Toto téma ukazuje, jak používat jako první krok při vývoji testování částí. V takovém případě napíšete testovací metoda, která ověřuje konkrétní chování v systému, který testujete a potom napíšete kód, který projde testem. Tím, že změny v pořadí podle následujících postupů lze zrušit tuto strategii první zapisovat kód, který chcete otestovat a teprve pak píšete jednotkové testy.  
  
 V tomto tématu se vytvoří také jedno řešení sady Visual Studio a samostatné projekty pro testy jednotky a knihovny DLL, který chcete testovat. Můžete také zahrnout jednotkové testy přímo do projektu knihovny DLL, nebo můžete vytvořit samostatné řešení pro testování částí a. KNIHOVNY DLL. V tématu [přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) tipy, které struktury používat.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 Toto téma vás provede následující úlohy:  
  
 [Vytvoření řešení a projektu testování částí](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Ověřte, že testy spustit v Průzkumníku testů](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Přidat do řešení projekt knihovny DLL](#BKMK_Add_the_DLL_project_to_the_solution)  
  
 [Několik testů projektu do projektu knihovny dll](#BKMK_Couple_the_test_project_to_the_dll_project)  
  
 [Využívejte iterativní posílit testy a daly se předat](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Ladit test chybou](#BKMK_Debug_a_failing_test)  
  
 [Refaktorujte kód beze změn testů](#BKMK_Refactor_the_code_without_changing_tests)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Vytvoření řešení a projektu testování částí  
  
1.  Na **souboru** nabídce zvolte **nový**a klikněte na tlačítko **nový projekt**.  
  
2.  V dialogovém okně Nový projekt rozbalte **nainstalováno**, potom rozbalte **Visual C++** a zvolte **Windows Store**. Klikněte na tlačítko **testovací knihovna jednotky (aplikace pro Windows Store)** ze seznamu šablon projektu.  
  
     ![Vytvoření a C&#43; &#43; knihovnu testu jednotky](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")  
  
3.  Pojmenujte projekt `RooterLibTests`, zadejte umístění, název řešení `RooterLib`; a ujistěte se, že **vytvořit adresář pro řešení** je zaškrtnuté políčko.  
  
     ![Zadejte název řešení a projektu a umístění](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")  
  
4.  V novém projektu, otevřete **unittest1.cpp**.  
  
     ![unittest1.cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")  
  
     Všimněte si, že:  
  
    -   Každý test se definuje pomocí `TEST_METHOD(YourTestName){...}`.  
  
         Není nutné zapsat signaturu konvenční funkce. Podpis je makro TEST_METHOD vytvořil. Makro generuje instance funkce vracející typ void. Zároveň vytvoří statickou funkci, která vrací informace o testovací metody. Tyto informace umožňují Průzkumníka testů se najít metodu.  
  
    -   Testovací metody jsou seskupené do třídy pomocí `TEST_CLASS(YourClassName){...}`.  
  
         Při spuštění testů, je vytvořena instance každé testovací třídy. Testovací metody jsou zavolány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každého modulu, třídy nebo metody. Další informace najdete v tématu [pomocí atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) v knihovně MSDN.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Ověřte, že testy spustit v Průzkumníku testů  
  
1.  Vložte kód testu:  
  
    ```cpp  
    TEST_METHOD(TestMethod1)  
    {  
        Assert::AreEqual(1,1);  
    }  
    ```  
  
     Všimněte si, že `Assert` třída poskytuje několik statických metod, které slouží k ověření výsledků v testovacích metod.  
  
2.  Na **testovací** nabídce zvolte **spustit** a klikněte na tlačítko **spustit všechny**.  
  
     Testovací projekt vytvoří a spustí. Zobrazí se okno Průzkumníka testů a test je uvedený v části **úspěšné testy**. Souhrn v dolní části okna poskytuje další podrobnosti o vybraných testů.  
  
     ![Průzkumník testů](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Přidat do řešení projekt knihovny DLL  
  
1.  V Průzkumníku řešení zvolte název řešení. V místní nabídce zvolte **přidat**a potom **přidat nový projekt**.  
  
     ![Vytvoření projektu RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")  
  
2.  V **přidat nový projekt** dialogového okna zvolte **knihovny DLL (aplikace pro Windows Store)**.  
  
3.  Přidejte následující kód, který **RooterLib.h** souboru:  
  
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
  
     Blok ifdef vysvětlují komentáře nejen vývojář knihovny DLL, ale všem uživatelům, kteří odkazuje na knihovnu DLL ve svém projektu. ROOTERLIB_EXPORTS symbol můžete přidat do příkazového řádku s použitím vlastností projektu knihovny DLL.  
  
     `CRooterLib` Třída deklaruje konstruktor a `SqareRoot` estimator metody.  
  
4.  Přidejte ROOTERLIB_EXPORTS symbol do příkazového řádku.  
  
    1.  V Průzkumníku řešení zvolte **RooterLib** projektu a klikněte na tlačítko **vlastnosti** z místní nabídky.  
  
         ![Přidat definici symbol preprocesoru](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")  
  
    2.  V dialogovém okně stránky vlastností RooterLib rozbalte **vlastnosti konfigurace**, rozbalte **C++** a zvolte **preprocesor**.  
  
    3.  Zvolte  **\<Upravit … >** z **Definice preprocesoru** seznamu a pak přidejte `ROOTERLIB_EXPORTS` v dialogovém okně Definice preprocesoru.  
  
5.  Přidáte minimální implementace deklarovaná funkce. Otevřít **RooterLib.cpp** a přidejte následující kód:  
  
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
  
##  <a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Několik testů projektu do projektu knihovny dll  
  
1. Přidáte RooterLib RooterLibTests projektu.  
  
   1.  V Průzkumníku řešení zvolte **RooterLibTests** projektu a klikněte na tlačítko **odkazy...**  v místní nabídce.  
  
   2.  V dialogovém okně Vlastnosti projektu RooterLib rozbalte **společné vlastnosti** a zvolte **rámec a odkazy**.  
  
   3.  Zvolte **přidat nový odkaz...**  
  
   4.  V **přidat odkaz** dialogového okna rozbalte **řešení** a klikněte na tlačítko **projekty**. Vyberte **RouterLib** položky.  
  
2. Zahrnutím souboru hlaviček RooterLib v **unittest1.cpp**.  
  
   1.  Otevřít **unittest1.cpp**.  
  
   2.  Tento kód vložte do níže `#include "CppUnitTest.h"` řádku:  
  
       ```cpp  
       #include "..\RooterLib\RooterLib.h"  
       ```  
  
3. Přidáte test, který používá importované funkce. Přidejte následující kód, který **unittest1.cpp**:  
  
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
  
    Nový test se zobrazí v Průzkumníku testů v **nespuštěné testy** uzlu.  
  
5. V Průzkumníku testů, zvolte **spustit všechny**.  
  
    ![Základní Test prošel](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Využívejte iterativní posílit testy a daly se předat  
  
1.  Přidáte nový test:  
  
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
    >  Doporučujeme neměňte testy, které prošly. Místo toho přidat nový test, aktualizovat kód tak, aby byl test úspěšný a pak přidejte jiného testu, a tak dále.  
    >   
    >  Pokud uživatelé změní své požadavky, zakážete testy, které už nejsou správné. Psát nové testy a jejich fungování postupně, přírůstkové stejně.  
  
2.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
3.  Test se nezdaří.  
  
     ![Nezdaří RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Ověřte, že každý test selže okamžitě poté, co jste ho napsali. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.  
  
4.  Vylepšete testovaného kódu tak, aby nový test byl úspěšný. Přidejte následující text do **RooterLib.cpp**:  
  
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
  
5.  Sestavte řešení a v Průzkumníku testů, zvolte **spustit všechny**.  
  
     Oba testy jsou úspěšné.  
  
> [!TIP]
>  Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Ladit test chybou  
  
1. Přidat jiného testu k **unittest1.cpp**:  
  
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
  
2. V Průzkumníku testů, zvolte **spustit všechny**.  
  
    Test se nezdaří. Zvolte název testu v aplikaci Test Explorer. Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je viditelný v podokně podrobností Test Explorer.  
  
    ![NegativeRangeTests nepovedlo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Chcete-li zjistit, proč se test nezdaří, kroku pomocí funkce:  
  
   1.  Nastavit zarážku na začátku `SquareRoot` funkce.  
  
   2.  V místní nabídce neúspěšných testů, zvolte **ladit vybrané testy**.  
  
        Při spuštění se zastaví na zarážce, krokovat kód.  
  
   3.  Přidejte kód, který **RooterLib.cpp** pro zachycení výjimky:  
  
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
  
   1.  V Průzkumníku testů zvolte **spustit všechny** testovací metoda opravené a ujistěte se, že nebyla zavedena regrese.  
  
   Všechny testy jsou nyní úspěšné.  
  
   ![Všechny testy byly úspěšné](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refaktorujte kód beze změn testů  
  
1.  Zjednodušení centrální výpočet v `SquareRoot` funkce:  
  
    ```  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Zvolte **spustit všechny** testovací metoda refaktorovaný a ujistěte se, že nebyla zavedena regrese.  
  
    > [!TIP]
    >  Se spouští stabilní sada testů jednotek dobré poskytuje jistotu, že nebyly zavedeny chyby při změně kódu.  
    >   
    >  Zachovat refaktorování odděleně od jiných změn.



