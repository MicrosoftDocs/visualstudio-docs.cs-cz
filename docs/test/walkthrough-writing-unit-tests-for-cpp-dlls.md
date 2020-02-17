---
title: 'Postupy: zápis testů jednotek pro C++ knihovny DLL'
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 752a2bb53e25954824a1400ee178cd0cbf4adcf2
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275421"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Postupy: zápis testů jednotek pro C++ knihovny DLL

Tento návod popisuje, jak vyvíjet nativní C++ knihovny DLL pomocí metodologie test-First. Základní postup je následující:

1. [Vytvořte nativní testovací projekt](#create_test_project). Testovací projekt se nachází ve stejném řešení jako projekt knihovny DLL.

2. [Vytvořte projekt knihovny DLL](#create_dll_project). Tento návod vytvoří novou knihovnu DLL, ale procedura pro testování existující knihovny DLL je podobná.

3. [Zpřístupněte funkce knihovny DLL pro testy](#make_functions_visible).

4. Provede [iterativní rozšíření testů](#iterate). Doporučujeme cyklus "Red-zelená-refaktor", ve kterém se vývoj kódu vede pomocí testů.

5. [Ladění neúspěšných testů](#debug). Testy můžete spouštět v režimu ladění.

6. [Refaktorujte a zachová testy beze změny](#refactor). Refaktoring znamená vylepšení struktury kódu beze změny jeho vnějšího chování. Můžete to udělat ke zlepšení výkonu, rozšiřitelnosti nebo čitelnosti kódu. Vzhledem k tomu, že záměr nemění chování, testy neměníte při provádění změn v kódu v refaktoringu. Testy vám pomohou zajistit, aby při refaktoringu nedošlo k chybám.

7. [Podívejte](using-code-coverage-to-determine-how-much-code-is-being-tested.md)se na pokrytí. Testy jednotek jsou užitečnější při cvičení více kódu. Můžete zjistit, které části kódu byly používány testy.

8. [Izolujte jednotky od externích prostředků](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Obvykle je knihovna DLL závislá na dalších součástech systému, které vyvíjíte, například jiných knihoven DLL, databází nebo vzdálených subsystémů. Je vhodné testovat každou jednotku v izolaci z jejích závislostí. Externí komponenty můžou testy běžet pomalu. Během vývoje nemusí být ostatní součásti dokončeny.

## <a name="create_test_project"></a>Vytvořit nativní projekt testu jednotek

1. V nabídce **soubor** vyberte možnost **Nový** > **projekt**.

     **Visual Studio 2017 a starší**: rozbalte položku **nainstalované** > **šablony** > **Visual C++**  > **test**.
     **Visual Studio 2019**: nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "test".

     Vyberte šablonu **projektu nativní testování částí** nebo libovolné nainstalované rozhraní, které dáváte přednost. Pokud zvolíte jinou šablonu, například Google Test nebo zvýšení. test, jsou základní principy stejné, i když se některé podrobnosti budou lišit.

     V tomto návodu se projekt testů jmenuje `NativeRooterTest`.

2. V novém projektu zkontrolujte **UnitTest1. cpp.**

     ![Testovací projekt s testovací&#95;třídou a&#95;testovací metodou](../test/media/utecpp2.png)

     Všimněte si, že:

    - Každý test je definován pomocí `TEST_METHOD(YourTestName){...}`.

         Není nutné zapsat signaturu konvenční funkce. Podpis je makro TEST_METHOD vytvořil. Makro generuje instance funkce vracející typ void. Zároveň vytvoří statickou funkci, která vrací informace o testovací metody. Tyto informace umožňují Průzkumníka testů se najít metodu.

    - Testovací metody jsou seskupeny do tříd pomocí `TEST_CLASS(YourClassName){...}`.

         Při spuštění testů, je vytvořena instance každé testovací třídy. Testovací metody jsou zavolány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každého modulu, třídy nebo metody.

3. Ověřte, zda jsou testy spuštěny v Průzkumníku testů:

    1. Vložte kód testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Všimněte si, že třída `Assert` poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

    2. V nabídce **test** vyberte možnost **Spustit** > **všechny testy**.

         Test se vytvoří a spustí.

         Zobrazí se **Průzkumník testů** .

         Test se zobrazí v části **prošlé testy**.

         ![Průzkumník testů jednotek s jedním úspěšným testem](../test/media/utecpp04.png)

## <a name="create_dll_project"></a>Vytvoření projektu knihovny DLL

::: moniker range="vs-2019"

Následující kroky ukazují, jak vytvořit projekt knihovny DLL v aplikaci Visual Studio 2019.

1. Vytvoření C++ projektu pomocí **Průvodce desktopovou aplikací Windows**: klikněte pravým tlačítkem myši na název řešení v **Průzkumník řešení** a vyberte **Přidat** > **Nový projekt**. Nastavte **jazyk** na C++ a do vyhledávacího pole zadejte "Windows". V seznamu výsledků vyberte možnost **Průvodce desktopovou plochou systému Windows** .

     V tomto návodu se projekt jmenuje `RootFinder`.

2. Stiskněte **Vytvořit**. V dalším dialogovém okně v části **Typ aplikace** vyberte **dynamická knihovna (DLL)** a také zaškrtněte políčko **exportovat symboly**.

     Možnost **exportovat symboly** generuje pohodlné makro, které lze použít k deklaraci exportovaných metod.

     ![C++Průvodce projektem nastaven pro knihovnu DLL a exportovat symboly](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Deklarujte exportovanou funkci v souboru Principal *. h* :

     ![Nový projekt kódu knihovny DLL a soubor. h s makry rozhraní API](../test/media/utecpp07.png)

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy budou viditelné vně knihovny DLL. Další informace naleznete v tématu [použití dllimport a dllexport ve C++ třídách](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Do souboru Principal *. cpp* přidejte minimální text pro funkci:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Následující kroky ukazují, jak vytvořit projekt knihovny DLL v aplikaci Visual Studio 2017.

1. Vytvořte C++ projekt pomocí šablony **projektu Win32** .

     V tomto návodu se projekt jmenuje `RootFinder`.

2. V Průvodci aplikací Win32 vyberte **DLL** a **exportujte symboly** .

     Možnost **exportovat symboly** generuje pohodlné makro, které lze použít k deklaraci exportovaných metod.

     ![C++Průvodce projektem nastaven pro knihovnu DLL a exportovat symboly](../test/media/utecpp06.png)

3. Deklarujte exportovanou funkci v souboru Principal *. h* :

     ![Nový projekt kódu knihovny DLL a soubor. h s makry rozhraní API](../test/media/utecpp07.png)

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy budou viditelné vně knihovny DLL. Další informace naleznete v tématu [použití dllimport a dllexport ve C++ třídách](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. Do souboru Principal *. cpp* přidejte minimální text pro funkci:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="make_functions_visible"></a>Spojit projekt testů s projektem knihovny DLL

1. Přidejte projekt knihovny DLL do odkazů projektu testovacího projektu:

   1. Klikněte pravým tlačítkem myši na uzel testovací projekt v **Průzkumník řešení** a vyberte možnost **Přidat** > **odkaz**.

   2. V dialogovém okně **Přidat odkaz** vyberte projekt knihovny DLL a zvolte možnost **Přidat**.

        ![C++vlastnosti projektu | Přidat nový odkaz](../test/media/utecpp09.png)

2. V souboru hlavní jednotky test *. cpp* zahrňte soubor *. h* kódu dll:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Přidejte základní test, který používá exportovanou funkci:

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

5. V **Průzkumníku testů**vyberte možnost **Spustit vše**.

    ![Test jednotek – &#45; základní test Průzkumníka testů byl úspěšný](../test/media/utecpp10.png)

   Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.

## <a name="iterate"></a>Iterativní rozšíření testů a jejich předání

1. Přidáte nový test:

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

2. Sestavte řešení a potom v **Průzkumníku testů**zvolte možnost **Spustit vše**.

     Nový test se nezdařil.

     ![RangeTest selže](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Ověřte, že každý test selže okamžitě poté, co jste ho napsali. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.

3. Vylepšete svůj kód DLL tak, aby nový test prošl:

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

4. Sestavte řešení a potom v **Průzkumníku testů**zvolte možnost **Spustit vše**.

     Oba testy jsou úspěšné.

     ![Test rozsahu Průzkumníka &#45; testů jednotek byl úspěšný](../test/media/utecpp12.png)

    > [!TIP]
    > Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.

## <a name="debug"></a>Ladění neúspěšného testu

1. Přidat další test:

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

2. Sestavte řešení a vyberte **Spustit vše**.

3. Otevřete (nebo dvakrát klikněte) na neúspěšný test.

     Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je zobrazena v podokně podrobností v **Průzkumníku testů**.

     ![NegativeRangeTests se nezdařilo](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Chcete-li zjistit, proč se test nezdaří, kroku pomocí funkce:

    1. Nastavte zarážku na začátku funkce SquareRoot.

    2. V místní nabídce neúspěšného testu vyberte možnost **ladit vybrané testy**.

         Při spuštění se zastaví na zarážce, krokovat kód.

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

6. Všechny testy jsou nyní úspěšné.

   ![Všechny testy byly úspěšné](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testu pomocí&#95;tlačítka&#45;![ustit parallelicon Small](../test/media/ute_parallelicon-small.png) přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní spuštění testů v nabídce nastavení na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.

::: moniker-end

## <a name="refactor"></a>Refaktoring kódu bez změny testů

1. Zjednodušení centrálního výpočtu ve funkci SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Sestavte řešení a vyberte **Spustit vše**, abyste se ujistili, že jste nepředstavili chybu.

    > [!TIP]
    > Dobrá sada testů jednotek poskytuje jistotu, že jste při změně kódu nepředstavili chyby.
    >
    > Zachovat refaktorování odděleně od jiných změn.

## <a name="next-steps"></a>Další kroky

- **Oddělení.** Většina knihoven DLL je závislá na jiných subsystémech, jako jsou databáze a jiné knihovny DLL. Tyto ostatní komponenty jsou často vyvíjeny paralelně. Aby bylo možné provádět testování jednotek i v případě, že ostatní komponenty ještě nejsou k dispozici, je nutné nahradit ho přípravou nebo

- **Ověřovací testy sestavení.** V nastavených intervalech můžete mít testy provedené na serveru sestavení vašeho týmu. Tím je zajištěno, že chyby nebudou zavedeny, když je integrována práce několika členů týmu.

- **Testy se změnami.** Můžete určit, že některé testy jsou provedeny předtím, než každý člen týmu zkontroluje kód do správy zdrojového kódu. Obvykle je to podmnožina kompletní sady ověřovacích testů sestavení.

   Můžete také pověřit minimální úroveň pokrytí kódu.

## <a name="see-also"></a>Viz také

- [Přidat testy částí do stávajících C++ aplikací](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Návod: vytvoření a použití dynamické knihovny DLL (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import a export](/cpp/build/importing-and-exporting)
