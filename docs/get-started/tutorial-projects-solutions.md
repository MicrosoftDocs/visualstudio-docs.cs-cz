---
title: Úvod do projektů a řešení
ms.date: 12/11/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 089060f8afc4f735f4fe2e27b956cacff3e1b892
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348447"
---
# <a name="learn-about-projects-and-solutions"></a>Seznamte se s projekty a řešení

V tomto článku úvodní podíváme, co to znamená, že k vytvoření *řešení* a *projektu* v sadě Visual Studio. Řešení je kontejner, který se používá k uspořádání jeden nebo více souvisejících projekty kódu, například projekt knihovny tříd a odpovídající testovací projekt. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Také vytvoříme odkaz z jednoho projektu do druhého.

> [!TIP]
> Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

Jako vzdělávací cvičení porozumět koncepci projekt jsme vám vytvořit řešení a projektu od začátku. V obecné používání sady Visual Studio, budete pravděpodobně používat některé z různých projektů *šablony* , nabízí Visual Studio při vytvoření nového projektu.

> [!NOTE]
> Řešení a projekty není nutné pro vývoj aplikací v sadě Visual Studio. Můžete také pouze otevřít složku, která obsahuje kód a začít kódování, sestavování a ladění. Například, pokud naklonujete [Githubu](https://github.com/) úložiště, nemusí obsahovat řešení a projektů sady Visual Studio. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Bez ohledu na jeho název řešení není "odpověď". Řešení je prostě kontejner používá sada Visual Studio k uspořádání jeden nebo více souvisejících projektů. Když otevřete řešení v sadě Visual Studio automaticky načte všechny projekty, které obsahuje řešení.

### <a name="create-a-solution"></a>Vytvoření řešení

Naše zkoumání začneme vytvořením prázdné řešení. Po získání znát sady Visual Studio, které pravděpodobně nenajdete sami velmi často vytvoření prázdných řešení. Při vytváření nového projektu sady Visual Studio automaticky vytvoří řešení k umístění projektu, pokud existuje řešení ještě není otevřený.

1. Otevřít Visual Studio.

1. Na panelu nabídek, které, jako je na řádku nabídek **souboru** a **upravit**, zvolte **souboru** > **nový**  >   **Projekt**.

   **Nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **ostatní typy projektů**, klikněte na tlačítko **řešení sady Visual Studio**. V prostředním podokně, vyberte **prázdné řešení** šablony. Název řešení **QuickSolution**, klikněte na tlačítko **OK** tlačítko.

   ![Šablonu prázdného řešení v sadě Visual Studio](media/tutorial-projects-new-solution.png)

   **Úvodní stránka** zavře a řešení se zobrazí v **Průzkumníka řešení** na pravé straně okna nástroje Visual Studio. Je pravděpodobně použijete **Průzkumníka řešení** často, procházet obsah vašich projektů.

### <a name="add-a-project"></a>Přidat do projektu

Nyní Pojďme přidat naši první projekt do řešení. Začneme s prázdným projektem a přidejte položky, které potřebujeme do projektu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **řešení "QuickSolution"** v **Průzkumníka řešení**, zvolte **přidat** > **nový projekt**.

   **Přidat nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **Visual C#** a zvolte **Windows Desktop**. Potom v prostředním podokně, vyberte **prázdný projekt (.NET Framework)** šablony. Pojmenujte projekt **QuickDate**, klikněte na tlačítko **OK** tlačítko.

   Zobrazí se pod řešení v projektu s názvem QuickDate **Průzkumníka řešení**. Aktuálně obsahuje jediný soubor volané *App.config*.

   > [!NOTE]
   > Pokud nevidíte **Visual C#** v levém podokně dialogového okna, je potřeba nainstalovat **vývoj desktopových aplikací .NET** sady Visual Studio *úlohy*. Visual Studio používá pouze nainstalovat součásti, které potřebujete pro typ vývoje, které vám instalace na základě pracovního vytížení. Snadný způsob, jak nainstalovat nový pracovní postup je vybrat **otevřít instalační program Visual Studio** odkaz v levém dolním rohu **přidat nový projekt** dialogové okno. Až se spustí instalační program sady Visual Studio, zvolte **vývoj desktopových aplikací .NET** úlohy a pak **změnit** tlačítko.

   ![Otevřít odkaz instalační program sady Visual Studio](media/tutorial-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Prázdný projekt máme. Přidejme souboru kódu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **QuickDate** projekt **Průzkumníka řešení**, zvolte **přidat** > **novou položku** .

   **Přidat novou položku** zobrazí se dialogové okno.

1. Rozbalte **položky Visual C#**, klikněte na tlačítko **kód**. V prostředním podokně vyberte **třídy** šablony položky. Název třídy **kalendáře**a klikněte na tlačítko **přidat** tlačítko.

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

   **Přidat nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **jazyka Visual Basic** a zvolte **Test** kategorie. V prostředním podokně, vyberte **projekt testu jednotek (.NET Framework)** šablony projektu. Pojmenujte projekt **QuickTest**a klikněte na tlačítko **OK** tlačítko.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.vb* otevře v editoru. *.vb* je přípona souboru, který je přiřazen do souborů s kódem jazyka Visual Basic.

   ![Průzkumník řešení Visual Studio se dva projekty](media/tutorial-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Chceme použít testovací projekt nové jednotky k otestování v metodě **QuickDate** projektu, takže je potřeba přidat odkaz na tento projekt. Tím se vytvoří *závislosti sestavení* mezi dva projekty, to znamená, že při sestavování řešení, **QuickDate** sestaveny dříve, než **QuickTest**.

1. Zvolte **odkazy** uzlu v **QuickTest** projektu a v nabídce klepněte pravým tlačítkem nebo kontextu zvolte **přidat odkaz**.

   ![Přidat odkaz na nabídku](media/tutorial-projects-add-reference.png)

   **Správce odkazů** zobrazí se dialogové okno.

1. V levém podokně rozbalte **projekty** a zvolte **řešení**. V prostředním podokně zaškrtněte políčko vedle položky **QuickDate**a klikněte na tlačítko **OK** tlačítko.

   Odkaz na **QuickDate** projekt je přidán.

## <a name="add-test-code"></a>Přidat testovací kód

1. Teď přidáme testovací kód do souboru kódu jazyka Visual Basic. Nahraďte obsah *UnitTest1.vb* následujícím kódem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Zobrazí se vám červený "podtržení" v části některý kód. Opravíme tuto chybu tak, že projekt testů [sestavení typu friend](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) k **QuickDate** projektu.

1. Zpátky **QuickDate** projekt, otevřete *Calendar.cs* souboru, pokud ještě není otevřený a přidejte následující [pomocí příkazu](/dotnet/csharp/language-reference/keywords/using-statement) a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut do horní části souboru, chcete-li vyřešit chybu v testovém projektu.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Soubor kódu by měl vypadat nějak takto:

   ![Kód CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Vlastnosti projektu

Na řádku *Calendar.cs* soubor, který obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut odkazuje na název sestavení (název souboru) **QuickTest** projektu. Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumníka řešení**, vyberte **QuickTest** projektu. V nabídce klepněte pravým tlačítkem nebo kontextu vyberte **vlastnosti**, nebo stačí stisknout kombinaci kláves **Alt**+**Enter**.

   *Stránky vlastností* pro projekt otevřít v **aplikace** kartu. Stránky vlastností obsahují různá nastavení pro projekt. Všimněte si, že název sestavení **QuickTest** projekt je skutečně "QuickTest". Pokud chcete změnit, toto je tam, kde by, která dělají. Potom, když sestavíte testovací projekt, název výsledný binární soubor změní z *QuickTest.dll* na cokoli, co jste zvolili.

   ![Vlastnosti projektu](media/tutorial-projects-properties.png)

1. Prozkoumejte některé z ostatních kartách stránky vlastností projektu, jako například **kompilaci** a **nastavení**. Tyto karty se liší pro různé typy projektů.

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
