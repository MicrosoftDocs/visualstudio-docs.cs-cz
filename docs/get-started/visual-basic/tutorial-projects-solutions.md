---
title: Výukové projekty a řešení Visual Basic
description: Zjistěte, jak vytvořit řešení a projekt v Visual Studio jako Visual Basic vývojáře.
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4f27973fcfb76d019cff31787b117f05f8266ad8
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308178"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Další informace o projektech a řešeních s využitím Visual Basic

V tomto úvodním článku prozkoumáme, co znamená vytvoření řešení *a* projektu *v* Visual Studio. Řešení je kontejner, který slouží k uspořádání jednoho nebo více souvisejících projektů kódu, například projektu knihovny tříd a odpovídajícího projektu testů. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Vytvoříme také odkaz z jednoho projektu na jiný.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Pokud jste si ještě nenainstalujete Visual Studio Preview, nainstalujte si ho zdarma na [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) downloads.

::: moniker-end

Jako vzdělávací cvičení vytvoříme řešení a projekt od začátku, abyste porozuměli konceptu projektu. Při obecném používání Visual Studio pravděpodobně při vytváření nového projektu použijete některé z různých šablon projektů, které Visual Studio nabízí. 

> [!NOTE]
> Řešení a projekty nejsou nutné k vývoji aplikací v Visual Studio. Můžete také otevřít složku, která obsahuje kód a začít kódovat, sestavování a ladění. Pokud například naklonujete [úložiště GitHub,](https://github.com/) nemusí obsahovat Visual Studio a řešení. Další informace najdete v tématu [Vývoj kódu v Visual Studio bez projektů nebo řešení.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Řešení a projekty

Řešení navzdory svému názvu není "odpovědí". Řešení je jednoduše kontejner, který používá Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Když otevřete řešení v Visual Studio, automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Začneme tím, že vytvoříme prázdné řešení. Jakmile se s Visual Studio, pravděpodobně nebudete příliš často vytvářet prázdná řešení. Když vytvoříte nový projekt, Visual Studio automaticky vytvoří řešení pro jeho vytvoření, pokud ještě není řešení otevřené.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek zvolte File New Project **(Soubor** > **nový** > **projekt).**

   Otevře **se dialogové okno** Nový projekt.

1. V levém podokně rozbalte **Ostatní typy projektů** a pak zvolte Visual Studio **řešení.** V podokně uprostřed zvolte šablonu **Prázdné** řešení. Pojmechte **řešení QuickSolution** a pak zvolte **OK.**

   ![Prázdná šablona řešení v Visual Studio](../media/tutorial-projects-new-solution.png)

   Úvodní **stránka se** zavře a v Průzkumník řešení na pravé straně okna Visual Studio řešení.  K procházení obsahu **Průzkumník řešení** budete pravděpodobně často používat .

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V úvodním okně zvolte **Vytvořit nový projekt.**

3. Na **stránce Vytvořit nový projekt** zadejte do **vyhledávacího** pole prázdné řešení, vyberte šablonu **Prázdné** řešení a pak zvolte **Další.**

   ![Prázdná šablona řešení v Visual Studio 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Pojmechte **řešení QuickSolution** a pak zvolte **Vytvořit.**

   Řešení se **Průzkumník řešení** na pravé straně okna Visual Studio zobrazení. K procházení obsahu **Průzkumník řešení** budete pravděpodobně často používat .

::: moniker-end

### <a name="add-a-project"></a>Přidání projektu

Teď do řešení přidáme náš první projekt. Začneme s prázdným projektem a přidáme do projektu položky, které potřebujeme.

::: moniker range="vs-2017"

1. V místní nabídce nebo kliknutí pravým tlačítkem **řešení QuickSolution** v **Průzkumník řešení** **přidat** > **nový projekt**.

   Otevře **se dialogové okno Přidat** nový projekt.

1. V levém podokně rozbalte položku **Visual Basic** a zvolte **Windows Desktop.** Potom v prostředním podokně zvolte šablonu **Prázdný projekt (.NET Framework).** Pojmete **projekt QuickDate** a pak zvolte **tlačítko OK.**

   Projekt QuickDate se zobrazí pod řešením v Průzkumník řešení **.** V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud v levém podokně dialogového **Visual Basic** nevidíte , musíte si nainstalovat úlohu vývoj desktopových aplikací **pro .NET** Visual Studio *.* Visual Studio pomocí instalace založené na úlohách instaluje jenom komponenty, které potřebujete pro typ vývoje. Snadným způsobem, jak nainstalovat novou úlohu, je zvolit odkaz Otevřít **Instalační program pro Visual Studio** v levém dolním rohu dialogového okna Přidat **nový** projekt. Po Instalační program pro Visual Studio počítače zvolte úlohu **Vývoj desktopových** aplikací .NET a pak **tlačítko** Upravit.
   >
   > ![Otevření Instalační program pro Visual Studio odkazu](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. V místní nabídce nebo kliknutí pravým tlačítkem **řešení QuickSolution** v **Průzkumník řešení** **přidat** > **nový projekt**.

   Otevře se dialogové okno s **textem Add a new project (Přidat nový projekt).**

1. Do **vyhledávacího pole** v horní části zadejte prázdný text a pak vyberte **Visual Basic** v části **Jazyk**.

1. Vyberte šablonu **Prázdný projekt (.NET Framework)** a pak zvolte **Další.**

1. Pojmechte **projekt QuickDate** a pak **zvolte Vytvořit.**

   Projekt QuickDate se zobrazí pod řešením v Průzkumník řešení **.** V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud nevidíte šablonu **Prázdný projekt (.NET Framework),** musíte si nainstalovat úlohu vývoj desktopových aplikací **pro .NET** Visual Studio *.* Visual Studio pomocí instalace založené na úlohách instaluje jenom komponenty, které potřebujete pro typ vývoje. Snadným způsobem, jak nainstalovat novou úlohu při vytváření nového  projektu, je zvolit odkaz Nainstalovat další nástroje a funkce pod textem, který říká, že nehledáte to, co **hledáte?**. Po Instalační program pro Visual Studio počítače zvolte úlohu **Vývoj desktopových** aplikací .NET a pak **tlačítko** Upravit.
   >
   > ![Odkaz na instalační program Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Máme prázdný projekt. Pojďme přidat soubor kódu.

1. V místní nabídce nebo kliknutí pravým tlačítkem projektu **QuickDate** **v Průzkumník řešení** **vyberte Přidat**  >  **novou položku.**

   Otevře **se dialogové okno Přidat** novou položku.

1. Rozbalte **položku Běžné** položky a pak zvolte **Kód.** V prostředním podokně zvolte **šablonu Položka** třídy. Pojmete **třídu Calendar** a pak zvolte **tlačítko** Přidat.

   Do projektu se *přidá soubor Calendar.vb.* .vb *na* konci je přípona souboru, která má Visual Basic kódu. Soubor se zobrazí v hierarchii projektu vizuálu **v Průzkumník řešení** a jeho obsah se otevře v editoru.

1. Obsah souboru *Calendar.vb nahraďte* následujícím kódem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Třída `Calendar` obsahuje jednu funkci , která vrací aktuální `GetCurrentDate` datum.

1. Otevřete vlastnosti projektu dvojím kliknutím na **Můj projekt v** **Průzkumník řešení**. Na kartě **Aplikace** změňte **Typ aplikace na** Knihovna **tříd**. Tento krok je nezbytný pro úspěšné sestavení projektu.

1. Sestavte projekt tak, že pravým tlačítkem myši kliknete **na** **QuickDate** Průzkumník řešení a zvolíte **Build (Sestavit).** V okně Výstup by se měla zobrazit zpráva o **úspěšném** sestavení.

## <a name="add-a-second-project"></a>Přidání druhého projektu

Řešení běžně obsahují více než jeden projekt a tyto projekty se často vzájemně odkazují. Některé projekty v řešení můžou být knihovny tříd, některé spustitelné aplikace a některé mohou být projekty testů jednotek nebo weby.

Pojďme do našeho řešení přidat projekt testování částí. Tentokrát začneme ze šablony projektu, abychom do projektu nemusíme přidávat další soubor kódu.

1. V místní nabídce nebo kliknutí pravým tlačítkem **řešení QuickSolution** v **Průzkumník řešení** **přidat**  >  **nový projekt**.

::: moniker range="Vs-2017"

2. V levém podokně rozbalte **Visual Basic** a zvolte **kategorii Test.** V prostředním podokně zvolte šablonu projektu Projekt testu jednotek **(.NET Framework).** Pojmechte **projekt QuickTest** a pak zvolte **OK**.

   Do souboru se přidá **druhý Průzkumník řešení** a v editoru se otevře soubor *UnitTest1.vb.*

   ![Visual Studio Průzkumník řešení se dvěma projekty](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V dialogovém **okně Přidat nový** projekt zadejte do vyhledávacího pole v horní části text unit **test** a pak v části **Language (Jazyk) Visual Basic** ( **Jazyk).**

3. Zvolte šablonu projektu Projektu testů **jednotek (.NET Framework)** a pak zvolte **Další.**

4. Pojmechte **projekt QuickTest** a pak zvolte **Vytvořit.**

   Do souboru se přidá **druhý Průzkumník řešení** a v editoru se otevře soubor *UnitTest1.vb.*

::: moniker-end

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Použijeme nový projekt testování částí k otestování naší metody v projektu **QuickDate** , takže musíme přidat odkaz na tento projekt. Tím se vytvoří *závislost sestavení* mezi dvěma projekty, což znamená, že při sestavování řešení je **QuickDate** sestaven před **QuickTest**.

1. Vyberte uzel **odkazy** v projektu **QuickTest** a v místní nabídce klikněte pravým tlačítkem myši nebo vyberte možnost **Přidat odkaz**.

   ![Přidat odkazovou nabídku](media/tutorial-projects-add-reference-vb.png)

   Otevře se dialogové okno **Správce odkazů** .

1. V levém podokně rozbalte položku **projekty** a klikněte na možnost **řešení**. V prostředním podokně klikněte na zaškrtávací políčko vedle **QuickDate** a pak klikněte na tlačítko **OK** .

   Přidá se odkaz na projekt **QuickDate** .

## <a name="add-test-code"></a>Přidat testovací kód

1. Nyní přidáme testovací kód do souboru kódu Visual Basic. Obsah *UnitTest1. vb* nahraďte následujícím kódem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   V části kódu se zobrazí červená vlnovka. Tuto chybu vyřešíme tak, že projekt testů vytvoří pro projekt **QuickDate** [sestavení typu Friend](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) .

1. Zpět v projektu **QuickDate** otevřete soubor *Calendar. vb* , pokud ještě není otevřený, a přidejte následující [příkaz Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut pro vyřešení chyby v testovacím projektu.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Soubor kódu by měl vypadat takto:

   ![Kód jazyka Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Vlastnosti projektu

Řádek v souboru *Calendar. vb* , který obsahuje atribut, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> odkazuje na název sestavení (název souboru) projektu **QuickTest** . Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumník řešení** vyberte projekt **QuickTest** . V místní nabídce klepněte pravým tlačítkem myši nebo vyberte možnost **vlastnosti**, nebo stačí stisknout klávesu **ALT** + **ENTER**. (Můžete také dvakrát kliknout na **projekt** v **Průzkumník řešení**.)

   *Stránky vlastností* projektu otevřené na kartě **aplikace** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení projektu **QuickTest** je skutečně "QuickTest". Pokud jste ho chtěli změnit, je to místo, kde to uděláte. Při sestavování testovacího projektu se pak název výsledného binárního souboru změní z *QuickTest.dll* na cokoliv, co jste zvolili.

   ![Vlastnosti projektu](../media/tutorial-projects-properties.png)

1. Prozkoumejte některé z ostatních karet na stránkách vlastností projektu, jako je například **kompilace** a **Nastavení**. Tyto karty jsou odlišné pro různé typy projektů.

## <a name="optional-run-the-test"></a>Volitelné Spustit test

Chcete-li zkontrolovat, zda je test jednotky funkční, vyberte možnost **test**  >  **Spustit**  >  **všechny testy** z řádku nabídek. Otevře se okno s názvem **Průzkumník testů** , které by mělo vidět, že test **TestGetCurrentDate** projde.

![Průzkumník textu v aplikaci Visual Studio zobrazující úspěšný test](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Pokud se **Průzkumník testů** neotevře automaticky, otevřete ho výběrem příkazu **test**  >  **Windows**  >  **Test Explorer** z řádku nabídek.

## <a name="next-steps"></a>Další kroky

Pokud chcete dále prozkoumat sadu Visual Studio, zvažte vytvoření aplikace pomocí jednoho z [kurzů Visual Basic](index.yml).

## <a name="see-also"></a>Viz také

- [Vytváření projektů a řešení](../../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Přehled integrovaného vývojového prostředí sady Visual Studio](../../get-started/visual-studio-ide.md)
