---
title: Zápis testů částí pro C-C + + s rozhraním Microsoft Unit Testing Framework for C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b6f358f43dcace230e1d58773e58be011d9033e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657081"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Zápis testů jednotek pro C/C++ s infrastrukturou testování částí Microsoft Unit Testing Framework pro C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete vytvořit testy jednotek pro nespravovaný kód napsaný v jazyce C++. Nespravovaný kód se někdy označuje jako nativní kód.

 Následující postup obsahuje základní informace, které vám pomohou začít. V dalších částech najdete návod, který popisuje kroky podrobněji.

### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Zápis testů jednotek pro knihovnu DLL nespravovaného kódu

1. Použijte šablonu **nativního testovacího projektu** k vytvoření samostatného projektu sady Visual Studio pro vaše testy.

     Projekt obsahuje ukázkový testovací kód.

2. Zpřístupněte knihovnu DLL pro projekt testů:

    - `#include``.h`soubor, který obsahuje deklarace externě přístupných funkcí knihovny DLL.

         `.h`Soubor by měl obsahovat deklarace funkcí označené `_declspec(dllimport)` . Alternativně můžete metody exportovat pomocí DEF souboru. Další informace najdete v tématu [Import a export](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).

         Testy jednotek mají přístup pouze k funkcím, které jsou exportovány z knihovny DLL v rámci testu.

    - Přidejte projekt knihovny DLL do odkazů testovacího projektu:

         Ve **vlastnostech** testovacího projektu rozbalte položku **společné vlastnosti**, **architekturu a odkazy**a vyberte možnost **Přidat odkaz**.

3. V testovacím projektu vytvořte testovací třídy a testovací metody pomocí těchto TESTOVACÍch maker a třídy Assert následujícím způsobem:

    ```cpp
    #include "stdafx.h"
    #include <CppUnitTest.h>
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    TEST_CLASS(TestClassName)
    {
    public:
      TEST_METHOD(TestMethodName)
      {
        // Run a function under test here.
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());
      }
    }
    ```

    - `Assert` obsahuje několik statických funkcí, které lze použít k ověření výsledku testu.

    - `LINE_INFO()`Parametr je nepovinný. V případech, kdy není k dispozici žádný soubor PDB, umožňuje nástroji Test Runner identifikovat umístění selhání.

    - Můžete také napsat nastavení testu a metody vyčištění. Chcete-li získat další informace, otevřete definici `TEST_METHOD` makra a přečtěte si komentáře v CppUnitTest. h.

    - Nemůžete vnořovat testovací třídy.

4. Pomocí Průzkumníka testů spusťte testy:

    1. V nabídce **zobrazení** vyberte možnost **ostatní okna**, **Průzkumník testů**.

    2. Sestavte řešení sady Visual Studio.

    3. V Průzkumníku testů vyberte možnost **Spustit vše**.

    4. Chcete-li prozkoumat jakýkoliv test podrobněji v Průzkumníku testů:

        1. Vyberte název testu, chcete-li zobrazit více podrobností, jako je například zpráva o selhání a trasování zásobníku.

        2. Otevřete název testu (například dvojitým kliknutím), abyste přešli do umístění selhání nebo do testovacího kódu.

        3. V místní nabídce testu vyberte možnost **ladit vybraný test** a spusťte test v ladicím programu.

## <a name="walkthrough-developing-an-unmanaged-dll-with-test-explorer"></a><a name="walkthrough"></a> Návod: Vývoj nespravované knihovny DLL pomocí Průzkumníka testů
 Tento návod můžete přizpůsobit pro vývoj vlastní knihovny DLL. Hlavní kroky jsou následující:

1. [Vytvořte nativní testovací projekt](#unitTestProject). Testy jsou vytvořeny v samostatném projektu z knihovny DLL, kterou vyvíjíte.

2. [Vytvořte projekt knihovny DLL](#createDllProject). Tento návod vytvoří novou knihovnu DLL, ale procedura pro testování existující knihovny DLL je podobná.

3. [Zpřístupněte funkce knihovny DLL pro testy](#coupleProjects).

4. Provede [iterativní rozšíření testů](#iterate). Doporučujeme cyklus "Red-zelená-refaktor", ve kterém se vývoj kódu vede pomocí testů.

5. [Ladění neúspěšných testů](#debug). Testy můžete spouštět v režimu ladění.

6. [Refaktorujte a zachová testy beze změny](#refactor). Refaktoring znamená vylepšení struktury kódu beze změny jeho vnějšího chování. Můžete to udělat ke zlepšení výkonu, rozšiřitelnosti nebo čitelnosti kódu. Vzhledem k tomu, že záměr nemění chování, testy neměníte při provádění změn v kódu v refaktoringu. Testy vám pomohou zajistit, aby při refaktoringu nedošlo k chybám. Proto je možné provádět tyto změny s větší jistotou, než kdyby jste testy provedli.

7. [Podívejte](https://msdn.microsoft.com/library/fc8hec9e.aspx)se na pokrytí. Testy jednotek jsou užitečnější při cvičení více kódu. Můžete zjistit, které části kódu byly používány testy.

8. [Izolujte jednotky od externích prostředků](https://msdn.microsoft.com/library/hh549174.aspx). Obvykle je knihovna DLL závislá na dalších součástech systému, které vyvíjíte, například jiných knihoven DLL, databází nebo vzdálených subsystémů. Je vhodné testovat každou jednotku v izolaci z jejích závislostí. Externí komponenty můžou testy běžet pomalu. Během vývoje nemusí být ostatní součásti dokončeny.

### <a name="create-a-native-unit-test-project"></a><a name="unitTestProject"></a> Vytvořit nativní projekt testu jednotek

1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

     V dialogovém okně rozbalte položku **nainstalováno**, **šablony**, **Visual C++**, **test**.

     Vyberte šablonu **projektu nativního testu** .

     V tomto návodu se projekt testu jmenuje `NativeRooterTest` .

     ![Vytvoření projektu testu jednotek&#43;&#43; C](../test/media/utecpp01.png "UteCpp01")

2. V novém projektu zkontrolujte **UnitTest1. cpp.**

     ![Testovací projekt s TESTOVACÍm&#95;TŘÍDou a TESTOVACÍm&#95;metodou](../test/media/utecpp2.png "UteCpp2")

     Všimněte si, že:

    - Každý test je definován pomocí `TEST_METHOD(YourTestName){...}` .

         Nemusíte psát konvenční signaturu funkce. Podpis je vytvořen TEST_METHOD makra. Makro vygeneruje funkci instance, která vrací typ void. Také generuje statickou funkci, která vrací informace o testovací metodě. Tyto informace umožňují Průzkumníku testů najít metodu.

    - Testovací metody jsou seskupeny do tříd pomocí `TEST_CLASS(YourClassName){...}` .

         Při spuštění testů je vytvořena instance každé testovací třídy. Testovací metody jsou volány v nespecifikovaném pořadí. Můžete definovat speciální metody, které jsou vyvolány před a za každým modulem, třídou nebo metodou.

3. Ověřte, zda jsou testy spuštěny v Průzkumníku testů:

    1. Vložte nějaký kód testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
        Assert::AreEqual(1,1);
        }
        ```

         Všimněte si, že `Assert` Třída poskytuje několik statických metod, které lze použít k ověření výsledků v testovacích metodách.

    2. V nabídce **test** vyberte možnost **Spustit** , **všechny testy**.

         Test se vytvoří a spustí.

         Zobrazí se Průzkumník testů.

         Test se zobrazí v části **prošlé testy**.

         ![Průzkumník testů jednotek s jedním úspěšným testem](../test/media/utecpp04.png "UteCpp04")

### <a name="create-an-unmanaged-dll-project"></a><a name="createDllProject"></a> Vytvořit projekt nespravované knihovny DLL

1. Vytvořte **Visual C++** projekt pomocí šablony **projektu Win32** .

     V tomto návodu se projekt jmenuje `RootFinder` .

     ![Vytvoření projektu v jazyce C&#43;&#43; Win32](../test/media/utecpp05.png "UteCpp05")

2. V Průvodci aplikací Win32 vyberte **DLL** a **exportujte symboly** .

     Možnost **exportovat symboly** generuje pohodlné makro, které lze použít k deklaraci exportovaných metod.

     ![Průvodce projektem v jazyce C&#43;&#43; nastaven pro knihovnu DLL a export symbolů](../test/media/utecpp06.png "UteCpp06")

3. Deklarujte exportovanou funkci v souboru Principal. h:

     ![Nový projekt kódu knihovny DLL a soubor. h s makry rozhraní API](../test/media/utecpp07.png "UteCpp07")

     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy budou viditelné vně knihovny DLL. Další informace naleznete v tématu [použití dllimport a dllexport ve třídách jazyka C++](https://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).

4. Do souboru Principal. cpp přidejte minimální text pro funkci:

    ```cpp
    // Find the square root of a number.
    double CRootFinder::SquareRoot(double v)
    {
      return 0.0;
    }
    ```

### <a name="couple-the-test-project-to-the-dll-project"></a><a name="coupleProjects"></a> Spojit projekt testů s projektem knihovny DLL

1. Přidejte projekt knihovny DLL do odkazů projektu testovacího projektu:

   1. Otevřete vlastnosti testovacího projektu a vyberte možnost **společné vlastnosti**, **rozhraní a odkazy**.

        ![C&#43;&#43; vlastnosti projektu &#45; Framework a odkazy](../test/media/utecpp08.png "UteCpp08")

   2. Vyberte možnost **Přidat nový odkaz**.

        V dialogovém okně **Přidat odkaz** vyberte projekt knihovny DLL a zvolte možnost **Přidat**.

        ![Vlastnosti projektu v jazyce C&#43;&#43; &#45; přidat nový odkaz](../test/media/utecpp09.png "UteCpp09")

2. V souboru hlavní jednotky test. cpp zahrňte soubor. h kódu DLL:

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

    Nový test se zobrazí v Průzkumníku testů.

5. V Průzkumníku testů vyberte možnost **Spustit vše**.

    ![Průzkumník testů jednotek &#45; základní test byl úspěšný](../test/media/utecpp10.png "UteCpp10")

   Nastavili jste test a projekty kódu a ověřili jste, že můžete spouštět testy, které spouštějí funkce v projektu kódu. Nyní můžete začít psát skutečné testy a kód.

### <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Iterativní rozšíření testů a jejich předání

1. Přidat nový test:

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
    > Doporučujeme neměnit testy, které byly úspěšné. Místo toho přidejte nový test, aktualizujte kód tak, aby byl test úspěšný, a poté přidejte další test atd.
    >
    >  Když uživatelé změní své požadavky, zakažte testy, které už nejsou správné. Zapište nové testy a zpřístupněte je po jednom, a to stejným přírůstkovým způsobem.

2. Sestavte řešení a potom v Průzkumníku testů zvolte možnost **Spustit vše**.

     Nový test se nezdařil.

     ![RangeTest se nezdařila](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Ověřte, že se každý test nezdařil okamžitě po jeho zápisu. To pomáhá vyhnout se jednoduchému omylu při psaní testu, který se nikdy nezdařil.

3. Zvyšte testovaný kód, aby nový test prošl:

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

4. Sestavte řešení a potom v Průzkumníku testů zvolte možnost **Spustit vše**.

     Oba testy proběhnou.

     ![Průzkumník testů jednotek &#45; test rozsahu úspěšný](../test/media/utecpp12.png "UteCpp12")

    > [!TIP]
    > Vývoj kódu přidáním testů po jednom. Ujistěte se, že všechny testy proběhnou po každé iteraci.

### <a name="debug-a-failing-test"></a><a name="debug"></a> Ladění neúspěšného testu

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

     Kontrolní výraz neúspěšného zpracování je zvýrazněný. Zpráva o selhání je zobrazena v podokně podrobností v Průzkumníku testů.

     ![NegativeRangeTests se nezdařilo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

4. Chcete-li zjistit, proč se test nezdařil, postupujte podle této funkce:

    1. Nastavte zarážku na začátku funkce SquareRoot.

    2. V místní nabídce neúspěšného testu vyberte možnost **ladit vybrané testy**.

         Když se běh zastaví na zarážce, krokovat kód.

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

6. Všechny testy jsou nyní passované.

     ![Všechny testy Pass](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

> [!TIP]
> Pokud jednotlivé testy neobsahují žádné závislosti, které jim brání v jejich spuštění v libovolném pořadí, zapněte paralelní provádění testů pomocí tlačítka ![ustit&#95;parallelicon&#45;malého](../test/media/ute-parallelicon-small.png "UTE_parallelicon – malý") přepínacího tlačítka na panelu nástrojů. To může výrazně zkrátit čas potřebný ke spuštění všech testů.

### <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Refaktoring kódu bez změny testů

1. Zjednodušení centrálního výpočtu ve funkci SquareRoot:

    ```
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Sestavte řešení a vyberte **Spustit vše**, abyste se ujistili, že jste nepředstavili chybu.

    > [!TIP]
    > Dobrá sada testů jednotek poskytuje jistotu, že jste při změně kódu nepředstavili chyby.
    >
    >  Udržujte refaktoring odděleně od jiných změn.

## <a name="next-steps"></a>Další kroky

- **Oddělení.** Většina knihoven DLL je závislá na jiných subsystémech, jako jsou databáze a jiné knihovny DLL. Tyto ostatní komponenty jsou často vyvíjeny paralelně. Aby bylo možné provádět testování jednotek i v případě, že ostatní komponenty ještě nejsou k dispozici, je nutné nahradit ho přípravou nebo

- **Ověřovací testy sestavení.** V nastavených intervalech můžete mít testy provedené na serveru sestavení vašeho týmu. Tím je zajištěno, že chyby nebudou zavedeny, když je integrována práce několika členů týmu.

- **Testy se změnami.** Můžete určit, že některé testy jsou provedeny předtím, než každý člen týmu zkontroluje kód do správy zdrojového kódu. Obvykle je to podmnožina kompletní sady ověřovacích testů sestavení.

     Můžete také pověřit minimální úroveň pokrytí kódu.

## <a name="see-also"></a>Viz také
 [Přidání jednotkových testů do existujících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) [pomocí Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) [Přehled přehledu o spolupráci spravovaného/nespravovaného kódu](https://msdn.microsoft.com/library/ms973872.aspx) [Debugging Native Code](../debugger/debugging-native-code.md) [: vytvoření a použití dynamické knihovny (C++)](https://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941) [Import a export](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)
