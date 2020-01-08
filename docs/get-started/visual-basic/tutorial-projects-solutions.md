---
title: Výukové projekty a řešení Visual Basic
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48b3f2c9aae099e3ae5f2cf2d8c438fb0f9062a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590212"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Další informace o projektech a řešeních pomocí Visual Basic

V tomto článku úvodní podíváme, co to znamená, že k vytvoření *řešení* a *projektu* v sadě Visual Studio. Řešení je kontejner, který slouží k uspořádání jednoho nebo více souvisejících kódových projektů, například projektu knihovny tříd a odpovídajícího testovacího projektu. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Také vytvoříme odkaz z jednoho projektu do druhého.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

Jako vzdělávací cvičení porozumět koncepci projekt jsme vám vytvořit řešení a projektu od začátku. V obecné používání sady Visual Studio, budete pravděpodobně používat některé z různých projektů *šablony* , nabízí Visual Studio při vytvoření nového projektu.

> [!NOTE]
> Řešení a projekty není nutné pro vývoj aplikací v sadě Visual Studio. Můžete také pouze otevřít složku, která obsahuje kód a začít kódování, sestavování a ladění. Například, pokud naklonujete [Githubu](https://github.com/) úložiště, nemusí obsahovat řešení a projektů sady Visual Studio. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Bez ohledu na jeho název není řešení "Answer". Řešení je jednoduše kontejner používaný aplikací Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Když otevřete řešení v aplikaci Visual Studio, automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Naše zkoumání začneme vytvořením prázdné řešení. Po získání znát sady Visual Studio, které pravděpodobně nenajdete sami velmi často vytvoření prázdných řešení. Při vytváření nového projektu sady Visual Studio automaticky vytvoří řešení k umístění projektu, pokud existuje řešení ještě není otevřený.

::: moniker range="vs-2017"

1. Otevřít Visual Studio.

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

   **Nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte **ostatní typy projektů**, klikněte na tlačítko **řešení sady Visual Studio**. V prostředním podokně, vyberte **prázdné řešení** šablony. Pojmenujte své řešení **QuickSolution**a pak zvolte **OK**.

   ![Šablonu prázdného řešení v sadě Visual Studio](../media/tutorial-projects-new-solution.png)

   **Úvodní stránka** zavře a řešení se zobrazí v **Průzkumníka řešení** na pravé straně okna nástroje Visual Studio. Je pravděpodobně použijete **Průzkumníka řešení** často, procházet obsah vašich projektů.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **prázdné řešení** , vyberte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.

   ![Prázdná šablona řešení v aplikaci Visual Studio 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Pojmenujte řešení **QuickSolution**a pak zvolte **vytvořit**.

   Řešení se zobrazí v **Průzkumník řešení** na pravé straně okna aplikace Visual Studio. Je pravděpodobně použijete **Průzkumníka řešení** často, procházet obsah vašich projektů.

::: moniker-end

### <a name="add-a-project"></a>Přidat do projektu

Nyní Pojďme přidat naši první projekt do řešení. Začneme s prázdným projektem a přidejte položky, které potřebujeme do projektu.

::: moniker range="vs-2017"

1. V **Průzkumník řešení**klikněte pravým tlačítkem nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte **Přidat** > **Nový projekt**.

   **Přidat nový projekt** zobrazí se dialogové okno.

1. V levém podokně rozbalte položku **Visual Basic** a vyberte možnost **plocha systému Windows**. Potom v prostředním podokně, vyberte **prázdný projekt (.NET Framework)** šablony. Pojmenujte projekt **QuickDate**, klikněte na tlačítko **OK** tlačítko.

   Zobrazí se pod řešení v projektu s názvem QuickDate **Průzkumníka řešení**. Aktuálně obsahuje jediný soubor volané *App.config*.

   > [!NOTE]
   > Pokud nevidíte **Visual Basic** v levém podokně dialogového okna, je nutné nainstalovat *úlohu*aplikace **.NET Desktop Development** sady Visual Studio. Visual Studio používá pouze nainstalovat součásti, které potřebujete pro typ vývoje, které vám instalace na základě pracovního vytížení. Snadný způsob, jak nainstalovat nový pracovní postup je vybrat **otevřít instalační program Visual Studio** odkaz v levém dolním rohu **přidat nový projekt** dialogové okno. Až se spustí instalační program sady Visual Studio, zvolte **vývoj desktopových aplikací .NET** úlohy a pak **změnit** tlačítko.
   >
   > ![Otevřít odkaz instalační program sady Visual Studio](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení**klikněte pravým tlačítkem nebo v kontextové nabídce **řešení ' QuickSolution '** , vyberte **Přidat** > **Nový projekt**.

   Otevře se dialogové okno s informacemi **o přidání nového projektu**.

1. Do vyhledávacího pole v horní části zadejte text **Empty** a v části **jazyk**vyberte **Visual Basic** .

1. Vyberte šablonu **prázdného projektu (.NET Framework)** a klikněte na tlačítko **Další**.

1. Pojmenujte projekt **QuickDate**a pak zvolte **vytvořit**.

   Zobrazí se pod řešení v projektu s názvem QuickDate **Průzkumníka řešení**. Aktuálně obsahuje jediný soubor volané *App.config*.

   > [!NOTE]
   > Pokud nevidíte **prázdnou šablonu projektu (.NET Framework)** , je nutné nainstalovat *úlohu*aplikace **.NET Desktop Development** sady Visual Studio. Visual Studio používá pouze nainstalovat součásti, které potřebujete pro typ vývoje, které vám instalace na základě pracovního vytížení. Snadný způsob, jak nainstalovat novou úlohu při vytváření nového projektu, je odkaz pro **instalaci dalších nástrojů a funkcí** pod textem, který **nehledá, co hledáte?** . Až se spustí instalační program sady Visual Studio, zvolte **vývoj desktopových aplikací .NET** úlohy a pak **změnit** tlačítko.
   >
   > ![Odkaz instalační služby v aplikaci Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Prázdný projekt máme. Přidejme souboru kódu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **QuickDate** projekt **Průzkumníka řešení**, zvolte **přidat** > **novou položku** .

   **Přidat novou položku** zobrazí se dialogové okno.

1. Rozbalte položku **běžné položky**a pak zvolte možnost **kód**. V prostředním podokně vyberte **třídy** šablony položky. Název třídy **kalendáře**a klikněte na tlačítko **přidat** tlačítko.

   Do projektu se přidá soubor s názvem *Calendar. vb* . Přípona *. vb* na konci je přípona souboru, která je dána Visual Basic soubory kódu. Soubor se zobrazí v hierarchii Visual Project v **Průzkumník řešení**a jeho obsah je otevřen v editoru.

1. Obsah souboru *Calendar. vb* nahraďte následujícím kódem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Třída `Calendar` obsahuje jedinou funkci, `GetCurrentDate`, která vrací aktuální datum.

1. Otevřete vlastnosti projektu dvojitým kliknutím na **můj projekt** v **Průzkumník řešení**. Na kartě **aplikace** změňte **Typ aplikace** na **Knihovna tříd**. Tento krok je nezbytný k úspěšnému sestavení projektu.

1. Sestavte projekt kliknutím pravým tlačítkem na **QuickDate** v **Průzkumník řešení** a výběrem možnosti **sestavit**. V okně **výstup** by se měla zobrazit zpráva o úspěšném sestavení.

## <a name="add-a-second-project"></a>Přidáte druhý projekt

Je běžné, že řešení obsahují více než jeden projekt a často tyto projekty odkazují na sebe navzájem. Některé projekty v řešení může být knihoven tříd, některých aplikací spustitelných souborů a některé můžou být projektů testů jednotek nebo weby.

Přidejme do našich řešení projekt testování částí. Tentokrát začneme ze šablony projektu, nemáme k přidání dalšího kódu souboru do projektu.

1. Z nabídky klikněte pravým tlačítkem nebo kontext **řešení "QuickSolution"** v **Průzkumníka řešení**, zvolte **přidat** > **nový projekt**.

::: moniker range="Vs-2017"

2. V levém podokně rozbalte **jazyka Visual Basic** a zvolte **Test** kategorie. V prostředním podokně, vyberte **projekt testu jednotek (.NET Framework)** šablony projektu. Pojmenujte projekt **QuickTest**a klikněte na **tlačítko OK**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.vb* otevře v editoru.

   ![Průzkumník řešení Visual Studio se dva projekty](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V dialogovém okně **Přidat nový projekt** zadejte do pole Hledat v horní části **test textové jednotky** a v části **jazyk**vyberte **Visual Basic** .

3. Zvolte šablonu projektu **projekt testování částí (.NET Framework)** a klikněte na tlačítko **Další**.

4. Pojmenujte projekt **QuickTest**a pak zvolte **vytvořit**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.vb* otevře v editoru.

::: moniker-end

## <a name="add-a-project-reference"></a>Přidat odkaz na projekt

Chceme použít testovací projekt nové jednotky k otestování v metodě **QuickDate** projektu, takže je potřeba přidat odkaz na tento projekt. Tím se vytvoří *závislosti sestavení* mezi dva projekty, to znamená, že při sestavování řešení, **QuickDate** sestaveny dříve, než **QuickTest**.

1. Zvolte **odkazy** uzlu v **QuickTest** projektu a v nabídce klepněte pravým tlačítkem nebo kontextu zvolte **přidat odkaz**.

   ![Přidat odkaz na nabídku](media/tutorial-projects-add-reference-vb.png)

   **Správce odkazů** zobrazí se dialogové okno.

1. V levém podokně rozbalte **projekty** a zvolte **řešení**. V prostředním podokně zaškrtněte políčko vedle položky **QuickDate**a klikněte na tlačítko **OK** tlačítko.

   Odkaz na **QuickDate** projekt je přidán.

## <a name="add-test-code"></a>Přidat testovací kód

1. Teď přidáme testovací kód do souboru kódu jazyka Visual Basic. Nahraďte obsah *UnitTest1.vb* následujícím kódem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   V části kódu se zobrazí červená vlnovka. Opravíme tuto chybu tak, že projekt testů [sestavení typu friend](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) k **QuickDate** projektu.

1. Zpět v projektu **QuickDate** otevřete soubor *Calendar. vb* , pokud ještě není otevřený, a přidejte následující [příkaz Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) a atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pro vyřešení chyby v testovacím projektu.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Soubor kódu by měl vypadat nějak takto:

   ![Kód jazyka Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Vlastnosti projektu

Řádek v souboru *Calendar. vb* , který obsahuje atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> odkazuje na název sestavení (název souboru) projektu **QuickTest** . Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumníka řešení**, vyberte **QuickTest** projektu. V nabídce klepněte pravým tlačítkem nebo kontextu vyberte **vlastnosti**, nebo stačí stisknout kombinaci kláves **Alt**+**Enter**. (Můžete také dvakrát kliknout na **projekt** v **Průzkumník řešení**.)

   *Stránky vlastností* projektu otevřené na kartě **aplikace** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení **QuickTest** projekt je skutečně "QuickTest". Pokud chcete změnit, toto je tam, kde by, která dělají. Potom, když sestavíte testovací projekt, název výsledný binární soubor změní z *QuickTest.dll* na cokoli, co jste zvolili.

   ![Vlastnosti projektu](../media/tutorial-projects-properties.png)

1. Prozkoumejte některé z ostatních kartách stránky vlastností projektu, jako například **kompilaci** a **nastavení**. Tyto karty se liší pro různé typy projektů.

## <a name="optional-run-the-test"></a>Volitelné Spustit test

Pokud chcete zkontrolovat, že je funkční testování částí, zvolte **testování** > **spustit** > **všechny testy** z řádku nabídek. Zobrazí se okno **Průzkumníka testů** otevře a měli byste vidět, který **TestGetCurrentDate** testovací průchody.

![Průzkumník textu v aplikaci Visual Studio zobrazující úspěšný test](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Pokud **Průzkumník testů** nebude automaticky otevřené, otevřete ho kliknutím **testovací** > **Windows** > **Průzkumník testů** z řádku nabídek.

## <a name="next-steps"></a>Další kroky

Pokud chcete dále prozkoumat sadu Visual Studio, zvažte vytvoření aplikace pomocí jednoho z [kurzů Visual Basic](index.yml).

## <a name="see-also"></a>Viz také:

- [Vytváření projektů a řešení](../../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE – přehled](../../get-started/visual-studio-ide.md)
