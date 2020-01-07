---
title: Úvod do projektů a řešení
ms.date: 07/22/2019
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c130f7f55409bd24520dd55e949d20e8d5bbb97
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567265"
---
# <a name="learn-about-projects-and-solutions"></a>Seznamte se s projekty a řešení

V tomto článku úvodní podíváme, co to znamená, že k vytvoření *řešení* a *projektu* v sadě Visual Studio. Řešení je kontejner, který slouží k uspořádání jednoho nebo více souvisejících kódových projektů, například projektu knihovny tříd a odpovídajícího testovacího projektu. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Také vytvoříme odkaz z jednoho projektu do druhého.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

Jako vzdělávací cvičení porozumět koncepci projekt jsme vám vytvořit řešení a projektu od začátku. V obecné používání sady Visual Studio, budete pravděpodobně používat některé z různých projektů *šablony* , nabízí Visual Studio při vytvoření nového projektu.

> [!NOTE]
> Řešení a projekty není nutné pro vývoj aplikací v sadě Visual Studio. Můžete také pouze otevřít složku, která obsahuje kód a začít kódování, sestavování a ladění. Například, pokud naklonujete [Githubu](https://github.com/) úložiště, nemusí obsahovat řešení a projektů sady Visual Studio. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Bez ohledu na jeho název není řešení "Answer". Řešení je jednoduše kontejner používaný aplikací Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Když otevřete řešení v aplikaci Visual Studio, automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Naše zkoumání začneme vytvořením prázdné řešení. Po získání znát sady Visual Studio, které pravděpodobně nenajdete sami velmi často vytvoření prázdných řešení. Při vytváření nového projektu sady Visual Studio automaticky vytvoří řešení k umístění projektu, pokud existuje řešení ještě není otevřený.

::: moniker range="vs-2017"

1. Otevřít Visual Studio.

1. Na horním panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

   **Nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **ostatní typy projektů**, klikněte na tlačítko **řešení sady Visual Studio**. V prostředním podokně, vyberte **prázdné řešení** šablony. Název řešení **QuickSolution**, klikněte na tlačítko **OK** tlačítko.

   ![Prázdná šablona řešení v aplikaci Visual Studio 2017](media/tutorial-projects-new-solution.png)

   **Úvodní stránka** zavře a řešení se zobrazí v **Průzkumníka řešení** na pravé straně okna nástroje Visual Studio. Je pravděpodobně použijete **Průzkumníka řešení** často, procházet obsah vašich projektů.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **prázdné řešení** , vyberte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.

   ![Prázdná šablona řešení v aplikaci Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Pojmenujte řešení **QuickSolution**a pak zvolte **vytvořit**.

   Řešení se zobrazí v **Průzkumník řešení** na pravé straně okna aplikace Visual Studio. Je pravděpodobně použijete **Průzkumníka řešení** často, procházet obsah vašich projektů.

::: moniker-end

### <a name="add-a-project"></a>Přidat do projektu

Nyní Pojďme přidat naši první projekt do řešení. Začneme s prázdným projektem a přidejte položky, které potřebujeme do projektu.

::: moniker range="vs-2017"

1. V **Průzkumník řešení**klikněte pravým tlačítkem nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte **Přidat** > **Nový projekt**.

   **Přidat nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **Visual C#** a zvolte **Windows Desktop**. Potom v prostředním podokně, vyberte **prázdný projekt (.NET Framework)** šablony. Pojmenujte projekt **QuickDate**a pak zvolte **OK**.

   Zobrazí se pod řešení v projektu s názvem QuickDate **Průzkumníka řešení**. Aktuálně obsahuje jediný soubor volané *App.config*.

   > [!NOTE]
   > Pokud nevidíte **Visual C#** v levém podokně dialogového okna, je potřeba nainstalovat **vývoj desktopových aplikací .NET** sady Visual Studio *úlohy*. Visual Studio používá pouze nainstalovat součásti, které potřebujete pro typ vývoje, které vám instalace na základě pracovního vytížení. Snadný způsob, jak nainstalovat nový pracovní postup je vybrat **otevřít instalační program Visual Studio** odkaz v levém dolním rohu **přidat nový projekt** dialogové okno. Až se spustí instalační program sady Visual Studio, zvolte **vývoj desktopových aplikací .NET** úlohy a pak **změnit** tlačítko.
   >
   > ![Otevřít odkaz instalační program sady Visual Studio](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení**klikněte pravým tlačítkem nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte **Přidat** > **Nový projekt**.

   Otevře se dialogové okno s informacemi **o přidání nového projektu**.

1. Do vyhledávacího pole v horní části zadejte text **Empty** a pak vyberte **C#** v části **jazyk**.

1. Vyberte šablonu **prázdného projektu (.NET Framework)** a klikněte na tlačítko **Další**.

1. Pojmenujte projekt **QuickDate**a pak zvolte **vytvořit**.

   Zobrazí se pod řešení v projektu s názvem QuickDate **Průzkumníka řešení**. Aktuálně obsahuje jediný soubor volané *App.config*.

   > [!NOTE]
   > Pokud nevidíte **prázdnou šablonu projektu (.NET Framework)** , je nutné nainstalovat *úlohu*aplikace **.NET Desktop Development** sady Visual Studio. Visual Studio používá pouze nainstalovat součásti, které potřebujete pro typ vývoje, které vám instalace na základě pracovního vytížení. Snadný způsob, jak nainstalovat novou úlohu při vytváření nového projektu, je odkaz pro **instalaci dalších nástrojů a funkcí** pod textem, který **nehledá, co hledáte?** . Až se spustí instalační program sady Visual Studio, zvolte **vývoj desktopových aplikací .NET** úlohy a pak **změnit** tlačítko.
   >
   > ![Otevřít odkaz instalační program sady Visual Studio](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Prázdný projekt máme. Přidejme souboru kódu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **QuickDate** projekt **Průzkumníka řešení**, zvolte **přidat** > **novou položku** .

   **Přidat novou položku** zobrazí se dialogové okno.

1. Rozbalte **položky Visual C#** , klikněte na tlačítko **kód**. V prostředním podokně vyberte **třídy** šablony položky. Název třídy **kalendáře**a klikněte na tlačítko **přidat** tlačítko.

   Soubor s názvem *Calendar.cs* se přidá do projektu. *.Cs* na konci je přípona souboru, která je přidělena soubory kódu jazyka C#. Soubor se zobrazí v hierarchii projektu vizuálu v **Průzkumníka řešení**, a její obsah se otevře v editoru.

1. Nahraďte obsah *Calendar.cs* souboru následujícím kódem:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Není nutné pochopit, co kód dělá, ale pokud chcete, můžete program spustit stisknutím kombinace kláves **Ctrl**+**F5** a podívejte se, že vytiskne okno dnešní datum konzoly (nebo standardní výstup).

## <a name="add-a-second-project"></a>Přidáte druhý projekt

Je běžné, že řešení tak, aby obsahovala více než jeden projekt a často tyto projekty odkaz na sebe navzájem. Některé projekty v řešení může být knihoven tříd, některých aplikací spustitelných souborů a některé můžou být projektů testů jednotek nebo weby.

Přidejme do našich řešení projekt testování částí. Tentokrát začneme ze šablony projektu, nemáme k přidání dalšího kódu souboru do projektu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **řešení "QuickSolution"** v **Průzkumníka řešení**, zvolte **přidat** > **nový projekt**.

::: moniker range="vs-2017"

2. V levém podokně rozbalte položku **vizuál C#**  a vyberte kategorii **test** . V prostředním podokně vyberte šablonu projektu **projekt testů MSTest (.NET Core)** . Pojmenujte projekt **QuickTest**a klikněte na **tlačítko OK**.

   Druhý projekt je přidán do **Průzkumník řešení**a v editoru se otevře soubor s názvem *UnitTest1.cs* .

   ![Průzkumník řešení Visual Studio se dva projekty](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V dialogovém okně **Přidat nový projekt** zadejte do pole Hledat v horní části text **testu jednotek** a potom vyberte **C#** v části **jazyk**.

3. Zvolte šablonu projektu **MSTest test (.NET Core)** a klikněte na tlačítko **Další**.

4. Pojmenujte projekt **QuickTest**a pak zvolte **vytvořit**.

   Druhý projekt je přidán do **Průzkumník řešení**a v editoru se otevře soubor s názvem *UnitTest1.cs* .

   ![Průzkumník řešení Visual Studio se dva projekty](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Chceme použít testovací projekt nové jednotky k otestování v metodě **QuickDate** projektu, takže je potřeba přidat odkaz na tento projekt. Tím se vytvoří *závislosti sestavení* mezi dva projekty, to znamená, že při sestavování řešení, **QuickDate** sestaveny dříve, než **QuickTest**.

1. V projektu **QuickTest** vyberte uzel **závislosti** a v místní nabídce klikněte pravým tlačítkem myši nebo vyberte možnost **Přidat odkaz**.

   **Správce odkazů** zobrazí se dialogové okno.

1. V levém podokně rozbalte **projekty** a zvolte **řešení**. V prostředním podokně klikněte na zaškrtávací políčko vedle **QuickDate**a pak zvolte * * OK.

   Odkaz na **QuickDate** projekt je přidán.

   ![Visual Studio 2019 Průzkumník řešení zobrazení odkazu na projekt](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Přidat testovací kód

1. Nyní přidáme testovací kód do souboru C# testovacího kódu. Obsah *UnitTest1.cs* nahraďte následujícím kódem:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   V části kódu se zobrazí červená vlnovka. Opravíme tuto chybu tak, že projekt testů [sestavení typu friend](/dotnet/standard/assembly/friend-assemblies) k **QuickDate** projektu.

1. Zpátky v projektu **QuickDate** otevřete soubor *Calendar.cs* , pokud ještě není otevřený. Přidejte následující [příkaz using](/dotnet/csharp/language-reference/keywords/using-statement) a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut na začátek souboru, chcete-li vyřešit chybu v testovacím projektu.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Soubor kódu by měl vypadat nějak takto:

   ![Kód CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Vlastnosti projektu

Na řádku *Calendar.cs* soubor, který obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut odkazuje na název sestavení (název souboru) **QuickTest** projektu. Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumníka řešení**, vyberte **QuickTest** projektu. V nabídce klepněte pravým tlačítkem nebo kontextu vyberte **vlastnosti**, nebo stačí stisknout kombinaci kláves **Alt**+**Enter**.

   *Stránky vlastností* projektu otevřené na kartě **aplikace** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení **QuickTest** projekt je skutečně "QuickTest". Pokud chcete změnit, toto je tam, kde by, která dělají. Potom, když sestavíte testovací projekt, název výsledný binární soubor změní z *QuickTest.dll* na cokoli, co jste zvolili.

   ![Vlastnosti projektu](media/tutorial-projects-netcore-properties.png)

1. Prozkoumejte některé z ostatních karet na stránkách vlastností projektu, jako je například **sestavení** a **ladění**. Tyto karty se liší pro různé typy projektů.

## <a name="next-steps"></a>Další kroky

Pokud chcete zkontrolovat, že je funkční testování částí, zvolte **testování** > **spustit** > **všechny testy** z řádku nabídek. Zobrazí se okno **Průzkumníka testů** otevře a měli byste vidět, který **TestGetCurrentDate** testovací průchody.

![Průzkumník testů v sadě Visual Studio zobrazuje předaný testu](media/tutorial-projects-test-explorer.png)

> [!TIP]
> Pokud **Průzkumník testů** nebude automaticky otevřené, otevřete ho kliknutím **testovací** > **Windows** > **Průzkumník testů** z řádku nabídek.

## <a name="see-also"></a>Viz také:

- [Vytváření projektů a řešení](../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE – přehled](../get-started/visual-studio-ide.md)
