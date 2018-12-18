---
title: Testování jednotek kódu jazyka Visual C# v aplikaci Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: ae41a5a646860526cbc5b3f6e3c04bfbf7612e2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901551"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Testování jednotek kódu jazyka Visual C# v Store app
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje jeden ze způsobů vytvoření testů jednotek pro třídy Visual C# v aplikaci Windows Store. Třída Rooter ukazuje vágní paměti limit teorie z calculus implementací funkce, která vypočítá odhad odmocninu daného čísla. Matematické výrazy aplikace pak pomocí této funkce můžete zobrazit uživateli zábavných věcí, které lze provést s matematickým výrazem.  
  
 Toto téma ukazuje, jak používat jako první krok při vývoji testování částí. V takovém případě napíšete testovací metoda, která ověřuje konkrétní chování v systému, který testujete a potom napíšete kód, který projde testem. Tím, že změny v pořadí podle následujících postupů lze zrušit tuto strategii první zapisovat kód, který chcete otestovat a teprve pak píšete jednotkové testy.  
  
 V tomto tématu se vytvoří také jedno řešení sady Visual Studio a samostatné projekty pro testy jednotky a knihovny DLL, který chcete testovat. Můžete také zahrnout jednotkové testy přímo do projektu knihovny DLL, nebo můžete vytvořit samostatné řešení pro testování částí a knihovny DLL.  
  
> [!NOTE]
>  Visual Studio Community, Enterprise. a Professional nabízí další funkce pro testování částí.  
> 
> - Použijte libovolné rozhraní testování částí třetích stran a open source, který byl vytvořen adaptér doplněk pro aplikaci Microsoft Test Explorer. Můžete také analyzovat a zobrazit informace o pokrytí kódu pro testy.  
>   -   Spusťte testy po každém sestavení.  
>   -   VS Enterprise také obsahuje Microsoft Fakes, izolované rozhraní pro spravovaný kód, který vám umožní zaměřit testů na váš vlastní kód nahrazením testovací kód pro systém a funkce třetích stran.  
> 
>   Další informace najdete v tématu [ověřování kódu pomocí testování částí](http://msdn.microsoft.com/library/dd264975.aspx) v knihovně MSDN.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [Vytvoření řešení a projektu testování částí](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Ověřte, že testy spustit v Průzkumníku testů](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Přidat třídu Rooter matematické výrazy projektu](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Několik testů projektu do projektu aplikace](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Využívejte iterativní posílit testy a daly se předat](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Ladit test chybou](#BKMK_Debug_a_failing_test)  
  
 [Refaktorování kódu](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Vytvoření řešení a projektu testování částí  
  
1.  Na **souboru** nabídce zvolte **nový**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **nainstalováno**, potom rozbalte **Visual C#** a zvolte **Windows Store**. Klikněte na tlačítko **prázdnou aplikaci** ze seznamu šablon projektu.  
  
3.  Pojmenujte projekt `Maths` a ujistěte se, že **vytvořit adresář pro řešení** zaškrtnuto.  
  
4.  V Průzkumníku řešení vyberte název řešení a zvolte **přidat** z místní nabídky a klikněte na tlačítko **nový projekt**.  
  
5.  V **nový projekt** dialogového okna rozbalte **nainstalováno**, potom rozbalte **Visual C#** a zvolte **Windows Store** . Klikněte na tlačítko **testovací knihovna jednotky (aplikace pro Windows Store)** ze seznamu šablon projektu.  
  
     ![Vytvoření projektu testování částí](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")  
  
6.  Otevřete UnitTest1.cs v editoru sady Visual Studio.  
  
    ```csharp  
  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;  
    using Maths;  
  
    namespace RooterTests  
    {  
        [TestClass]  
        public class UnitTest1  
  
            [TestMethod]  
            public void TestMethod1()  
            {  
  
            }  
  
    ```  
  
     Všimněte si, že:  
  
    1.  Každý test se definuje pomocí `[TestMethod]`. Testovací metoda musí vracet typ void a nemůže mít žádné parametry.  
  
    2.  Testovací metody musí být ve třídě dekorován `[TestClass]` atribut.  
  
         Při spuštění testů, je vytvořena instance každé testovací třídy. Testovací metody jsou zavolány v nespecifikovaném pořadí.  
  
    3.  Můžete definovat speciální metody, které jsou vyvolány před a za každého modulu, třídy nebo metody. Další informace najdete v tématu [používání členů oboru názvů Microsoft.VisualStudio.TestTools.UnitTesting při testech jednotek](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) v knihovně MSDN.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Ověřte, že testy spustit v Průzkumníku testů  
  
1.  Vložit některé testovací kód ve `TestMethod1` z **UnitTest1.cs** souboru:  
  
    ```csharp  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Všimněte si, že `Assert` třída poskytuje několik statických metod, které slouží k ověření výsledků v testovacích metod.  
  
2.  Na **testovací** nabídce zvolte **spustit** a klikněte na tlačítko **spustit všechny**.  
  
     Testovací projekt vytvoří a spustí. Zobrazí se okno Průzkumníka testů a test je uvedený v části **úspěšné testy**. Souhrn v dolní části okna poskytuje další podrobnosti o vybraných testů.  
  
     ![Průzkumník testů](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Přidat třídu Rooter matematické výrazy projektu  
  
1.  V Průzkumníku řešení zvolte **matematické výrazy** název projektu. V místní nabídce zvolte **přidat**a potom **třídy**.  
  
2.  Název souboru třídy `Rooter.cs`  
  
3.  Přidejte následující kód do třídy Rooter **Rooter.cs** souboru:  
  
    ```csharp  
  
    public Rooter()  
    {  
    }  
  
    // estimate the square root of a number  
    public double SquareRoot(double x)  
    {  
        return 0.0;  
    }  
  
    ```  
  
     `Rooter` Třída deklaruje konstruktor a `SqareRoot` estimator metody.  
  
4.  `SqareRoot` Pouze minimální implementaci, je metoda právě takové, aby test základní struktura nastavení testování.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Několik testů projektu do projektu aplikace  
  
1. Přidáte odkaz na aplikaci matematické výrazy RooterTests projektu.  
  
   1.  V Průzkumníku řešení zvolte **RooterTests** projektu a klikněte na tlačítko **přidat odkaz...**  v místní nabídce.  
  
   2.  Na **přidat odkaz - RooterTests** dialogového okna rozbalte **řešení** a zvolte **projekty**. Vyberte **matematické výrazy** položky.  
  
        ![Přidat odkaz na projekt matematické výrazy](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")  
  
2. Přidat sadu pomocí příkazu soubor UnitTest1.cs:  
  
   1.  Otevřít **UnitTest1.cs**.  
  
   2.  Přidejte tento kód níže `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` řádku:  
  
       ```csharp  
       using Maths;  
       ```  
  
3. Přidáte test, který používá funkci Rooter. Přidejte následující kód, který **UnitTest1.cpp**:  
  
   ```csharp  
   [TestMethod]  
   public void BasicTest()  
   {  
       Maths.Rooter rooter = new Rooter();  
       double expected = 0.0;  
       double actual = rooter.SquareRoot(expected * expected);  
       double tolerance = .001;  
       Assert.AreEqual(expected, actual, tolerance);  
   }  
  
   ```  
  
4. Sestavte řešení.  
  
    Nový test se zobrazí v Průzkumníku testů v **nespuštěné testy** uzlu.  
  
5. V Průzkumníku testů, zvolte **spustit všechny**.  
  
    ![Základní Test prošel](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Máte nastavení testu a kódové projekty a ověřit, že je možné spustit testy, na kterých běží funkce v projektu kódu. Teď můžete začít psát skutečné testů a kódu.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Využívejte iterativní posílit testy a daly se předat  
  
1.  Přidáte nový test:  
  
    ```csharp  
    [TestMethod]  
    public void RangeTest()  
    {  
        Rooter rooter = new Rooter();  
        for (double v = 1e-6; v < 1e6; v = v * 3.2)  
        {  
            double expected = v;  
            double actual = rooter.SquareRoot(v*v);  
            double tolerance = ToleranceHelper(expected);  
            Assert.AreEqual(expected, actual, tolerance);  
        }  
    }  
  
    ```  
  
    > [!TIP]
    >  Doporučujeme neměňte testy, které prošly. Místo toho přidat nový test, aktualizovat kód tak, aby byl test úspěšný a pak přidejte jiného testu, a tak dále.  
    >   
    >  Pokud uživatelé změní své požadavky, zakážete testy, které už nejsou správné. Psát nové testy a jejich fungování postupně, přírůstkové stejně.  
  
2.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
3.  Test se nezdaří.  
  
     ![Nezdaří RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Ihned poté, co jste ho napsali, ověřte, že každý test se nezdaří. To umožňuje vyhnout se snadno chybu zápisu test, který se nikdy selže.  
  
4.  Vylepšete testovaného kódu tak, aby nový test byl úspěšný. Změnit `SqareRoot` fungovat v **Rooter.cs** tomuto:  
  
    ```csharp  
    public double SquareRoot(double x)  
    {  
        double estimate = x;  
        double diff = x;  
        while (diff > estimate / 1000)  
        {  
            double previousEstimate = estimate;  
            estimate = estimate - (estimate * estimate - x) / (2 * estimate);  
            diff = Math.Abs(previousEstimate - estimate);  
        }  
        return estimate;  
    }  
  
    ```  
  
5.  Sestavte řešení a v Průzkumníku testů, zvolte **spustit všechny**.  
  
     Všechny tři testy jsou nyní úspěšné.  
  
> [!TIP]
>  Vývoj kódu tak, že přidáte testy jeden po druhém. Ujistěte se, že všechny testy jsou úspěšné po každé iteraci.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Ladit test chybou  
  
1. Přidat jiného testu k **UnitTest1.cs**:  
  
   ```csharp  
   // Verify that negative inputs throw an exception.  
   [TestMethod]  
   public void NegativeRangeTest()  
   {  
       string message;  
       Rooter rooter = new Rooter();  
       for (double v = -0.1; v > -3.0; v = v - 0.5)  
       {  
           try  
           {  
               // Should raise an exception:  
               double actual = rooter.SquareRoot(v);  
  
               message = String.Format("No exception for input {0}", v);  
               Assert.Fail(message);  
           }  
           catch (ArgumentOutOfRangeException ex)  
           {  
               continue; // Correct exception.  
           }  
           catch (Exception e)  
           {  
               message = String.Format("Incorrect exception for {0}", v);  
               Assert.Fail(message);  
           }  
       }  
   }  
  
   ```  
  
2. V Průzkumníku testů, zvolte **spustit všechny**.  
  
    Test se nezdaří. Zvolte název testu v aplikaci Test Explorer. Neplatnost kontrolního výrazu je zvýrazněn. Zpráva o selhání je viditelný v podokně podrobností Test Explorer.  
  
    ![NegativeRangeTests nepovedlo](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Chcete-li zjistit, proč se test nezdaří, kroku pomocí funkce:  
  
   1.  Nastavit zarážku na začátku `SquareRoot` funkce.  
  
   2.  V místní nabídce neúspěšných testů, zvolte **ladit vybrané testy**.  
  
        Při spuštění se zastaví na zarážce, krokovat kód.  
  
   3.  Přidejte kód do metody Rooter pro zachycení výjimky:  
  
       ```csharp  
       public double SquareRoot(double x)  
       {  
           if (x < 0.0)  
           {  
               throw new ArgumentOutOfRangeException();  
       }  
  
       ```  
  
   1.  V Průzkumníku testů zvolte **spustit všechny** testovací metoda opravené a ujistěte se, že nebyla zavedena regrese.  
  
   Všechny testy jsou nyní úspěšné.  
  
   ![Všechny testy byly úspěšné](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Refaktorování kódu  
 **Zjednodušení centrální výpočtu ve funkci SquareRoot.**  
  
1.  Změňte implementaci výsledek  
  
    ```csharp  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Zvolte **spustit všechny** testovací metoda refaktorovaný a ujistěte se, že nebyla zavedena regrese.  
  
> [!TIP]
>  Se spouští stabilní sada testů jednotek dobré poskytuje jistotu, že nebyly zavedeny chyby při změně kódu.  
  
 **Testovací kód Refaktorujte k vyloučení duplicitním kódem.**  
  
 Všimněte si, že `RangeTest` metoda pevné kódů jmenovatel proměnnou proti chybám, který se používá v `Assert` metody. Pokud budete chtít přidat další testy, které používají stejný výpočet proti chybám, použijte hodnotu pevně zakódované v několika umístěních může vést k chybám.  
  
1.  Přidejte privátní metodu do třídy Unit1Test pro výpočet hodnoty proti chybám a místo toho volejte tuto metodu.  
  
    ```csharp  
    private double ToleranceHelper(double expected)  
    {  
        return expected / 1000;  
    }  
  
    ...  
  
    [TestMethod]  
    public void RangeTest()  
    {  
        ...  
        // old code  
        // double tolerance = expected/1000;  
        // new code  
        double tolerance = ToleranceHelper(expected);  
        Assert.AreEqual(expected, actual, tolerance);  
    }  
    ...  
  
    ```  
  
2.  Zvolte **spustit všechny** testovací metoda refaktorovaný a ujistěte se, že nebyla zavedena chybu.  
  
> [!NOTE]
>  Pokud chcete přidat do testovací třídy Pomocná metoda, nepřidávejte `[TestMethod]` atribut do metody. Průzkumník testů nezaregistruje metodu ke spuštění.



