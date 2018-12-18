---
title: 'Rychlý Start: Testovací vývoj řízený testy s použitím Průzkumníka testů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: 17
ms.author: gewarren
manager: douge
ms.openlocfilehash: a67f4f79688cb4cdbe482c90cd93b784349d748a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831689"
---
# <a name="quick-start-test-driven-development-with-test-explorer"></a>Rychlý začátek: Vývoj řízený testy s použitím Průzkumníka testů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Doporučujeme vytvořit jednotkové testy zajistit, aby byl váš kód správně funguje napříč mnoha inkrementálními kroky vývoje. Existuje několik architektur, které můžete použít pro psaní jednotkových testů, včetně některých vyvinutých třetími stranami. Některá testovací rozhraní jsou zaměřena na testování v jiných jazycích či platformách. Průzkumník testů poskytuje tak jednotné rozhraní pro testování částí v některém z těchto rozhraní. Adaptéry jsou k dispozici pro nejčastěji používaná rozhraní a můžete napsat vlastní adaptér pro jiná rozhraní.  
  
 Průzkumník testů nahrazuje okna jednotkových testů starších vydání sady Visual Studio. Mezi její výhody patří:  
  
-   Spustit .NET, nespravovaných, databázových a jiných testů pomocí jednoho rozhraní.  
  
-   Použití jednotky testovacího rozhraní dle vlastního výběru, jako je například NUnit nebo rozhraní MSTest.  
  
-   Zobrazit v jednom okně všechny informace, které potřebujete.  
  
## <a name="using-test-explorer"></a>Pomocí Průzkumníka testů  
 ![Spustit všechny tlačítko zobrazuje Průzkumník testů jednotek](../test/media/unittestexplorer-beta.png "UnitTestExplorer(beta)")  
  
#### <a name="to-run-unit-tests-by-using-test-explorer"></a>Spouštění jednotkových testů pomocí Průzkumníku testů  
  
1. Vytvořte jednotkové testy používající vybrané testovací rozhraní podle vlastního výběru.  
  
    Například vytvořit test používající rozhraní MSTest:  
  
   1.  Vytvoření testovacího projektu.  
  
        V **nový projekt** dialogového okna rozbalte **jazyka Visual Basic**, **Visual C#**, nebo **Visual C++** a klikněte na tlačítko **Test**.  
  
        Vyberte **projekt testu jednotek**.  
  
   2.  Zapište každý Jednotkový test jako metodu. Předpona každou metodu testu `[TestMethod]` atribut.  
  
2. Je-li jednotlivé testy nemají žádné závislosti, které brání spuštění v libovolném pořadí, zapněte paralelní provádění testů s ![USTIT&#95;parallelicon&#45;malé](../test/media/ute-parallelicon-small.png "UTE_parallelicon malé") přepínací tlačítko na panelu nástrojů. To může výrazně snížit čas potřebný ke spuštění všech testů.  
  
3. V panelu nabídky zvolte **testovací**, **spustit jednotkové testy**, **všechny testy**.  
  
    Řešení je sestaveno a testy spuštěny.  
  
    Průzkumník testů otevře a zobrazí souhrn výsledků.  
  
   **Pokud chcete zobrazit úplný seznam testů:** zvolit **Zobrazit vše** v každé kategorii.  
  
   **Pokud chcete zobrazit podrobnosti výsledku testu:** vyberte test v Průzkumníku testů, chcete-li zobrazit podrobnosti, jako jsou zprávy o výjimkách v podokně podrobností.  
  
   **Přejít na kód testu:** klikněte dvakrát na test v Průzkumníku testů nebo zvolte **otevřít Test** v místní nabídce.  
  
   **Ladění testu:** otevřete místní nabídku pro jeden nebo více testů a klikněte na tlačítko **ladit vybrané testy**.  
  
> [!IMPORTANT]
>  Výsledky, které se zobrazují se poslední spuštění. Obarvený panel výsledků zobrazuje pouze výsledky testů, které byly spuštěny. Například pokud spuštění více testů a některé z nich selhání a poté spustíte pouze úspěšné testy, pak na panelu výsledků bude celý zelený.  
  
> [!NOTE]
>  Je-li zobrazen žádný test, ujistěte se, že máte nainstalován adaptér pro připojení Průzkumníku testů pro testovací rozhraní, kterou používáte. Další informace najdete v tématu [použití různých testovacích rozhraní s Průzkumníkem testů](#frameworks).  
  
##  <a name="walkthrough"></a> Návod: Použití jednotkových testů pro vývoj metody  
 Tento návod ukazuje, jak vyvinout testovanou metodu v jazyce C# pomocí rozhraní Microsoft Unit Test framework. Můžete snadno přizpůsobit ho pro ostatní jazyky a použití jiných testovacích architektur, jako je například NUnit. Další informace najdete v tématu [použití různých testovacích rozhraní](#frameworks).  
  
#### <a name="creating-the-test-and-method"></a>Vytvoření testu a – metoda  
  
1. Vytvořte projekt knihovny tříd Visual C#. Tento projekt bude obsahovat kód, který chceme dodat. V tomto příkladu je pojmenována `MyMath`.  
  
2. Vytvoření testovacího projektu.  
  
   -   V **nový projekt** dialogovém okně zvolte **Visual C#**, **testovací** a klikněte na tlačítko **projekt testu jednotek**.  
  
        ![Nové projekty kódu a testování](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")  
  
3. Napište základní testovací metodu. Ověřte výsledek pro určitý vstup:  
  
   ```csharp  
  
   [TestMethod]  
   public void BasicRooterTest()  
   {  
     // Create an instance to test:  
     Rooter rooter = new Rooter();  
     // Define a test input and output value:  
     double expectedResult = 2.0;  
     double input = expectedResult * expectedResult;  
     // Run the method under test:  
     double actualResult = rooter.SquareRoot(input);  
     // Verify the result:  
     Assert.AreEqual(expectedResult, actualResult,  
         delta: expectedResult / 100);  
   }  
   ```  
  
4. Generovat metodu testu.  
  
   1.  Umístěte kurzor na `Rooter`a pak v místní nabídce zvolte **generovat**, **nový typ**.  
  
   2.  V **generovat nový typ** dialogové okno, nastavte **projektu** do projektu knihovny tříd. V tomto příkladu je `MyMath`.  
  
   3.  Umístěte kurzor na `SquareRoot`a pak v místní nabídce zvolte **generovat**, **Pahýl metody**.  
  
5. Spusťte Jednotkový test.  
  
   1.  Na **testovací** nabídce zvolte **spustit jednotkové testy**, **všechny testy**.  
  
        Toto řešení je sestaveno a spuštěno.  
  
        Průzkumník testů otevře a zobrazí výsledky.  
  
        Test je zobrazen **neúspěšné testy**.  
  
6. Vyberte název testu.  
  
    Podrobnosti testu se zobrazí v dolní části Průzkumníku testů.  
  
7. Vyberte položky v oblasti **trasování zásobníku** zobrazíte, pokud se test nezdařil.  
  
   ![Testování jednotek Test Explorer zobrazující se nezdařilo. ](../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")  
  
   V tomto okamžiku jste vytvořili test a prázdnou metodu, kterou upravíte tak, aby byl test úspěšný.  
  
#### <a name="after-every-change-make-all-the-tests-pass"></a>Po každé změně Ujistěte se, všechny testy úspěšné.  
  
1.  V `MyMath\Rooter.cs`, Vylepšete kód `SquareRoot`:  
  
    ```csharp  
    public double SquareRoot(double input)  
     {  
       return input / 2;  
     }  
    ```  
  
2.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
     Kód sestavení a spuštění testu.  
  
     Test byl úspěšný.  
  
     ![Průzkumník testů jednotek zobrazující prochází testem. ](../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")  
  
#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Přidat testy do Rozšiřte rozsah vstupů  
  
1.  Pokud chcete zlepšit si být jistější, který váš kód funguje ve všech případech, přidejte testy, které zkoušejí širší rozsah vstupních hodnot.  
  
    > [!TIP]
    >  Neupravujte existující testy, které předávají. Místo toho přidejte nové testy. Existující testy měňte pouze v případě, že se změní požadavky uživatele. Tato zásada umožňuje zajistit, aby neztratili stávajících funkcí během rozšiřování kódu.  
  
     V testovací třídě přidejte následující test, který zkouší rozsah vstupních hodnot:  
  
    ```csharp  
    [TestMethod]  
    public void RooterValueRange()  
    {  
      // Create an instance to test:  
      Rooter rooter = new Rooter();  
      // Try a range of values:  
      for (double expectedResult = 1e-8;  
          expectedResult < 1e+8;  
          expectedResult = expectedResult * 3.2)  
      {  
        RooterOneValue(rooter, expectedResult);  
      }  
    }  
  
    private void RooterOneValue(Rooter rooter, double expectedResult)  
    {  
      double input = expectedResult * expectedResult;  
      double actualResult = rooter.SquareRoot(input);  
      Assert.AreEqual(expectedResult, actualResult,  
          delta: expectedResult / 1000);  
    }  
    ```  
  
2.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
     Nový test se nezdaří, i když se první test stále úspěšný.  
  
     K hledání bodu selhání, zvolte test obsahující a potom v dolní části Průzkumníku testů vyberte položku nejvýše **trasování zásobníku**.  
  
3.  Zkontrolujte, zda chcete zobrazit, co mohlo způsobit chybu testované metody. V `MyMath.Rooter` třídy, revize kódu:  
  
    ```  
    public double SquareRoot(double input)  
    {  
      double result = input;  
      double previousResult = -input;  
      while (Math.Abs(previousResult - result) > result / 1000)  
      {  
        previousResult = result;  
        result = result - (result * result - input) / (2 * result);  
      }  
      return result;  
    }  
    ```  
  
4.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
     Oba testy jsou nyní úspěšné.  
  
#### <a name="add-tests-for-exceptional-cases"></a>Přidejte testy výjimečných případů  
  
1.  Přidejte test záporných vstupů:  
  
    ```csharp  
    [TestMethod]  
     public void RooterTestNegativeInputx()  
     {  
         Rooter rooter = new Rooter();  
         try  
         {  
             rooter.SquareRoot(-10);  
         }  
         catch (ArgumentOutOfRangeException e)  
         {  
             return;  
         }  
         Assert.Fail();  
     }  
    ```  
  
2.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
     Metoda v rámci testu smyčky a musí být ukončena ručně.  
  
3.  Zvolte **zrušit**.  
  
     Test se ukončí po 10 sekundách.  
  
4.  Opravte kód metody:  
  
    ```csharp  
  
    public double SquareRoot(double input)  
    {  
      if (input <= 0.0)   
      {  
        throw new ArgumentOutOfRangeException();  
      }   
    ...  
    ```  
  
5.  V Průzkumníku testů, zvolte **spustit všechny**.  
  
     Všechny testy jsou úspěšné.  
  
#### <a name="refactor-without-changing-tests"></a>Refaktorujte beze změn testů  
  
1.  Zjednodušte kód, ale neměňte testy.  
  
    > [!TIP]
    >  A *refaktoring* je změna, která slouží k provádění kódu líp fungovat nebo k srozumitelnější kód. Refaktorování není zamýšleno změnit chování kódu, a proto testy zůstávají nezměněny.  
    >   
    >  Doporučujeme provádět kroky refaktorování odděleně od kroků rozšiřujících funkčnost. Udržování testů v nezměněné podobě zajišťuje, že jste ještě kódu omylem zavedeny chyby během refaktoringu.  
  
    ```csharp  
    public class Rooter  
    {  
      public double SquareRoot(double input)  
      {  
        if (input <= 0.0)   
        {  
          throw new ArgumentOutOfRangeException();  
        }  
        double result = input;  
        double previousResult = -input;  
        while (Math.Abs(previousResult - result) > result / 1000)  
        {  
          previousResult = result;  
          result = (result + input / result) / 2;  
          //was: result = result - (result * result - input) / (2*result);  
        }  
        return result;  
      }  
    }  
    ```  
  
2.  Zvolte **spustit všechny**.  
  
     Všechny testy jsou stále úspěšné.  
  
     ![Úspěšné testy 3 zobrazuje Průzkumník testu jednotek. ](../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")



