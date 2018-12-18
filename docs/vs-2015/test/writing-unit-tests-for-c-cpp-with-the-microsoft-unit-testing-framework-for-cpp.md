---
title: Zápis testů jednotek pro C / C++ pomocí Microsoft Unit Testing Framework pro C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: gewarren
manager: douge
ms.openlocfilehash: 180f970f35ed0bb3de70ba3a7b7b47dbe656ddf7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904037"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Zápis testů jednotek pro C/C++ s infrastrukturou testování částí Microsoft Unit Testing Framework pro C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete vytvořit testy jednotek pro nespravovaný kód napsaný v jazyce C++. Nespravovaného kódu se někdy označuje jako nativní kód.  
  
 Následující postup obsahuje základní informace, které se vám pomůžou začít. Další oddíly obsahují návod, který popisuje kroky, které podrobněji.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Pro psaní jednotkových testů pro nespravovaný kód knihovny DLL  
  
1.  Použití **nativní projekt testu** šablony k vytvoření samostatného projektu sady Visual Studio pro vaše testy.  
  
     Projekt obsahuje vzorový kód testu.  
  
2.  Zpřístupnění knihovny DLL pro testovací projekt:  
  
    -   `#include` `.h` soubor obsahující deklarace funkcí knihovny DLL externě dostupný.  
  
         `.h` Soubor by měl obsahovat deklarace funkce označené `_declspec(dllimport)`. Alternativně můžete exportovat metod pomocí souborů DEF. Další informace najdete v tématu [import a export](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).  
  
         Testování částí můžete přistupovat pouze funkce, které byly exportovány z knihovny DLL v rámci testu.  
  
    -   Přidejte projekt knihovny DLL do odkazů projektu testu:  
  
         V **vlastnosti** testovacího projektu, rozbalte **společné vlastnosti**, **rámec a odkazy**a zvolte **přidat odkaz**.  
  
3.  V testovacím projektu vytvořit třídy testu a testovací metody pomocí makra testu a kontrolní výraz třídy následujícím způsobem:  
  
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
  
    -   `Assert` obsahuje několik statické funkce, které můžete použít k ověření výsledku testu.  
  
    -   `LINE_INFO()` Parametr je nepovinný. V případech, pokud neexistuje žádný soubor PDB, je možné nástroj test runner pro určení umístění k chybě.  
  
    -   Můžete také napsat instalační a čistící metody testu. Další informace, otevřete definici `TEST_METHOD` – makro, a přečtěte si komentáře v CppUnitTest.h  
  
    -   Nelze vnořovat testovacích tříd.  
  
4.  Spuštění testů pomocí Průzkumníka testů:  
  
    1.  Na **zobrazení** nabídce zvolte **ostatní Windows**, **Průzkumník testů**.  
  
    2.  Sestavte řešení sady Visual Studio.  
  
    3.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
    4.  Chcete-li prozkoumat podrobněji v aplikaci Test Explorer jakýkoli test:  
  
        1.  Vyberte název testu, chcete-li zobrazit více podrobností, třeba selhání zpráv nebo trasování zásobníku.  
  
        2.  Otevřete název testu (například poklikáním) přejděte do umístění, selhání nebo testovací kód.  
  
        3.  V místní nabídce pro test, zvolte **ladit vybraný Test** pro spuštění testu v ladicím programu.  
  
##  <a name="walkthrough"></a> Návod: Vývoj nespravovaná knihovna DLL s použitím Průzkumníka testů  
 Můžete upravit tento návod pro vývoj vlastní knihovny DLL. Hlavní kroky jsou následující:  
  
1.  [Vytvořte projekt pro nativní Test](#unitTestProject). Testy jsou vytvořeny v samostatném projektu z knihovny DLL, které vyvíjíte.  
  
2.  [Vytvoření projektu knihovny DLL](#createDllProject). Tento návod vytvoří nová knihovna DLL, ale je podobný postup testování existující knihovny DLL.  
  
3.  [Zpřístupnění funkcí knihovny DLL pro testy](#coupleProjects).  
  
4.  [Využívejte iterativní posílit testy](#iterate). Doporučujeme, abyste cyklus "červená zelená Refaktorujte", ve kterém je vývoj kódu vedené testy.  
  
5.  [Ladit selhání testů](#debug). Testy můžete spustit v režimu ladění.  
  
6.  [Refaktoring při udržování testů beze změny](#refactor). Refaktoring zlepšení strukturu kódu beze změny jeho chování externí prostředky. Můžete to provést na zlepšení výkonu, rozšíření a čitelnost kódu. Protože záměrem nebudou je moci měnit chování, se nezmění testy při provedení refaktoringu změny kódu. Testy pomoct, ujistěte se, že když jsou refaktoring není způsobit chyby. Proto můžete provádět tyto změny s větší jistotou než pokud nemáte testy.  
  
7.  [Zkontrolujte pokrytí](https://msdn.microsoft.com/library/fc8hec9e.aspx). Testování jednotek je užitečnější, když využijí víc svého kódu. Je-li zjistit, které části kódu se používají testy.  
  
8.  [Izolace jednotky z externích zdrojů](https://msdn.microsoft.com/library/hh549174.aspx). Obvykle je závislé na dalších komponentách systému, kterou vyvíjíte, jako jsou jiné knihovny DLL, databáze nebo subsystémy vzdálené knihovny DLL. Je užitečné k testování jednotlivých jednotek v izolaci od jeho závislosti. Externí komponenty můžete provádět testy pomalý. Během vývoje nemusí být kompletní ostatní součásti.  
  
###  <a name="unitTestProject"></a> Vytvořte projekt testu jednotek native  
  
1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
     V dialogovém okně rozbalte **nainstalováno**, **šablony**, **Visual C++**, **Test**.  
  
     Zvolte **nativní projekt testu** šablony.  
  
     V tomto návodu je testovací projekt s názvem `NativeRooterTest`.  
  
     ![Vytváření C&#43; &#43; projekt testu jednotek](../test/media/utecpp01.png "UteCpp01")  
  
2.  V novém projektu, zkontrolujte **unittest1.cpp**  
  
     ![Testovací projekt s TESTEM&#95;třídy a testování&#95;metoda](../test/media/utecpp2.png "UteCpp2")  
  
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
  
    2.  Na **testovací** nabídce zvolte **spustit** , **všechny testy**.  
  
         Test vytvoří a spustí.  
  
         Otevře se Průzkumník testů.  
  
         Test je zobrazen **úspěšné testy**.  
  
         ![Průzkumník testů jednotek s jeden úspěšných testů](../test/media/utecpp04.png "UteCpp04")  
  
###  <a name="createDllProject"></a> Vytvoření projektu nespravovaná knihovna DLL  
  
1.  Vytvoření **Visual C++** projektu pomocí **projekt Win32** šablony.  
  
     V tomto názorném postupu má projekt název `RootFinder`.  
  
     ![Vytváření C&#43; &#43; projekt Win32](../test/media/utecpp05.png "UteCpp05")  
  
2.  Vyberte **DLL** a **symboly exportu** v Průvodci aplikací Win32.  
  
     **Exportovat symboly** možnost generuje pohodlný makro, které můžete použít k deklarování exportovaných metod.  
  
     ![C&#43; &#43; Průvodce projektu nastavit pro knihovny DLL a exportovat symboly](../test/media/utecpp06.png "UteCpp06")  
  
3.  Deklarujte exportované funkce v souboru .h instančního objektu:  
  
     ![Nový kód projektu a .h souboru DLL s makry API](../test/media/utecpp07.png "UteCpp07")  
  
     Deklarátor `__declspec(dllexport)` způsobí, že veřejné a chráněné členy třídy viditelný mimo knihovnu DLL. Další informace najdete v tématu [používání příkazů dllimport a dllexport ve třídách jazyka C++](http://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).  
  
4.  Soubor .cpp instančního objektu přidejte minimální tělo funkce:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
###  <a name="coupleProjects"></a> Několik testů projektu do projektu knihovny DLL  
  
1. Přidejte projekt knihovny DLL do odkazů projektu testovacího projektu:  
  
   1.  Otevřete vlastnosti projektu testu a zvolte **společné vlastnosti**, **rámec a odkazy**.  
  
        ![C&#43; &#43; vlastnosti projektu &#45; rámec a odkazy](../test/media/utecpp08.png "UteCpp08")  
  
   2.  Zvolte **přidat nový odkaz**.  
  
        V **přidat odkaz** dialogového okna, vyberte projekt knihovny DLL a vyberte **přidat**.  
  
        ![C&#43; &#43; vlastnosti projektu &#45; přidat nový odkaz](../test/media/utecpp09.png "UteCpp09")  
  
2. V souboru .cpp hlavní jednotkového testu zahrňte soubor .h kódu knihovny DLL:  
  
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
  
    Nový test se zobrazí v Průzkumníku testů.  
  
5. V Průzkumníku testů, zvolte **spustit všechny**.  
  
    ![Průzkumník testu jednotek &#45; základní Test prošel](../test/media/utecpp10.png "UteCpp10")  
  
   Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.  
  
###  <a name="iterate"></a> Využívejte iterativní posílit testy a daly se předat  
  
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
    >  Doporučujeme neměňte testy, které prošly. Místo toho přidat nový test, aktualizovat kód tak, aby byl test úspěšný a pak přidejte jiného testu, a tak dále.  
    >   
    >  Pokud uživatelé změní své požadavky, zakážete testy, které už nejsou správné. Psát nové testy a jejich fungování postupně, přírůstkové stejně.  
  
2.  Sestavte řešení a v Průzkumníku testů, zvolte **spustit všechny**.  
  
     Nový test se nezdaří.  
  
     ![Nezdaří RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Ověřte, že každý test selže okamžitě poté, co jste ho napsali. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.  
  
3.  Vylepšení testovaného kódu tak, aby byl nový test úspěšný:  
  
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
  
4.  Sestavte řešení a v Průzkumníku testů, zvolte **spustit všechny**.  
  
     Oba testy jsou úspěšné.  
  
     ![Průzkumník testu jednotek &#45; rozsah Test prošel](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    >  Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.  
  
###  <a name="debug"></a> Ladit test chybou  
  
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
  
     Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je viditelný v podokně podrobností Test Explorer.  
  
     ![NegativeRangeTests nepovedlo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
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
  
     ![Všechny testy byly úspěšné](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
>  Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute-parallelicon-small.png "UTE_parallelicon malé") přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.  
  
###  <a name="refactor"></a> Refaktorujte kód beze změn testů  
  
1.  Zjednodušení centrální výpočtu ve funkci SquareRoot:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2.  Sestavte řešení a zvolte **spustit všechny**, abyste měli jistotu, že nebyla zavedena chybu.  
  
    > [!TIP]
    >  Správnou sadu testů jednotek poskytuje jistotu, že nebyly zavedeny chyby při změně kódu.  
    >   
    >  Zachovat refaktorování odděleně od jiných změn.  
  
## <a name="next-steps"></a>Další kroky  
  
-   **Izolace.** Většinu knihoven DLL jsou závislé na ostatních subsystémů, jako jsou databáze a další knihovny DLL. Tyto součásti jsou často paralelně. Pokud chcete povolit testování, která se má provést, zatímco ostatní součásti ještě nejsou k dispozici, budete muset nahradit mock nebo  
  
-   **Ověřovací testy sestavení.** Můžete mít testy provést na serveru sestavení vašeho týmu v nastavených intervalech. Tím se zajistí, že chyby nejsou zavedena při integraci pracovní několik členů týmu.  
  
-   **Vrácení se změnami testy.** Můžete ukládat povinnost, aby některé testy byly provedeny před každý člen týmu vrátí kód do správy zdrojového kódu. To je obvykle podmnožinou všech ověřovacích testů sestavení.  
  
     Lze také ukládat povinnost minimální úrovně pokrytí kódu.  
  
## <a name="see-also"></a>Viz také  
 [Přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Přehled Interoperability spravovaného a nespravovaného kódu](http://msdn.microsoft.com/library/ms973872.aspx)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Návod: Vytvoření a použití dynamické knihovny (C++)](http://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941)   
 [Import a export](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)



