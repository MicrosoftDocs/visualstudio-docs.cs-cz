---
title: Začínáme s testováním jednotek
description: Pomocí sady Visual Studio definujte a spusťte testy jednotek, které udržují stav kódu, a vyhledejte chyby a chyby před vašimi zákazníky.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e1576f8865fc5945514ce6965cdba66a1cfda55
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386047"
---
# <a name="get-started-with-unit-testing"></a>Začínáme s testováním jednotek

Pomocí sady Visual Studio definujte a spusťte testy jednotek, abyste zachovali stav kódu, zajistili pokrytí kódu a vyhledali chyby a chyby před vašimi zákazníky. Pravidelně spouštějte testy jednotek, abyste se ujistili, že váš kód funguje správně.

V tomto článku kód a ilustrace používají jazyk C#, ale koncepty a funkce se vztahují na jazyky .NET, C++, Python, JavaScript a TypeScript.

## <a name="create-unit-tests"></a>Create unit tests
(Vytvořit testy jednotek)

Tato část popisuje, jak vytvořit projekt testování částí.

1. Otevřete projekt, který chcete testovat v aplikaci Visual Studio.

   Pro účely demonstrace ukázkového testu jednotek Tento článek testuje jednoduchý projekt C# "Hello World" s názvem **HelloWorldCore**. Vzorový kód pro takový projekt je následující:

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

1. V **Průzkumník řešení** vyberte uzel řešení. Pak na horním panelu nabídek vyberte **soubor**  >  **Přidat**  >  **Nový projekt**.

1. V dialogovém okně Nový projekt vyhledejte šablonu projektu testování částí pro testovací rozhraní, které chcete použít, například MSTest, a vyberte ji.

   Počínaje verzí Visual Studio 2017 verze 14,8 obsahují jazyky .NET předdefinované šablony pro NUnit a xUnit. V jazyce C++ bude nutné vybrat testovací rozhraní podporované jazykem. Pro Python si přečtěte téma [nastavení testování částí v kódu Pythonu](../python/unit-testing-python-in-visual-studio.md) pro nastavení testovacího projektu.

   > [!TIP]
   > V jazyce C# můžete vytvořit projekty testování částí z kódu pomocí rychlejší metody. Další informace najdete v tématu [vytvoření projektů testování částí a testovacích metod](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Chcete-li použít tuto metodu pro .NET Core nebo .NET Standard, je vyžadována aplikace Visual Studio 2019.

   Následující ilustrace znázorňuje MSTest test jednotek, který je podporován v rozhraní .NET.

   ::: moniker range=">=vs-2019"

   ![Šablona projektu testování částí v aplikaci Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Klikněte na **Další**, zvolte název testovacího projektu a pak klikněte na **vytvořit**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Šablona projektu testování částí v aplikaci Visual Studio 2019](media/mstest-test-project-template.png)

   Zvolte název testovacího projektu, například HelloWorldTests, a pak klikněte na **OK**.

   ::: moniker-end

   Projekt se přidá do vašeho řešení.

   ![Projekt testování částí v Průzkumník řešení](media/vs-2019/solution-explorer.png)

1. V projektu testování jednotky přidejte odkaz na projekt, který chcete otestovat, kliknutím pravým tlačítkem myši na **odkazy** nebo **závislosti** a následným výběrem možnosti **Přidat odkaz**.

1. Vyberte projekt, který obsahuje kód, který budete testovat, a klikněte na **OK**.

   ![Přidat odkaz na projekt v aplikaci Visual Studio](media/vs-2019/reference-manager.png)

1. Přidejte kód do metody testování částí.

   Například můžete použít následující kód tak, že vyberete správnou kartu dokumentace, která odpovídá vašemu testovacímu rozhraní: MSTest, NUnit nebo xUnit (podporováno pouze v rozhraní .NET).

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

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

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

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

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ---

## <a name="run-unit-tests"></a>Spuštění testů jednotek

1. Otevřete [Průzkumník testů](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Chcete-li otevřít Průzkumníka testů, zvolte možnost **testovat** > **Průzkumníka** testů v horním řádku nabídky (nebo stiskněte klávesy **CTRL +** + , **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Chcete-li otevřít Průzkumníka testů  , v > horním řádku nabídek vyberte test  > **Průzkumník testů** systému Windows.
   ::: moniker-end

1. Spusťte testy jednotek kliknutím na tlačítko **Spustit vše** (nebo stiskněte klávesovou **zkratku CTRL**  +  **R**, **V**).

   ![Spouštění testů jednotek v Průzkumníku testů](media/vs-2019/test-explorer-run-all.png)

   Po dokončení testů zelená značka zaškrtnutí značí, že test proběhl úspěšně. Červená ikona "x" značí, že se test nezdařil.

   ![Kontrola výsledků testování částí v Průzkumníku testů](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Můžete použít [Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md) ke spuštění testů jednotek z integrovaného testovacího rozhraní (MSTest) nebo z testovacích rozhraní třetích stran. Můžete seskupit testy do kategorií, filtrovat seznam testů a vytvářet, ukládat a spouštět seznamy testů. Můžete také ladit testy a analyzovat výkon testu a pokrytí kódu.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Zobrazit výsledky živého testu jednotek (Visual Studio Enterprise)

Pokud používáte testovací rozhraní MSTest, xUnit nebo NUnit v aplikaci Visual Studio 2017 nebo novější, můžete zobrazit živé výsledky testů jednotek.

> [!NOTE]
> Pokud chcete postupovat podle těchto kroků, Visual Studio Enterprise je potřeba.

1. V nabídce **test** zapněte živé testování jednotek výběrem možnosti **test**  >  **Live Unit Testing**  >  **Spustit**.

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

## <a name="use-a-third-party-test-framework"></a>Použití testovacího rozhraní třetí strany

V aplikaci Visual Studio můžete spouštět testy jednotek pomocí testovacích rozhraní třetích stran, jako je například zvýšení úrovně, Google a NUnit, v závislosti na vašem programovacím jazyce. Použití architektury třetí strany:

- Pomocí **Správce balíčků NuGet** nainstalujte balíček NuGet pro rozhraní podle vašeho výběru.

- Platformy Počínaje verzí Visual Studio 2017 verze 14,6 obsahuje Visual Studio předem nakonfigurované šablony testů pro testovací architektury NUnit a xUnit. Šablony také obsahují potřebné balíčky NuGet pro povolení podpory.

- Volat V aplikaci Visual Studio 2017 a novějších verzích jsou již některé architektury, jako je například zvýšení, zahrnuty. Další informace najdete v tématu [zápis testů jednotek pro C/C++ v aplikaci Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Postup přidání projektu testu jednotek:

1. Otevřete řešení, které obsahuje kód, který chcete otestovat.

2. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **Nový projekt**.

3. Vyberte šablonu projektu testování částí.

   V tomto příkladu vyberte [nunit](https://nunit.org/)

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

   V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a pak vyberte **Přidat**  >  **odkaz**. (Můžete také přidat odkaz z místní nabídky na uzlu **odkazy** nebo **závislosti** .)

5. Přidejte kód do testovací metody.

   ![Přidat kód do souboru kódu testu jednotek](media/vs-2019/unit-test-method.png)

6. Spusťte test z **Průzkumníka testů** nebo kliknutím pravým tlačítkem na testovací kód a zvolením možnosti **Spustit testy** (nebo **CTRL**  +  **R**, **T**).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Základní informace o testování částí](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Vytváření a spouštění testů jednotek pro spravovaný kód](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
