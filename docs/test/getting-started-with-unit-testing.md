---
title: Začínáme s testováním jednotek
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d961af66658d6924da1b5ba38b9ec7f2a8b19aaa
ms.sourcegitcommit: c3b6af7367bef67a02c37404534229b935f713a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80892788"
---
# <a name="get-started-with-unit-testing"></a>Začínáme s testováním jednotek

Pomocí sady Visual Studio můžete definovat a spouštět testy částí k udržování stavu kódu, zajištění pokrytí kódu a hledání chyb a chyb dříve než vaši zákazníci. Spouštějte testy částí často a ujistěte se, že váš kód funguje správně.

## <a name="create-unit-tests"></a>Create unit tests
(Vytvořit testy jednotek)

Tato část popisuje, jak vytvořit projekt testování částí.

1. Otevřete projekt, který chcete otestovat v sadě Visual Studio.

   Pro účely demonstrování ukázkový test částí tento článek testuje jednoduchý projekt "Hello World" s názvem **HelloWorldCore**. Ukázkový kód pro takový projekt je následující:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. V **Průzkumníku řešení**vyberte uzel řešení. Potom v horním řádku nabídek vyberte Přidat nový**Add** > **projekt** **.** > 

1. V dialogovém okně nový projekt vyhledejte šablonu projektu testování částí pro testovací rámec, který chcete použít, a vyberte ji.

   ::: moniker range=">=vs-2019"

   ![Šablona projektu testování částí v Sadě Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Klepněte na tlačítko **Další**, zvolte název testovacího projektu a klepněte na tlačítko **Vytvořit**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Šablona projektu testování částí v Sadě Visual Studio 2019](media/mstest-test-project-template.png)

   Zvolte název testovacího projektu a klepněte na tlačítko **OK**.

   ::: moniker-end

   Projekt je přidán do vašeho řešení.

   ![Projekt testování částí v Průzkumníku řešení](media/vs-2019/solution-explorer.png)

1. V projektu testování částí přidejte odkaz na projekt, který chcete testovat, kliknutím pravým tlačítkem myši na **odkazy** nebo **závislosti** a potom zvolte **Přidat odkaz**.

1. Vyberte projekt obsahující kód, který budete testovat, a klepněte na tlačítko **OK**.

   ![Přidání odkazu na projekt v sadě Visual Studio](media/vs-2019/reference-manager.png)

1. Přidejte kód do metody testování částí.

   Například pro projekt MSTest můžete použít následující kód.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   Nebo pro projekt NUnit můžete použít následující kód.

   ```csharp
   using using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Další podrobnosti o vytváření testů částí naleznete v [tématu Vytvoření a spuštění testů částí spravovaného kódu](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Spuštění testů jednotek

1. Otevřete [Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Chcete-li otevřít Průzkumníka testů, zvolte **Průzkumník** > **testů** z horního řádku nabídek.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Chcete-li otevřít Průzkumníka testů, zvolte **Testovat** > **Průzkumníka testů** **systému Windows** > z horního řádku nabídek.
   ::: moniker-end

1. Spusťte testy částí klepnutím na tlačítko **Spustit vše**.

   ![Spouštění testů jednotek v Průzkumníku testů](media/vs-2019/test-explorer-run-all.png)

   Po dokončení testů zelená značka zaškrtnutí označuje, že test prošel. Červená ikona "x" označuje, že test se nezdařil.

   ![Kontrola výsledků testů částí v Průzkumníkovi testů](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Průzkumník testů](../test/run-unit-tests-with-test-explorer.md) můžete použít ke spuštění testů částí z předdefinovaného testovacího rámce (MSTest) nebo z testovacích architektur jiných výrobců. Můžete seskupit testy do kategorií, filtrovat seznam testů a vytvářet, ukládat a spouštět seznamy stop testů. Můžete také ladit testy a analyzovat výkon testu a pokrytí kódu.

## <a name="view-live-unit-test-results"></a>Zobrazit výsledky testů živých částí

Pokud používáte mstest, xUnit nebo NUnit testování rozhraní v sadě Visual Studio 2017 nebo novější, můžete zobrazit živé výsledky testů částí.

> [!NOTE]
> Testování živých částí je k dispozici pouze v edici Enterprise.

1. Z nabídky **Test** se zvolte **Test** > **Live Unit Testing** > **Start**zapněte testování živých částí .

   ::: moniker range="vs-2017"

   ![Zapnutí testování živých částí](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Spuštění testování živých částí ve Visual Studiu 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Při psaní a úpravách kódu můžete zobrazit výsledky testů v okně editoru kódu.

   ![Zobrazit výsledky testů](media/vs-2019/live-unit-testing-results.png)

1. Kliknutím na indikátor výsledku testu zobrazíte další informace, například názvy testů, které tuto metodu pokrývají.

   ![Zvolte indikátory výsledků testu](media/vs-2019/live-unit-testing-details.png)

Další informace o testování živých částí naleznete v tématu [Live unit testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generování testů jednotek pomocí funkce IntelliTest

Při spuštění IntelliTest, můžete zjistit, které testy selhávají a přidat všechny potřebné kód k jejich opravě. Můžete vybrat, které z generovaných testů uložit do testovacího projektu poskytnout regresní sadu. Při změně kódu znovu spusťte IntelliTest, aby generované testy byly synchronizovány se změnami kódu. Postup najdete v [tématu Generování testů částí kódu pomocí intelliTestu](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest je k dispozici pouze pro spravovaný kód, který cílí na rozhraní .NET Framework.

![Generování testů částí pomocí IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analýza pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Chcete-li účinně chránit před chybami, testy by měly vykonávat velkou část kódu. Informace o tom, jak, najdete [v tématu Použití pokrytí kódu k určení, kolik kódu se testuje](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Použití testovacího rámce jiného výrobce

Testy částí můžete spustit v sadě Visual Studio pomocí testovacích architektur třetích stran, jako je Boost, Google a NUnit. Pomocí **Správce balíčků NuGet** nainstalujte balíček NuGet pro rámec podle vašeho výběru. Nebo pro testovací architektury NUnit a xUnit visual studio obsahuje předkonfigurované šablony testovacích projektů, které obsahují nezbytné balíčky NuGet.

Chcete-li vytvořit testy částí, které používají [NUnit](https://nunit.org/):

1. Otevřete řešení, které obsahuje kód, který chcete testovat.

2. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a zvolte **Přidat** > **nový projekt**.

3. Vyberte šablonu projektu **NUnit Test Project.**

   ::: moniker range=">=vs-2019"

   ![Šablona testovacího projektu NUnit ve Visual Studiu 2019](media/vs-2019/nunit-test-project-template.png)

   Klepněte na tlačítko **Další**, pojmenujte projekt a potom klepněte na **tlačítko Vytvořit**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Pojmenujte projekt a pak ho vytvořte klepnutím na **tlačítko OK.**

   ::: moniker-end

   Šablona projektu obsahuje odkazy NuGet na NUnit a NUnit3TestAdapter.

   ![Závislosti NUnit NuGet v Průzkumníku řešení](media/vs-2019/nunit-nuget-dependencies.png)

4. Přidejte odkaz z testovacího projektu do projektu, který obsahuje kód, který chcete testovat.

   Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení**a potom vyberte **přidat** > **odkaz**. (Můžete také přidat odkaz z nabídky pravým tlačítkem myši uzlu **Odkazy** nebo **závislosti.)**

5. Přidejte kód do testovací metody.

   ![Přidání kódu do souboru kódu testování částí](media/vs-2019/unit-test-method.png)

6. Spusťte test z **Průzkumníka testů** nebo kliknutím pravým tlačítkem myši na testovací kód a výběrem **možnosti Spustit test (testy).**

## <a name="see-also"></a>Viz také

* [Návod: Vytváření a spouštění testů jednotek pro spravovaný kód](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Vytvoření příkazu pro testování částí](create-unit-tests-menu.md)
* [Generování testů pomocí testu IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Spuštění testů pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Analýza pokrytí kódu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
