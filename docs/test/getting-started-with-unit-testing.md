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
ms.openlocfilehash: c167e98f9419842876aed713e008b8746064669a
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82153038"
---
# <a name="get-started-with-unit-testing"></a>Začínáme s testováním jednotek

Pomocí sady Visual Studio definujte a spusťte testy jednotek, abyste zachovali stav kódu, zajistili pokrytí kódu a vyhledali chyby a chyby před vašimi zákazníky. Pravidelně spouštějte testy jednotek, abyste se ujistili, že váš kód funguje správně.

## <a name="create-unit-tests"></a>Create unit tests
(Vytvořit testy jednotek)

Tato část popisuje, jak vytvořit projekt testování částí.

1. Otevřete projekt, který chcete testovat v aplikaci Visual Studio.

   Pro účely demonstrace ukázkového testu jednotek Tento článek testuje jednoduchý projekt "Hello World" s názvem **HelloWorldCore**. Vzorový kód pro takový projekt je následující:

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

1. V **Průzkumník řešení**vyberte uzel řešení. Pak na horním panelu nabídek vyberte **soubor** > **Přidat** > **Nový projekt**.

1. V dialogovém okně Nový projekt vyhledejte šablonu projektu testování částí pro testovací rozhraní, které chcete použít, a vyberte ji.

   ::: moniker range=">=vs-2019"

   ![Šablona projektu testování částí v aplikaci Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Klikněte na **Další**, zvolte název testovacího projektu a pak klikněte na **vytvořit**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Šablona projektu testování částí v aplikaci Visual Studio 2019](media/mstest-test-project-template.png)

   Zvolte název testovacího projektu a klikněte na tlačítko **OK**.

   ::: moniker-end

   Projekt se přidá do vašeho řešení.

   ![Projekt testování částí v Průzkumník řešení](media/vs-2019/solution-explorer.png)

1. V projektu testování jednotky přidejte odkaz na projekt, který chcete otestovat, kliknutím pravým tlačítkem myši na **odkazy** nebo **závislosti** a následným výběrem možnosti **Přidat odkaz**.

1. Vyberte projekt, který obsahuje kód, který budete testovat, a klikněte na **OK**.

   ![Přidat odkaz na projekt v aplikaci Visual Studio](media/vs-2019/reference-manager.png)

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
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
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
> Další informace o vytváření testů jednotek najdete v tématu [Vytvoření a spuštění testů jednotek pro spravovaný kód](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Spuštění testů jednotek

1. Otevřete [Průzkumník testů](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Chcete-li otevřít Průzkumníka testů, v horním řádku nabídek vyberte **test** > **Test Explorer** .
   ::: moniker-end
   ::: moniker range="vs-2017"
   Chcete-li otevřít Průzkumníka testů, v horním řádku nabídek vyberte **test** > **Průzkumník testů** **systému Windows** > .
   ::: moniker-end

1. Spusťte testy jednotek kliknutím na **Spustit vše**.

   ![Spouštění testů jednotek v Průzkumníku testů](media/vs-2019/test-explorer-run-all.png)

   Po dokončení testů zelená značka zaškrtnutí značí, že test proběhl úspěšně. Červená ikona "x" značí, že se test nezdařil.

   ![Kontrola výsledků testování částí v Průzkumníku testů](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Můžete použít [Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) ke spuštění testů jednotek z integrovaného testovacího rozhraní (MSTest) nebo z testovacích rozhraní třetích stran. Můžete seskupit testy do kategorií, filtrovat seznam testů a vytvářet, ukládat a spouštět seznamy testů. Můžete také ladit testy a analyzovat výkon testu a pokrytí kódu.

## <a name="view-live-unit-test-results"></a>Zobrazit výsledky živého testu jednotek

Pokud používáte testovací rozhraní MSTest, xUnit nebo NUnit v aplikaci Visual Studio 2017 nebo novější, můžete zobrazit živé výsledky testů jednotek.

> [!NOTE]
> Live Unit Testing je k dispozici pouze v edici Enterprise.

1. V nabídce **test** zapněte živé testování jednotek výběrem možnosti **test** > **Live Unit Testing** > **Spustit**.

   ::: moniker range="vs-2017"

   ![Zapnout funkci Live Unit Testing](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Spustit Live Unit Testing v aplikaci Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Umožňuje zobrazit výsledky testů v rámci okna editoru kódu při psaní a úpravách kódu.

   ![Zobrazit výsledky testů](media/vs-2019/live-unit-testing-results.png)

1. Kliknutím na indikátor výsledku testu zobrazíte další informace, například názvy testů, které pokrývají tuto metodu.

   ![Zvolit indikátory výsledku testu](media/vs-2019/live-unit-testing-details.png)

Další informace o živém testování částí naleznete v tématu [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generování testů jednotek pomocí funkce IntelliTest

Při spuštění IntelliTest můžete zjistit, které testy selžou, a přidat potřebný kód, který je opraví. Můžete vybrat, které z vygenerovaných testů mají být uloženy do projektu testů pro zajištění regresní sady. Při změně kódu znovu spusťte IntelliTest, abyste zachovali vygenerované testy v synchronizaci se změnami kódu. Informace o tom, jak najdete v tématu [generování testování částí kódu pomocí IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest je k dispozici pouze pro spravovaný kód, který cílí na .NET Framework.

![Generování testů jednotek pomocí IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analyzovat pokrytí kódu

Funkci pokrytí kódu sady Visual Studio lze použít ke zjištění toho, jaký podíl kódu projektu je skutečně testován kódovanými testy, jako jsou například jednotkové testy. Aby bylo možné efektivně chránit proti chybám, testy by měly vyvolávat velký podíl kódu. Další informace o tom, jak zjistit, kolik [kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md), najdete v tématu Použití pokrytí kódu.

## <a name="use-a-third-party-test-framework"></a>Použití testovacího rozhraní třetí strany

Testy jednotek můžete spustit v aplikaci Visual Studio pomocí testovacích rozhraní třetích stran, jako je například zvýšení úrovně, Google nebo NUnit. Pomocí **Správce balíčků NuGet** nainstalujte balíček NuGet pro rozhraní podle vašeho výběru. Nebo pro testovací architektury NUnit a xUnit obsahuje Visual Studio předem nakonfigurované šablony testovacích projektů, které obsahují nezbytné balíčky NuGet.

Postup vytvoření jednotkových testů, které používají [nunit](https://nunit.org/):

1. Otevřete řešení, které obsahuje kód, který chcete otestovat.

2. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.

3. Vyberte šablonu projektu **projektu testu nunit** .

   ::: moniker range=">=vs-2019"

   ![Šablona projektu testů NUnit v aplikaci Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Klikněte na **Další**, pojmenujte projekt a pak klikněte na **vytvořit**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Pojmenujte projekt a kliknutím na tlačítko **OK** jej vytvořte.

   ::: moniker-end

   Šablona projektu obsahuje odkazy NuGet na NUnit a NUnit3TestAdapter.

   ![NUnit závislosti NuGet v Průzkumník řešení](media/vs-2019/nunit-nuget-dependencies.png)

4. Přidejte odkaz z testovacího projektu do projektu, který obsahuje kód, který chcete otestovat.

   V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak vyberte **Přidat** > **odkaz**. (Můžete také přidat odkaz z místní nabídky na uzlu **odkazy** nebo **závislosti** .)

5. Přidejte kód do testovací metody.

   ![Přidat kód do souboru kódu testu jednotek](media/vs-2019/unit-test-method.png)

6. Spusťte test z **Průzkumníka testů** nebo kliknutím pravým tlačítkem na testovací kód a výběrem možnosti **Spustit testy**.

## <a name="see-also"></a>Viz také

* [Návod: Vytváření a spouštění testů jednotek pro spravovaný kód](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Vytvoření příkazu pro testování částí](create-unit-tests-menu.md)
* [Generování testů pomocí IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Spuštění testů pomocí Průzkumníka testů](run-unit-tests-with-test-explorer.md)
* [Analyzovat pokrytí kódu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
