---
title: Úvod do projektů a řešení
ms.date: 02/24/2020
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da2fc196f687e2335933794a578f507dafbc6de3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579973"
---
# <a name="learn-about-projects-and-solutions"></a>Další informace o projektech a řešeních

V tomto úvodním článku se podíváme, co to znamená vytvořit *řešení* a *projekt* v sadě Visual Studio. Řešení je kontejner, který se používá k uspořádání jednoho nebo více souvisejících projektů kódu, například projekt knihovny tříd a odpovídající testovací projekt. Podíváme se na vlastnosti projektu a některé soubory, které může obsahovat. Vytvoříme také odkaz z jednoho projektu do druhého.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

Vytvoříme řešení a projekt od nuly jako vzdělávací cvičení, abychom pochopili koncept projektu. Při obecném použití sady Visual Studio budete pravděpodobně používat některé různé *šablony* projektů, které visual studio nabízí při vytváření nového projektu.

> [!NOTE]
> Řešení a projekty nejsou nutné k vývoji aplikací v sadě Visual Studio. Můžete také otevřít složku, která obsahuje kód a začít kódování, vytváření a ladění. Například pokud klonovat úložiště [GitHub,](https://github.com/) nemusí obsahovat projekty a řešení sady Visual Studio. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Řešení a projekty

Navzdory svému názvu není řešení "odpovědí". Řešení je jednoduše kontejner používaný aplikací Visual Studio k uspořádání jednoho nebo více souvisejících projektů. Při otevření řešení v sadě Visual Studio automaticky načte všechny projekty, které řešení obsahuje.

### <a name="create-a-solution"></a>Vytvoření řešení

Začneme náš průzkum vytvořením prázdného řešení. Po seznámení s Visual Studio, pravděpodobně nenajdete sami vytvářet prázdná řešení velmi často. Při vytváření nového projektu Visual Studio automaticky vytvoří řešení pro dům projektu, pokud není řešení již otevřené.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

   Otevře se dialogové okno **Nový projekt.**

1. V levém podokně rozbalte **položku Jiné typy projektů**a pak zvolte **Řešení sady Visual Studio**. V prostředním podokně zvolte šablonu **Prázdné řešení.** Pojmenujte své řešení **QuickSolution**a zvolte tlačítko **OK.**

   ![Prázdná šablona řešení v Sadě Visual Studio 2017](media/tutorial-projects-new-solution.png)

   Úvodní **stránka** se zavře a řešení se zobrazí v **Průzkumníku řešení** na pravé straně okna sady Visual Studio. Pravděpodobně budete často používat **Průzkumníka řešení** k procházení obsahu vašich projektů.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Na stránce **Vytvořit nový projekt** zadejte do vyhledávacího pole prázdné **řešení,** vyberte šablonu **Prázdné řešení** a pak zvolte **Další**.

   ![Šablona Prázdné řešení ve Visual Studiu 2019](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Pojmenujte řešení **QuickSolution**a pak zvolte **Vytvořit**.

   Řešení se zobrazí v **Průzkumníku řešení** na pravé straně okna sady Visual Studio. Pravděpodobně budete často používat **Průzkumníka řešení** k procházení obsahu vašich projektů.

::: moniker-end

### <a name="add-a-project"></a>Přidání projektu

Nyní přidáme náš první projekt k řešení. Začneme s prázdným projektem a přidáme položky, které potřebujeme k projektu.

::: moniker range="vs-2017"

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

   Otevře se dialogové okno **Přidat nový projekt.**

1. V levém podokně rozbalte **visual c#** a zvolte **Plochu systému Windows**. Potom v prostředním podokně zvolte šablonu **Prázdný projekt (.NET Framework).** Pojmenujte projekt **QuickDate**a pak zvolte **OK**.

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumníku řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud visual **c#** nevidíte v levém podokně dialogového okna, je nutné nainstalovat úlohu **vývoje plochy .NET** Visual Studio. Visual Studio používá instalaci založenou na úlohách k instalaci pouze součástí, které potřebujete pro typ vývoje, který děláte. Snadný způsob instalace novéúlohy je zvolit odkaz Otevřít instalační program **sady Visual Studio** v levém dolním rohu dialogového okna Přidat nový **projekt.** Po spuštění Instalační služby sady Visual Studio zvolte **úlohu vývoje plochy .NET** a potom tlačítko **Změnit.**
   >
   > ![Otevřít odkaz Instalační služby sady Visual Studio](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

   Otevře se dialogové okno s **nápisem Přidat nový projekt**.

1. V horní části zadejte **prázdný** text do vyhledávacího pole a v části **Jazyk**vyberte **C#** .

1. Vyberte šablonu **Prázdný projekt (.NET Framework)** a pak zvolte **Další**.

1. Pojmenujte projekt **QuickDate**a pak zvolte **Vytvořit**.

   Projekt s názvem QuickDate se zobrazí pod řešením v **Průzkumníku řešení**. V současné době obsahuje jeden soubor s názvem *App.config*.

   > [!NOTE]
   > Pokud nevidíte šablonu **Prázdný projekt (.NET Framework),** musíte nainstalovat úlohu visual studia **pro vývoj desktopů .NET.** Visual Studio používá instalaci založenou na úlohách k instalaci pouze součástí, které potřebujete pro typ vývoje, který děláte. Snadný způsob, jak nainstalovat nové pracovní zatížení při vytváření nového projektu, je vybrat odkaz **Instalovat další nástroje a funkce** pod textem, který říká **Nenajít to, co hledáte?**. Po spuštění Instalační služby sady Visual Studio zvolte **úlohu vývoje plochy .NET** a potom tlačítko **Změnit.**
   >
   > ![Otevřít odkaz Instalační služby sady Visual Studio](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Přidání položky do projektu

Máme prázdný projekt. Přidáme soubor kódu.

1. V nabídce pravým tlačítkem nebo v místní nabídce projektu **QuickDate** v **Průzkumníku řešení**zvolte **Přidat** > **novou položku**.

   Otevře se dialogové okno **Přidat novou položku.**

1. Rozbalte **položky Visual C# a**pak zvolte **Kód**. Ve středním podokně zvolte šablonu **položky třídy.** Pojmenujte **kalendář**třídy a pak zvolte tlačítko **Přidat.**

   Do projektu je přidán soubor s názvem *Calendar.cs.* *.cs* na konci je přípona souboru, který je dán souborům kódu C#. Soubor se zobrazí v hierarchii vizuálního projektu v **Průzkumníku řešení**a jeho obsah se otevře v editoru.

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

   Nemusíte pochopit, co kód dělá, ale pokud chcete, můžete spustit program stisknutím **ctrl**+**F5** a uvidíte, že vytiskne dnešní datum do okna konzoly (nebo standardní výstup).

## <a name="add-a-second-project"></a>Přidání druhého projektu

Je běžné, že řešení obsahují více než jeden projekt a často tyto projekty odkazují na sebe navzájem. Některé projekty v řešení mohou být knihovny tříd, některé spustitelné aplikace a některé mohou být projekty testování částí nebo weby.

Přidáme projekt testování částí do našeho řešení. Tentokrát začneme od šablony projektu, takže nemusíme do projektu přidávat další soubor kódu.

1. V nabídce řešení QuickSolution v **Průzkumníku řešení**nebo v kontextové nabídce **položky Řešení** zvolte **Přidat** > **nový projekt**.

::: moniker range="vs-2017"

2. V levém podokně rozbalte **visual c#** a zvolte kategorii **Test.** V prostředním podokně zvolte šablonu projektu **Testovací projekt MSTest (.NET Core).** Pojmenujte projekt **QuickTest**a pak zvolte **OK**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.cs* otevře v editoru.

   ![Průzkumník řešení Visual Studio se dvěma projekty](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. V **dialogovém** okně Přidat nový projekt zadejte test textové **jednotky** do vyhledávacího pole v horní části a v části **Jazyk**vyberte **C#** .

3. Zvolte šablonu projektu **Testovací projekt MSTest (.NET Core)** a pak zvolte **Další**.

4. Pojmenujte projekt **QuickTest**a pak zvolte **Vytvořit**.

   Druhý projekt je přidán do **Průzkumníka řešení**a soubor s názvem *UnitTest1.cs* otevře v editoru.

   ![Průzkumník řešení Visual Studio se dvěma projekty](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Přidání odkazu na projekt

Budeme používat nový projekt testování částí k testování naší metody v projektu **QuickDate,** takže musíme přidat odkaz na tento projekt. Tím se vytvoří závislost sestavení mezi *dvěma projekty,* což znamená, že při vytváření řešení **QuickDate** je postaven před **QuickTest**.

1. Zvolte uzel **Závislosti** v projektu **QuickTest** a z nabídky pravým tlačítkem nebo kontextové nabídky zvolte **Přidat odkaz**.

   Otevře se dialogové okno **Správce odkazů.**

1. V levém podokně rozbalte **položku Projekty** a zvolte **Řešení**. V prostředním podokně zaškrtněte políčko vedle **quickdate**a pak zvolte **OK**.

   Je přidán odkaz na projekt **QuickDate.**

   ![Průzkumník řešení Visual Studia 2019 s odkazem na projekt](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Přidat testovací kód

1. Nyní přidáme testovací kód do souboru testovacího kódu Jazyka C#. Nahraďte obsah *UnitTest1.cs* následujícím kódem:

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

   Pod některým kódem uvidíte červenou vlnovku. Tuto chybu opravíme tak, že testovací projekt bude [sestavením přítele](/dotnet/standard/assembly/friend-assemblies) do projektu **QuickDate.**

1. V projektu **QuickDate** otevřete soubor *Calendar.cs,* pokud ještě není otevřený. Přidejte následující using <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> [příkaz](/dotnet/csharp/language-reference/keywords/using-statement) a atribut do horní části souboru k vyřešení chyby v testovacím projektu.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Soubor kódu by měl vypadat takto:

   ![Kód CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Vlastnosti projektu

Řádek v *souboru Calendar.cs,* který obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut odkazuje na název sestavení (název souboru) projektu **QuickTest.** Název sestavení nemusí být vždy stejný jako název projektu. Chcete-li najít název sestavení projektu, otevřete vlastnosti projektu.

1. V **Průzkumníku řešení**vyberte projekt **QuickTest.** V nabídce pravým tlačítkem nebo v místní nabídce vyberte **Vlastnosti**nebo stiskněte **klávesu Alt**+**Enter**.

   *Stránky vlastností* projektu se otevřou na kartě **Aplikace.** Stránky vlastností obsahují různá nastavení projektu. Všimněte si, že název sestavení projektu **QuickTest** je skutečně "QuickTest". Kdybys to chtěl změnit, udělal bys to tady. Potom při vytváření testovacího projektu, název výsledného binárního souboru by změnit z *QuickTest.dll* na cokoliv, co jste zvolili.

   ![Vlastnosti projektu](media/tutorial-projects-netcore-properties.png)

1. Prozkoumejte některé další karty stránek vlastností projektu, například **Sestavení** a **ladění**. Tyto karty se liší pro různé typy projektů.

## <a name="next-steps"></a>Další kroky

Pokud chcete zkontrolovat, zda test částí funguje, zvolte **Testovat** > **spustit** > **všechny testy** z řádku nabídek. Otevře se okno s názvem **Průzkumník testů** a měli byste vidět, že test **TestGetCurrentDate** projde.

![Průzkumník testů v sadě Visual Studio zobrazující předjetý test](media/tutorial-projects-test-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Pokud **se Průzkumník testů** neotevře automaticky, otevřete ho tak, že z řádku nabídek zvolíte **Testovat** > **Průzkumníka testů** **systému Windows.** > 

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Pokud **se Průzkumník testů** neotevře automaticky, otevřete ho tak, že z řádku nabídek zvolíte **Test** > **Explorer.**

::: moniker-end

## <a name="see-also"></a>Viz také

- [Vytváření projektů a řešení](../ide/creating-solutions-and-projects.md)
- [Správa vlastností projektu a řešení](../ide/managing-project-and-solution-properties.md)
- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
- [Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Přehled ide sady Visual Studio](../get-started/visual-studio-ide.md)
