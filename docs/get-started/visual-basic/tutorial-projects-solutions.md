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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75590212"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Informace o projektech a řešeních pomocí jazyka Visual Basic

V tomto úvodním článku se podíváme, co to znamená vytvořit *řešení* a *projekt* v sadě Visual Studio. Řešení je kontejner, který se používá k uspořádání jednoho nebo více souvisejících projektů kódu, například projekt knihovny tříd a odpovídající testovací projekt. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Vytvoříme také odkaz z jednoho projektu do druhého.

::: moniker range="vs-2017"

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

Vytvoříme řešení a projekt od nuly jako vzdělávací cvičení, abychom pochopili koncept projektu. Při obecném použití sady Visual Studio budete pravděpodobně používat některé různé *šablony* projektů, které visual studio nabízí při vytváření nového projektu.

> [!NOTE]
> Řešení a projekty nejsou nutné k vývoji aplikací v sadě Visual Studio. Můžete také otevřít složku, která obsahuje kód a začít kódování, vytváření a ladění. Například pokud klonovat úložiště [GitHub,](https://github.com/) nemusí obsahovat projekty a řešení sady Visual Studio. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Navzdory svému názvu není řešení "odpovědí". Řešení je jednoduše kontejner používaný aplikací Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Při otevření řešení v sadě Visual Studio automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Začneme náš průzkum vytvořením prázdného řešení. Po seznámení s Visual Studio, pravděpodobně nenajdete sami vytvářet prázdná řešení velmi často. Při vytváření nového projektu Visual Studio automaticky vytvoří řešení pro dům projektu, pokud není řešení již otevřené.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

   Otevře se dialogové okno **Nový projekt.**

1. V levém podokně rozbalte **položku Jiné typy projektů**a pak zvolte **Řešení sady Visual Studio**. V prostředním podokně zvolte šablonu **Prázdné řešení.** Pojmenujte řešení **QuickSolution**a pak zvolte **OK**.

   ![Prázdná šablona řešení v sadě Visual Studio](../media/tutorial-projects-new-solution.png)

   Úvodní **stránka** se zavře a řešení se zobrazí v **Průzkumníku řešení** na pravé straně okna sady Visual Studio. Pravděpodobně budete často používat **Průzkumníka řešení** k procházení obsahu vašich projektů.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Na stránce **Vytvořit nový projekt** zadejte do vyhledávacího pole prázdné **řešení,** vyberte šablonu **Prázdné řešení** a pak zvolte **Další**.

   ![Šablona Prázdné řešení ve Visual Studiu 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Pojmenujte řešení **QuickSolution**a pak zvolte **Vytvořit**.

   Řešení se zobrazí v **Průzkumníku řešení** na pravé straně okna sady Visual Studio. Pravděpodobně budete často používat **Průzkumníka řešení** k procházení obsahu vašich projektů.

::: moniker-end

### <a name="add-a-project"></a>Přidání projektu

Nyní přidáme náš první projekt k řešení. Začneme s prázdným projektem a přidáme položky, které potřebujeme k projektu.

::: moniker range="vs-2017"

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

   Otevře se dialogové okno **Přidat nový projekt.**

1. V levém podokně rozbalte **položku Visual Basic** a zvolte **plochu systému Windows**. Potom v prostředním podokně zvolte šablonu **Prázdný projekt (.NET Framework).** Pojmenujte projekt **QuickDate**a zvolte tlačítko **OK.**

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumníku řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud v levém podokně dialogového okna nevidíte **visual basic,** je třeba nainstalovat *úlohu*visual studia **pro vývoj plochy .NET** . Visual Studio používá instalaci založenou na úlohách k instalaci pouze součástí, které potřebujete pro typ vývoje, který děláte. Snadný způsob instalace novéúlohy je zvolit odkaz Otevřít instalační program **sady Visual Studio** v levém dolním rohu dialogového okna Přidat nový **projekt.** Po spuštění Instalační služby sady Visual Studio zvolte **úlohu vývoje plochy .NET** a potom tlačítko **Změnit.**
   >
   > ![Otevřít odkaz Instalační služby sady Visual Studio](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

   Otevře se dialogové okno s **nápisem Přidat nový projekt**.

1. V horní části zadejte **prázdný** text do vyhledávacího pole a v části **Jazyk**vyberte **Položku Visual Basic** .

1. Vyberte šablonu **Prázdný projekt (.NET Framework)** a pak zvolte **Další**.

1. Pojmenujte projekt **QuickDate**a pak zvolte **Vytvořit**.

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumníku řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud šablonu Prázdný **projekt (.NET Framework)** nevidíte, je třeba nainstalovat *úlohu*visual studia **pro vývoj desktopů .NET** . Visual Studio používá instalaci založenou na úlohách k instalaci pouze součástí, které potřebujete pro typ vývoje, který děláte. Snadný způsob, jak nainstalovat nové pracovní zatížení při vytváření nového projektu, je vybrat odkaz **Instalovat další nástroje a funkce** pod textem, který říká **Nenajít to, co hledáte?**. Po spuštění Instalační služby sady Visual Studio zvolte **úlohu vývoje plochy .NET** a potom tlačítko **Změnit.**
   >
   > ![Odkaz instalačního programu ve Visual Studiu 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Máme prázdný projekt. Přidáme soubor kódu.

1. V nabídce pravým tlačítkem nebo v místní nabídce projektu **QuickDate** v **Průzkumníku řešení**zvolte **Přidat** > **novou položku**.

   Otevře se dialogové okno **Přidat novou položku.**

1. Rozbalte **položky společné položky**a pak zvolte **Kód**. Ve středním podokně zvolte šablonu **položky třídy.** Pojmenujte **kalendář**třídy a pak zvolte tlačítko **Přidat.**

   Do projektu je přidán soubor s názvem *Calendar.vb.* *.vb* na konci je přípona souboru, který je uveden do souborů kódu jazyka. Soubor se zobrazí v hierarchii vizuálního projektu v **Průzkumníku řešení**a jeho obsah se otevře v editoru.

1. Nahraďte obsah souboru *Calendar.vb* následujícím kódem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Třída `Calendar` obsahuje jednu `GetCurrentDate`funkci , která vrací aktuální datum.

1. Otevřete vlastnosti projektu poklepáním na **můj projekt** v **Průzkumníku řešení**. Na kartě **Aplikace** změňte **typ aplikace** na **Knihovnu tříd**. Tento krok je nezbytné k úspěšnému sestavení projektu.

1. Sestavte projekt kliknutím pravým tlačítkem myši na **QuickDate** v **Průzkumníku řešení** a výběrem **možnosti Sestavení**. V okně **Výstup** by se měla zobrazit zpráva o úspěšném sestavení.

## <a name="add-a-second-project"></a>Přidání druhého projektu

Je běžné, že řešení obsahují více než jeden projekt a často tyto projekty odkazují na sebe navzájem. Některé projekty v řešení mohou být knihovny tříd, některé spustitelné aplikace a některé mohou být projekty testování částí nebo weby.

Přidáme projekt testování částí do našeho řešení. Tentokrát začneme od šablony projektu, takže nemusíme do projektu přidávat další soubor kódu.

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

::: moniker range="Vs-2017"

2. V levém podokně rozbalte **položku Visual Basic** a zvolte kategorii **Test.** V prostředním podokně zvolte šablonu projektu **Projekt testování částí (.NET Framework).** Pojmenujte projekt **QuickTest**a pak zvolte **OK**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.vb* otevře v editoru.

   ![Průzkumník řešení Visual Studio se dvěma projekty](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V **dialogovém** okně Přidat nový projekt zadejte test textové **jednotky** do vyhledávacího pole v horní části a pak vyberte **Jazyk v** části **Jazyk**.

3. Zvolte šablonu **projektu Projekt testování částí (.NET Framework)** a pak zvolte **Další**.

4. Pojmenujte projekt **QuickTest**a pak zvolte **Vytvořit**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.vb* otevře v editoru.

::: moniker-end

## <a name="add-a-project-reference"></a>Přidání odkazu na projekt

Budeme používat nový projekt testování částí k testování naší metody v projektu **QuickDate,** takže musíme přidat odkaz na tento projekt. Tím se vytvoří závislost sestavení mezi *dvěma projekty,* což znamená, že při vytváření řešení **QuickDate** je postaven před **QuickTest**.

1. Zvolte uzel **Odkazy** v projektu **QuickTest** a z nabídky pravým tlačítkem nebo kontextové nabídky zvolte **Přidat odkaz**.

   ![Nabídka Přidat odkaz](media/tutorial-projects-add-reference-vb.png)

   Otevře se dialogové okno **Správce odkazů.**

1. V levém podokně rozbalte **položku Projekty** a zvolte **Řešení**. V prostředním podokně zaškrtněte políčko vedle **QuickDate**a pak zvolte tlačítko **OK.**

   Je přidán odkaz na projekt **QuickDate.**

## <a name="add-test-code"></a>Přidat testovací kód

1. Teď přidáme testovací kód do souboru kódu jazyka Visual Basic. Nahraďte obsah *UnitTest1.vb* následujícím kódem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Pod některým kódem uvidíte červenou vlnovku. Tuto chybu opravíme tak, že testovací projekt bude [sestavením přítele](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) do projektu **QuickDate.**

1. Zpět v projektu **QuickDate** otevřete soubor *Calendar.vb,* pokud ještě není otevřený, a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> přidejte následující [příkaz importu](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) a atribut, abyste vyřešili chybu v testovacím projektu.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Soubor kódu by měl vypadat takto:

   ![Kód jazyka Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Vlastnosti projektu

Řádek v souboru *Calendar.vb,* který obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut odkazuje na název sestavení (název souboru) projektu **QuickTest.** Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumníku řešení**vyberte projekt **QuickTest.** V nabídce pravým tlačítkem nebo v místní nabídce vyberte **Vlastnosti**nebo stiskněte **klávesu Alt**+**Enter**. (Můžete také poklepat na **můj projekt** v **Průzkumníku řešení**.)

   *Stránky vlastností* projektu se otevřou na kartě **Aplikace.** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení projektu **QuickTest** je skutečně "QuickTest". Kdybys to chtěl změnit, udělal bys to tady. Potom při vytváření testovacího projektu, název výsledného binárního souboru by změnit z *QuickTest.dll* na cokoliv, co jste zvolili.

   ![Vlastnosti projektu](../media/tutorial-projects-properties.png)

1. Prozkoumejte některé další karty stránek vlastností projektu, například **Kompilace** a **Nastavení**. Tyto karty se liší pro různé typy projektů.

## <a name="optional-run-the-test"></a>(Nepovinné) Spuštění testu

Pokud chcete zkontrolovat, zda test částí funguje, zvolte **Testovat** > **spustit** > **všechny testy** z řádku nabídek. Otevře se okno s názvem **Průzkumník testů** a měli byste vidět, že test **TestGetCurrentDate** projde.

![Průzkumník textu v sadě Visual Studio zobrazující předjetý test](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Pokud **se Průzkumník testů** neotevře automaticky, otevřete ho tak, že z řádku nabídek zvolíte **Testovat** > **Průzkumníka testů** **systému Windows.** > 

## <a name="next-steps"></a>Další kroky

Pokud chcete další prozkoumání sady Visual Studio, zvažte vytvoření aplikace podle jednoho z [kurzů jazyka Visual Basic](index.yml).

## <a name="see-also"></a>Viz také

- [Vytváření projektů a řešení](../../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Přehled ide sady Visual Studio](../../get-started/visual-studio-ide.md)
