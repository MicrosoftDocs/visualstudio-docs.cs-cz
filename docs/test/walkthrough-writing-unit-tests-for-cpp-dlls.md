---
title: 'Postupy: zápis testů jednotek pro knihovny DLL C++'
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 9458fd6886243102f6479166fb9df21f9e4869fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877254"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Postupy: zápis testů jednotek pro knihovny DLL C++

Tento návod popisuje, jak vyvíjet nativní knihovny DLL C++ pomocí první testovací metody. Základní kroky jsou následující:

1.  [Vytvořte projekt pro nativní test](#create_test_project). Projekt testů je umístěn ve stejném řešení jako projekt knihovny DLL.

2.  [Vytvoření projektu knihovny DLL](#create_dll_project). Tento návod vytvoří nová knihovna DLL, ale je podobný postup testování existující knihovny DLL.

3.  [Zpřístupnění funkcí knihovny DLL pro testy](#make_functions_visible).

4.  [Využívejte iterativní posílit testy](#iterate). Doporučujeme, abyste cyklus "červená zelená Refaktorujte", ve kterém je vývoj kódu vedené testy.

5.  [Ladit selhání testů](#debug). Testy můžete spustit v režimu ladění.

6.  [Refaktoring při udržování testů beze změny](#refactor). Refaktoring zlepšení strukturu kódu beze změny jeho chování externí prostředky. Můžete to provést na zlepšení výkonu, rozšíření a čitelnost kódu. Protože záměrem nebudou je moci měnit chování, se nezmění testy při provedení refaktoringu změny kódu. Testy pomoct, ujistěte se, že když jsou refaktoring není způsobit chyby.

7.  [Zkontrolujte pokrytí](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testování jednotek je užitečnější, když využijí víc svého kódu. Je-li zjistit, které části kódu se používají testy.

8.  [Izolace jednotky z externích zdrojů](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Obvykle je závislé na dalších komponentách systému, kterou vyvíjíte, jako jsou jiné knihovny DLL, databáze nebo subsystémy vzdálené knihovny DLL. Je užitečné k testování jednotlivých jednotek v izolaci od jeho závislosti. Externí komponenty můžete provádět testy pomalý. Během vývoje nemusí být kompletní ostatní součásti.

##  <a name="create_test_project"></a> Vytvořte projekt testu jednotek native

1.  Na **souboru** nabídce zvolte **nový** > **projektu**.

     V dialogovém okně rozbalte **nainstalováno** > **šablony** > **Visual C++** > **Test**.

     Zvolte **nativní projekt testu jednotek** šablony nebo cokoli, co nainstalované rozhraní framework dáváte přednost. Pokud zvolíte jinou šablonu, jako je Google Test a Boost.Test, základní principy jsou stejné, i když některé podrobnosti se budou lišit.

     V tomto návodu je testovací projekt s názvem `NativeRooterTest`.

     ![Vytvoření projektu testů jednotek C++](../test/media/utecpp01.png)

2.  V novém projektu, zkontrolujte **unittest1.cpp**

     ![Testovací projekt s TESTEM&#95;třídy a testování&#95;– metoda](../test/media/utecpp2.png)

     Všimněte si, že:

    -   Každý test se definuje pomocí `TEST_METHOD(YourTestName){...}`.

         Není nutné zapsat signaturu konvenční funkce. Podpis je makro TEST_METHOD vytvořil. Makro generuje instance funkce vracející typ void. Zároveň vytvoří statickou funkci, která vrací informace o testovací metody. Tyto informace umožňují Průzkumníka testů se najít metodu.

    -   Testovací metody jsou seskupené do třídy pomocí `TEST_CLASS(YourClassName){...}`.

         Při spuštění testů, je vytvořena instance každé testovací třídy. Testovací metody jsou zavolány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každého modulu, třídy nebo metody.

3.  Ověřte, že testy spustit v Průzkumníku testů:

    1.  Vložte kód testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Všimněte si, že `Assert` třída poskytuje několik statických metod, které slouží k ověření výsledků v testovacích metod.

    2.  Na **testovací** nabídce zvolte **spustit** > **všechny testy**.

         Test vytvoří a spustí.

         **Průzkumník testů** se zobrazí.

         Test je zobrazen **úspěšné testy**.

         ![Průzkumník testů jednotek s jeden úspěšných testů](../test/media/utecpp04.png)

##  <a name="create_dll_project"></a> Vytvoření projektu knihovny DLL

1.  Vytvoření **Visual C++** projektu pomocí **projekt Win32** šablony.

     V tomto názorném postupu má projekt název `RootFinder`.

     ![Vytváří se projekt C++ Win32](../test/media/utecpp05.png)

2.  Vyberte **DLL** a **symboly exportu** v Průvodci aplikací Win32.

     **Exportovat symboly** možnost generuje pohodlný makro, které můžete použít k deklarování exportovaných metod.

     ![Průvodce projektu C++ pro knihovny DLL a symboly exportu](../test/media/utecpp06.png)

3.  Deklarovat exportované funkce v objektu zabezpečení *.h* souboru:

     ![Nový kód projektu a .h souboru DLL s makry rozhraní API](../test/media/utecpp07.png)

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy viditelný mimo knihovnu DLL. Další informace najdete v tématu [používání příkazů dllimport a dllexport ve třídách jazyka C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4.  V objektu zabezpečení *.cpp* souboru, přidejte minimální tělo funkce:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

##  <a name="make_functions_visible"></a> Několik testů projektu do projektu knihovny DLL

1. Přidejte projekt knihovny DLL do odkazů projektu testovacího projektu:

   1.  Otevřete vlastnosti projektu testu a zvolte **společné vlastnosti** > **rámec a odkazy**.

        ![Vlastnosti projektu C++ | Rámec a odkazy](../test/media/utecpp08.png)

   2.  Zvolte **přidat nový odkaz**.

        V **přidat odkaz** dialogového okna, vyberte projekt knihovny DLL a vyberte **přidat**.

        ![Vlastnosti projektu C++ | Přidat nový odkaz](../test/media/utecpp09.png)

2. V hlavní Jednotkový test *.cpp* souboru, zahrnují *.h* soubor zdrojového kódu knihovny DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Přidáte základní test, který používá exportované funkce:

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
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

    Nový test se zobrazí v **Průzkumníka testů**.

5. V **Průzkumník testů**, zvolte **spustit všechny**.

    ![Průzkumník testu jednotek &#45; základní Test prošel](../test/media/utecpp10.png)

   Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.

##  <a name="iterate"></a> Využívejte iterativní posílit testy a daly se předat

1.  Přidáte nový test:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Doporučujeme neměňte testy, které prošly. Místo toho přidat nový test, aktualizovat kód tak, aby byl test úspěšný a pak přidejte jiného testu, a tak dále.
    >
    > Pokud uživatelé změní své požadavky, zakážete testy, které už nejsou správné. Psát nové testy a jejich fungování postupně, přírůstkové stejně.

2.  Sestavte řešení a potom v **Průzkumník testů**, zvolte **spustit všechny**.

     Nový test se nezdaří.

     ![RangeTest selže](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, že každý test selže okamžitě poté, co jste ho napsali. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.

3.  Vylepšení váš kód knihovny DLL tak, aby byl nový test úspěšný:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
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

4.  Sestavte řešení a potom v **Průzkumník testů**, zvolte **spustit všechny**.

     Oba testy jsou úspěšné.

     ![Průzkumník testu jednotek &#45; rozsah Test prošel](../test/media/utecpp12.png)

    > [!TIP]
    > Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.

##  <a name="debug"></a> Ladit test chybou

1.  Přidáte jiného testu:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2.  Sestavte řešení a zvolte **spustit všechny**.

3.  Otevřete (nebo dvakrát klikněte na panel) selhání testu.

     Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je viditelný v podokně podrobností **Průzkumník testů**.

     ![NegativeRangeTests se nezdařilo](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4.  Chcete-li zjistit, proč se test nezdaří, kroku pomocí funkce:

    1.  Nastavte zarážku na začátku funkce SquareRoot.

    2.  V místní nabídce neúspěšných testů, zvolte **ladit vybrané testy**.

         Při spuštění se zastaví na zarážce, krokovat kód.

5.  Vložte kód ve funkci při vývoji:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6.  Všechny testy jsou nyní úspěšné.

     ![Všechny testy byly úspěšné](../test/media/ute_ult_alltestspass.png)

> [!TIP]
> Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute_parallelicon-small.png) přepínacího tlačítka na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.


##  <a name="refactor"></a> Refaktorujte kód beze změn testů

1.  Zjednodušení centrální výpočtu ve funkci SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2.  Sestavte řešení a zvolte **spustit všechny**, abyste měli jistotu, že nebyla zavedena chybu.

    > [!TIP]
    > Správnou sadu testů jednotek poskytuje jistotu, že nebyly zavedeny chyby při změně kódu.
    >
    > Zachovat refaktorování odděleně od jiných změn.

## <a name="next-steps"></a>Další kroky

-   **Izolace.** Většinu knihoven DLL jsou závislé na ostatních subsystémů, jako jsou databáze a další knihovny DLL. Tyto součásti jsou často paralelně. Pokud chcete povolit testování, která se má provést, zatímco ostatní součásti ještě nejsou k dispozici, budete muset nahradit mock nebo

-   **Ověřovací testy sestavení.** Můžete mít testy provést na serveru sestavení vašeho týmu v nastavených intervalech. Tím se zajistí, že chyby nejsou zavedena při integraci pracovní několik členů týmu.

-   **Vrácení se změnami testy.** Můžete ukládat povinnost, aby některé testy byly provedeny před každý člen týmu vrátí kód do správy zdrojového kódu. To je obvykle podmnožinou všech ověřovacích testů sestavení.

     Lze také ukládat povinnost minimální úrovně pokrytí kódu.

## <a name="see-also"></a>Viz také:

- [Přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
- [Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití dynamické knihovny (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
