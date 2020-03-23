---
title: 'Postup: Zápis testů částí pro knihovny DLL jazyka C++'
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 752a2bb53e25954824a1400ee178cd0cbf4adcf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275421"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Postup: Zápis testů částí pro knihovny DLL jazyka C++

Tento návod popisuje, jak vytvořit nativní dll C++ pomocí první test metodiky. Základní kroky jsou následující:

1. [Vytvořte nativní testovací projekt](#create_test_project). Testovací projekt je umístěn ve stejném řešení jako projekt DLL.

2. [Vytvořte projekt DLL](#create_dll_project). Tento návod vytvoří novou dll, ale postup pro testování existující DLL je podobný.

3. [Zviditelnit funkce DLL pro testy](#make_functions_visible).

4. [Iterativně rozšířit testy](#iterate). Doporučujeme cyklus "červeno-zelené refaktorování", ve kterém je vývoj kódu veden testy.

5. [Ladění selhává testy](#debug). Testy můžete spustit v režimu ladění.

6. [Refaktorovat při zachování testů beze změny](#refactor). Refaktoring znamená zlepšení struktury kódu beze změny jeho vnější chování. Můžete to udělat ke zlepšení výkonu, rozšiřitelnost nebo čitelnost kódu. Vzhledem k tomu, že záměrem není změnit chování, nezměníte testy při provádění změny refaktoringu kódu. Testy pomáhají zajistit, že nezavedete chyby při refaktoringu.

7. [Zkontrolujte pokrytí](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy částí jsou užitečnější při jejich cvičení více kódu. Můžete zjistit, které části kódu byly použity testy.

8. [Izolujte jednotky od externích zdrojů](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Knihovna DLL je obvykle závislá na jiných součástech systému, který vyvíjíte, například na jiných knihovnách DLL, databázích nebo vzdálených subsystémech. Je užitečné otestovat každou jednotku izolovaně od jejích závislostí. Externí součásti mohou provádět testy spustit pomalu. Během vývoje nemusí být ostatní součásti dokončeny.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a>Vytvoření projektu testování nativní jednotky

1. V nabídce **Soubor** zvolte **Nový** > **projekt**.

     **Visual Studio 2017 a starší**: Rozbalte **nainstalované** > **šablony** > **Visual C++** > **Test**.
     **Visual Studio 2019**: Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test".

     Zvolte šablonu **nativního projektu testování částí** nebo jakýkoli nainstalovaný rámec, který dáváte přednost. Pokud zvolíte jinou šablonu, například Google Test nebo Boost.Test, základní principy jsou stejné, i když některé podrobnosti se budou lišit.

     V tomto návodu je projekt `NativeRooterTest`testu pojmenován .

2. V novém projektu zkontrolujte **unittest1.cpp**

     ![Zkušební projekt s metodou TEST&#95;TŘÍDY a&#95;TESTU](../test/media/utecpp2.png)

     Všimněte si, že:

    - Každý test je `TEST_METHOD(YourTestName){...}`definován pomocí .

         Není třeba psát konvenční funkce podpisu. Podpis je vytvořen TEST_METHOD makra. Makro generuje funkci instance, která vrací void. Generuje také statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují průzkumníkovi testů najít metodu.

    - Zkušební metody jsou seskupeny `TEST_CLASS(YourClassName){...}`do tříd pomocí .

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v neurčeném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a po každém modulu, třídě nebo metodě.

3. Ověřte, zda jsou testy spuštěny v Průzkumníku testů:

    1. Vložte nějaký testovací kód:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Všimněte `Assert` si, že třída poskytuje několik statických metod, které můžete použít k ověření výsledků v testovacích metodách.

    2. V nabídce **Test** zvolte **Spustit** > **všechny testy**.

         Test sestaví a spustí.

         Zobrazí se **Průzkumník testů.**

         Test se zobrazí v části **Předané testy**.

         ![Průzkumník testování částí s jedním testem](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a>Vytvoření projektu DLL

::: moniker range="vs-2019"

Následující kroky ukazují, jak vytvořit projekt DLL v sadě Visual Studio 2019.

1. Vytvoření projektu jazyka C++ pomocí **Průvodce plochu systému Windows**: Klikněte pravým tlačítkem myši na název řešení v **Průzkumníku řešení** a zvolte **Přidat** > **nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "windows". Ze seznamu výsledků zvolte **Průvodce plochami systému Windows.**

     V tomto návodu je `RootFinder`projekt pojmenován .

2. Stiskněte **Vytvořit**. V dalším dialogovém okně v části **Typ aplikace** zvolte **DynamicKá knihovna odkazů (dll)** a také **zaškrtněte políčko Exportovat symboly**.

     Volba **Exportovat symboly** generuje vhodné makro, které můžete použít k deklarování exportovaných metod.

     ![Sada průvodce projektem c++ pro dll a exportovat symboly](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Deklarujte exportovnou funkci v základním souboru *H:*

     ![Nový projekt kódu DLL a soubor H s makry rozhraní API](../test/media/utecpp07.png)

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy, které mají být viditelné mimo DLL. Další informace naleznete [v tématu Použití dllimport a dllexport v C++ třídy](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Do základního souboru *CPP* přidejte minimální tělo funkce:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Následující kroky ukazují, jak vytvořit projekt DLL v sadě Visual Studio 2017.

1. Vytvořte projekt Jazyka C++ pomocí šablony **projektu Win32.**

     V tomto návodu je `RootFinder`projekt pojmenován .

2. V Průvodci aplikací win32 vyberte **dll** a **exportovat symboly.**

     Volba **Exportovat symboly** generuje vhodné makro, které můžete použít k deklarování exportovaných metod.

     ![Sada průvodce projektem c++ pro dll a exportovat symboly](../test/media/utecpp06.png)

3. Deklarujte exportovnou funkci v základním souboru *H:*

     ![Nový projekt kódu DLL a soubor H s makry rozhraní API](../test/media/utecpp07.png)

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy, které mají být viditelné mimo DLL. Další informace naleznete [v tématu Použití dllimport a dllexport v C++ třídy](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Do základního souboru *CPP* přidejte minimální tělo funkce:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a>Spárovat testovací projekt s projektem DLL

1. Přidejte projekt DLL do odkazů na projekt testovacího projektu:

   1. Klikněte pravým tlačítkem myši na uzel testovacího projektu v **Průzkumníku řešení** a zvolte **Přidat** > **odkaz**.

   2. V dialogovém okně **Přidat odkaz** vyberte projekt DLL a zvolte **Přidat**.

        ![Vlastnosti projektu jazyka C++ | Přidat nový odkaz](../test/media/utecpp09.png)

2. Do souboru *CPP* základního testování částí zahrňte soubor *H* kódu DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Přidejte základní test, který používá exportovnou funkci:

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

    Nový test se zobrazí v **Průzkumníku testů**.

5. V **Průzkumníkovi testů**zvolte **Spustit vše**.

    ![Test jednotky Explorer &#45; základní test předán](../test/media/utecpp10.png)

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spustit testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a>Iterativně rozšířit testy a učinit je projít

1. Přidejte nový test:

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
    > Doporučujeme neměnit testy, které prošly. Místo toho přidejte nový test, aktualizujte kód tak, aby test prošel, a pak přidejte další test a tak dále.
    >
    > Pokud uživatelé změní své požadavky, zakažte testy, které již nejsou správné. Psát nové testy a aby byly pracovat jeden po druhém, stejným přírůstkovým způsobem.

2. Sestavte řešení a pak v **Průzkumníkovi testů**zvolte **Spustit vše**.

     Nový test se nezdaří.

     ![RangeTest se nezdaří](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, zda se každý test nezdaří ihned po jeho napsání. To vám pomůže vyhnout se snadné chybě psaní testu, který nikdy neselže.

3. Vylepšete kód DLL tak, aby nový test prošel:

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

4. Sestavte řešení a potom v **Průzkumníkovi testů**zvolte **Spustit vše**.

     Oba testy jsou v pořádku.

     ![Test jednotky Explorer &#45; rozsah test předán](../test/media/utecpp12.png)

    > [!TIP]
    > Vývoj kódu přidáním testů jeden po druhém. Ujistěte se, že všechny testy projít po každé iteraci.

## <a name="debug-a-failing-test"></a><a name="debug"></a>Ladění neúspěšného testu

1. Přidejte další test:

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

2. Sestavte řešení a zvolte **Spustit vše**.

3. Otevřete (nebo poklepejte) neúspěšný test.

     Kontrolní výraz se nezdařilo je zvýrazněna. Zpráva o selhání je viditelná v podokně podrobností **Průzkumníka testů**.

     ![Testy NegativeRangeSe se nezdařily.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Chcete-li zjistit, proč test selže, krokovat funkci:

    1. Nastavte zarážku na začátku funkce SquareRoot.

    2. V místní nabídce neúspěšného testu zvolte **Ladění vybraných testů**.

         Když se zastaví spuštění na zarážky, krokovat kód.

5. Vložte kód do funkce, kterou vyvíjíte:

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

6. Všechny testy nyní probíhají.

   ![Všechny testy projdou](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Pokud jednotlivé testy nemají žádné závislosti, které brání jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testu s ![ute&#95;parallelicon&#45;malé](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Pokud jednotlivé testy nemají žádné závislosti, které brání jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testu v nabídce nastavení panelu nástrojů. To může výrazně zkrátit dobu trvalou ke spuštění všech testů.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a>Refaktorování kódu bez změny testů

1. Zjednodušte centrální výpočet ve funkci SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Sestavte řešení a zvolte **Spustit vše**, abyste se ujistili, že jste nezavedli chybu.

    > [!TIP]
    > Dobrá sada testů částí dává jistotu, že jste nezavedli chyby při změně kódu.
    >
    > Udržujte refaktoring odděleně od ostatních změn.

## <a name="next-steps"></a>Další kroky

- **Izolace.** Většina knihoven DLL je závislá na jiných subsystémech, jako jsou databáze a jiné knihovny DLL. Tyto další komponenty jsou často vyvíjeny paralelně. Chcete-li povolit testování částí, zatímco ostatní součásti ještě nejsou k dispozici, musíte nahradit mock nebo

- **Sestavení ověřovacích testů.** Testy můžete provést na serveru sestavení vašeho týmu v nastavených intervalech. Tím je zajištěno, že chyby nejsou zavedeny při integrované práce několika členů týmu.

- **Testy vrácení se změnami.** Můžete nařídit, že některé testy jsou prováděny před každý člen týmu kontroluje kód do správy zdrojového kódu. Obvykle se jedná o podmnožinu kompletní sadu testů ověření sestavení.

   Můžete také nařídit minimální úroveň pokrytí kódu.

## <a name="see-also"></a>Viz také

- [Přidání testů částí do existujících aplikací jazyka C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: Vytvoření a použití knihovny dynamických odkazů (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
