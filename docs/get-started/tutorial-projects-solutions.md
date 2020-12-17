---
title: Seznámení s projekty a řešení
description: Přečtěte si o rozdílech mezi projekty a řešeními a jejich používáním v aplikaci Visual Studio.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fb0f1c22b2f7055005640baff2239a0ad4a32a
ms.sourcegitcommit: fed8782b2fb2ca18a90746b6e7e0b33f3fde10f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/17/2020
ms.locfileid: "97646408"
---
# <a name="learn-about-projects-and-solutions"></a>Další informace o projektech a řešeních

V tomto úvodním článku probereme to, co znamená vytvoření *řešení* a *projektu* v aplikaci Visual Studio. Řešení je kontejner, který slouží k uspořádání jednoho nebo více souvisejících kódových projektů, například projektu knihovny tříd a odpovídajícího testovacího projektu. Podíváme se na vlastnosti projektu a na některé ze souborů, které může obsahovat. Také vytvoříme odkaz z jednoho projektu na jiný.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

Vytvoříme řešení a projekt od začátku jako vzdělávací cvičení, abychom pochopili koncept projektu. Při obecném použití sady Visual Studio budete pravděpodobně používat některé z různých *šablon* projektu, které Visual Studio nabízí při vytváření nového projektu.

> [!NOTE]
> Řešení a projekty nejsou nutné pro vývoj aplikací v aplikaci Visual Studio. Můžete také otevřít složku, která obsahuje kód a spustit kódování, sestavování a ladění. Pokud například naklonujte úložiště [GitHubu](https://github.com/) , nemusí obsahovat projekty a řešení sady Visual Studio. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Bez ohledu na jeho název není řešení "Answer". Řešení je jednoduše kontejner používaný aplikací Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Když otevřete řešení v aplikaci Visual Studio, automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Náš průzkum začneme vytvořením prázdného řešení. Až se dostanete k aplikaci Visual Studio, nebudete si pravděpodobně zcela často vytvářet prázdná řešení. Když vytvoříte nový projekt, Visual Studio automaticky vytvoří řešení pro umístění projektu, pokud již není řešení otevřeno.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

   Otevře se dialogové okno **Nový projekt** .

1. V levém podokně rozbalte položku **jiné typy projektů** a pak zvolte možnost **řešení sady Visual Studio**. V prostředním podokně vyberte šablonu **prázdná řešení** . Pojmenujte své řešení **QuickSolution** a pak klikněte na tlačítko **OK** .

   ![Prázdná šablona řešení v aplikaci Visual Studio 2017](media/tutorial-projects-new-solution.png "Prázdná šablona řešení v aplikaci Visual Studio 2017.")

   **Úvodní stránka** se zavře a na pravé straně okna sady Visual Studio se zobrazí řešení **Průzkumník řešení** . K procházení obsahu svých projektů pravděpodobně použijete **Průzkumník řešení** často.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **prázdné řešení** , vyberte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.

   ![Prázdná šablona řešení v aplikaci Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png "Prázdná šablona řešení v aplikaci Visual Studio 2019.")

    > [!TIP]
    > Pokud máte nainstalované několik úloh, **prázdná šablona řešení** se nemusí zobrazit v horní části seznamu výsledků hledání. Zkuste posun k **ostatním výsledkům na základě vašeho oddílu hledání** v seznamu. Mělo by se tady zobrazit.

4. Pojmenujte řešení **QuickSolution** a pak zvolte **vytvořit**.

   Řešení se zobrazí v **Průzkumník řešení** na pravé straně okna aplikace Visual Studio. K procházení obsahu svých projektů pravděpodobně použijete **Průzkumník řešení** často.

::: moniker-end

### <a name="add-a-project"></a>Přidat projekt

Nyní do řešení přidáme náš první projekt. Začneme s prázdným projektem a přidáte do projektu položky, které potřebujeme.

::: moniker range="vs-2017"

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte možnost **Přidat** > **Nový projekt**.

   Otevře se dialogové okno **Přidat nový projekt** .

1. V levém podokně rozbalte položku **Visual C#** a vyberte možnost **plocha systému Windows**. Pak v prostředním podokně vyberte šablonu **prázdného projektu (.NET Framework)** . Pojmenujte projekt **QuickDate** a pak zvolte **OK**.

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumník řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud nevidíte v levém podokně dialogového okna **Visual C#** , je nutné nainstalovat úlohu aplikace **.NET Desktop Development** sady Visual Studio. Visual Studio používá instalaci založenou na úlohách k instalaci jenom těch komponent, které potřebujete pro typ vývoje. Snadný způsob, jak nainstalovat novou úlohu, je kliknout na odkaz **otevřít instalační program pro Visual Studio** v levém dolním rohu dialogového okna **Přidat nový projekt** . Po spuštění Instalační program pro Visual Studio zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak klikněte na tlačítko **Upravit** .
   >
   > ![Otevřít Instalační program pro Visual Studio odkaz](media/tutorial-projects-open-installer.png "Odkaz otevřít Instalační program pro Visual Studio v dialogovém okně Přidat nový projekt v aplikaci Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte možnost **Přidat** > **Nový projekt**.

   Otevře se dialogové okno s informacemi **o přidání nového projektu**.

1. Do vyhledávacího pole v horní části zadejte text **Empty** a potom v části **jazyk** vyberte **C#** .

1. Vyberte šablonu **prázdného projektu (.NET Framework)** a klikněte na tlačítko **Další**.

1. Pojmenujte projekt **QuickDate** a pak zvolte **vytvořit**.

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumník řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud nevidíte **prázdnou šablonu projektu (.NET Framework)** , je nutné nainstalovat úlohu aplikace **.NET Desktop Development** sady Visual Studio. Visual Studio používá instalaci založenou na úlohách k instalaci jenom těch komponent, které potřebujete pro typ vývoje.
   >
   >Snadný způsob, jak nainstalovat novou úlohu při vytváření nového projektu, je odkaz pro **instalaci dalších nástrojů a funkcí** pod textem, který **nehledá, co hledáte?**. Po spuštění Instalační program pro Visual Studio zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak klikněte na tlačítko **Upravit** .
   >
   > ![Otevřít Instalační program pro Visual Studio odkaz](media/vs-2019/tutorial-projects-open-installer.png "Odkaz otevřít Instalační program pro Visual Studio v dialogovém okně vytvořit nový projekt v aplikaci Visual Studio.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidat položku do projektu

Máme prázdný projekt. Pojďme přidat soubor kódu.

1. V Průzkumník řešení klikněte pravým tlačítkem myši nebo místní nabídky projektu **QuickDate** v části vyberte možnost **Přidat**  >  **novou položku**.

   Otevře se dialogové okno **Přidat novou položku** .

1. Rozbalte položku **Visual C# položky** a pak zvolte možnost **kód**. V prostředním podokně vyberte šablonu položky **Třída** . Pojmenujte **Kalendář** třídy a pak klikněte na tlačítko **Přidat** .

   Do projektu se přidá soubor s názvem *Calendar.cs* . Přípona *. cs* na konci je přípona souboru, která je předána souborům kódu jazyka C#. Soubor se zobrazí v hierarchii Visual Project v **Průzkumník řešení** a jeho obsah je otevřen v editoru.

1. Obsah souboru *Calendar.cs* nahraďte následujícím kódem:

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

   Nemusíte porozumět tomu, co kód dělá, ale pokud chcete, můžete program spustit stisknutím **klávesy CTRL** + **F5** a podívat se, že se dnešní datum tiskne do okna konzoly (nebo standardního výstupu).

## <a name="add-a-second-project"></a>Přidat druhý projekt

Je běžné, že řešení obsahují více než jeden projekt a často tyto projekty odkazují na sebe navzájem. Některé projekty v řešení mohou být knihovny tříd, některé spustitelné aplikace a některé mohou být projekty testování částí nebo weby.

Pojďme do našeho řešení přidat projekt testování částí. Tentokrát začneme ze šablony projektu, takže nemusíme do projektu přidat další soubor kódu.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte možnost **Přidat**  >  **Nový projekt**.

::: moniker range="vs-2017"

2. V levém podokně rozbalte položku **Visual C#** a vyberte kategorii **test** . V prostředním podokně vyberte šablonu projektu **projekt testů MSTest (.NET Core)** . Pojmenujte projekt **QuickTest** a klikněte na **tlačítko OK**.

   Druhý projekt je přidán do **Průzkumník řešení** a v editoru se otevře soubor s názvem *UnitTest1.cs* .

   ![Visual Studio Průzkumník řešení se dvěma projekty](media/tutorial-projects-solution-explorer.png "Průzkumník řešení se dvěma projekty v aplikaci Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

2. V dialogovém okně **Přidat nový projekt** zadejte do vyhledávacího pole v horní části text **testu jednotek** a potom v části **jazyk** vyberte **C#** .

3. Zvolte šablonu projektu **MSTest test (.NET Core)** a klikněte na tlačítko **Další**.

4. Pojmenujte projekt **QuickTest** a pak zvolte **vytvořit**.

   Druhý projekt je přidán do **Průzkumník řešení** a v editoru se otevře soubor s názvem *UnitTest1.cs* .

   ![Visual Studio Průzkumník řešení se dvěma projekty](media/vs-2019/tutorial-projects-solution-explorer.png "Průzkumník řešení se dvěma projekty v aplikaci Visual Studio.")

::: moniker-end

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Použijeme nový projekt testování částí k otestování naší metody v projektu **QuickDate** , takže musíme přidat odkaz na tento projekt. Tím se vytvoří *závislost sestavení* mezi dvěma projekty, což znamená, že při sestavování řešení je **QuickDate** sestaven před **QuickTest**.

::: moniker range="vs-2017"

1. V projektu **QuickTest** vyberte uzel **závislosti** a v místní nabídce klikněte pravým tlačítkem myši nebo vyberte možnost **Přidat odkaz**.

   Otevře se dialogové okno **Správce odkazů** .

1. V levém podokně rozbalte položku **projekty** a klikněte na možnost **řešení**. V prostředním podokně klikněte na zaškrtávací políčko vedle **QuickDate** a pak zvolte **OK**.

   Přidá se odkaz na projekt **QuickDate** .

   ![Visual Studio 2019 Průzkumník řešení zobrazení odkazu na projekt](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Průzkumník řešení zobrazení odkazu na projekt v aplikaci Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. V projektu **QuickTest** vyberte uzel **závislosti** a v místní nabídce klikněte pravým tlačítkem myši nebo vyberte možnost **Přidat odkaz na projekt.**...

   Otevře se dialogové okno **Správce odkazů** .

1. V levém podokně rozbalte položku **projekty** a klikněte na možnost **řešení**. V prostředním podokně klikněte na zaškrtávací políčko vedle **QuickDate** a pak zvolte **OK**.

   Přidá se odkaz na projekt **QuickDate** .

   ![Visual Studio 2019 Průzkumník řešení zobrazení odkazu na projekt](media/vs-2019/tutorial-projects-solution-explorer-reference.png)
   
::: moniker-end

## <a name="add-test-code"></a>Přidat testovací kód

1. Nyní přidáme testovací kód do souboru testovacího kódu C#. Obsah *UnitTest1.cs* nahraďte následujícím kódem:

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

   V části kódu se zobrazí červená vlnovka. Tuto chybu vyřešíme tak, že projekt testů vytvoří pro projekt **QuickDate** [sestavení typu Friend](/dotnet/standard/assembly/friend-assemblies) .

1. Zpátky v projektu **QuickDate** otevřete soubor *Calendar.cs* , pokud ještě není otevřený. Přidejte následující [příkaz using](/dotnet/csharp/language-reference/keywords/using-statement) a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut na začátek souboru pro vyřešení chyby v testovacím projektu.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Soubor kódu by měl vypadat takto:

   ![CSharp kód](media/tutorial-projects-cs-code.png "Fragment kódu z části Přidat testovací kód v tomto článku.")

## <a name="project-properties"></a>Vlastnosti projektu

Řádek v souboru *Calendar.cs* , který obsahuje atribut, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> odkazuje na název sestavení (název souboru) projektu **QuickTest** . Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumník řešení** vyberte projekt **QuickTest** . V místní nabídce klepněte pravým tlačítkem myši nebo vyberte možnost **vlastnosti**, nebo stačí stisknout klávesu **ALT** + **ENTER**.

   *Stránky vlastností* projektu otevřené na kartě **aplikace** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení projektu **QuickTest** je skutečně "QuickTest". Pokud jste ho chtěli změnit, je to místo, kde to uděláte. Při sestavování testovacího projektu se pak název výsledného binárního souboru změní z *QuickTest.dll* na cokoliv, co jste zvolili.

   ![Vlastnosti projektu](media/tutorial-projects-netcore-properties.png "Dialogové okno Vlastnosti projektu v aplikaci Visual Studio.")

1. Prozkoumejte některé z ostatních karet na stránkách vlastností projektu, jako je například **sestavení** a **ladění**. Tyto karty jsou odlišné pro různé typy projektů.

## <a name="next-steps"></a>Další kroky

Chcete-li zkontrolovat, zda je test jednotky funkční, vyberte možnost **test**  >  **Spustit**  >  **všechny testy** z řádku nabídek. Otevře se okno s názvem **Průzkumník testů** , které by mělo vidět, že test **TestGetCurrentDate** projde.

![Průzkumník testů v aplikaci Visual Studio zobrazující prošlý test](media/tutorial-projects-test-explorer.png "Průzkumník testů v aplikaci Visual Studio zobrazující úspěšný test.")

::: moniker range="vs-2017"

> [!TIP]
> Pokud se **Průzkumník testů** neotevře automaticky, otevřete ho výběrem příkazu **test**  >  **Windows**  >  **Test Explorer** z řádku nabídek.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Pokud se **Průzkumník testů** neotevře automaticky, otevřete ho výběrem možnosti **test**  >  **Test Explorer** z řádku nabídek.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Vytváření projektů a řešení](../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
