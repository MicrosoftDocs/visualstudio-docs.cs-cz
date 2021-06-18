---
title: Co jsou Visual Studio &amp; řešení?
description: Seznamte se Visual Studio projekty a řešeními, jak vytvářet nové projekty ze šablony a jak zobrazit & spravovat projekty v Průzkumník řešení.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f632922078383708319e610d82a4c94a58619424
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306394"
---
# <a name="what-are-solutions-and-projects-in-visual-studio"></a>Co jsou řešení a projekty v Visual Studio?

V tomto článku se dozvíte, co *je projekt* *a* řešení v Visual Studio. Stručně se také věnuje Průzkumník řešení nástroje a vytvoření nového projektu.

> [!NOTE]
> Toto téma se týká Visual Studio ve Windows. Další Visual Studio pro Mac v tématu [Projekty a řešení v Visual Studio pro Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Při vytváření aplikace nebo webu v Visual Studio začnete s *projektem*. V logickém smyslu projekt obsahuje všechny soubory, které jsou zkompilovány do spustitelného souboru, knihovny nebo webu. Mezi tyto soubory může zahrnovat zdrojový kód, ikony, obrázky, datové soubory atd. Projekt obsahuje také nastavení kompilátoru a další konfigurační soubory, které mohou být potřebné různými službami nebo komponentami, se které program komunikuje.

### <a name="project-file"></a>Soubor projektu

Visual Studio každý projekt v řešení pomocí nástroje [MSBuild](../msbuild/msbuild.md) a každý projekt obsahuje soubor projektu nástroje MSBuild. Přípona souboru odráží typ projektu, například projekt jazyka C# (.csproj), projekt Visual Basic (.vbproj) nebo databázový projekt (.dbproj). Soubor projektu je dokument XML, který obsahuje všechny informace a pokyny, které nástroj MSBuild potřebuje k sestavení projektu, včetně obsahu, požadavků na platformu, informací o verzích, nastavení webového serveru nebo databázového serveru a úkolů, které se mají provést.

Soubory projektu jsou založené na schématu [MSBuild XML](../msbuild/msbuild-project-file-schema-reference.md). Pokud se chcete podívat na obsah novějších souborů projektu ve stylu sady [SDK](../msbuild/how-to-use-project-sdk.md) v Visual Studio, klikněte pravým tlačítkem na uzel projektu v **Průzkumník řešení** vyberte **Upravit. \<projectname\>** Pokud se chcete podívat na obsah .NET Framework a dalších projektů tohoto stylu, nejprve uvolněte projekt (klikněte pravým tlačítkem na uzel projektu v **Průzkumník řešení** vyberte **Uvolnit projekt**). Pak klikněte pravým tlačítkem na projekt a zvolte **Upravit. \<projectname\>**

> [!NOTE]
> K úpravám, sestavování a ladění kódu nemusíte Visual Studio nebo projekty v nástroji . Můžete jednoduše otevřít složku, která obsahuje zdrojové soubory v Visual Studio a začít s úpravami. Další informace najdete v tématu [Vývoj kódu v Visual Studio bez projektů nebo řešení.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

### <a name="create-new-projects"></a>Vytvořit nové projekty

Nejjednodušší způsob, jak vytvořit nový projekt, je použít šablonu projektu pro typ projektu, který chcete. Šablona projektu obsahuje základní sadu předem vygenerovaných souborů kódu, konfiguračních souborů, prostředků a nastavení. Pomocí **možnosti**  >  **File New** Project  >  **(Soubor** nového projektu) vyberte šablonu projektu. Další informace najdete v [tématu Vytvoření nového projektu.](create-new-project.md)

Můžete také vytvořit vlastní šablonu projektu, ze které můžete vytvářet nové projekty. Další informace najdete v tématu [Vytvoření šablon projektů a položek.](../ide/creating-project-and-item-templates.md)

Když vytvoříte nový projekt, Visual Studio uloží do výchozího umístění *, %USERPROFILE%\source\repos*. Pokud chcete toto umístění změnit, přejděte na **Nástroje**  >  **Možnosti**  >  **Umístění projektů a**  >  **řešení.** Další informace najdete v dialogovém [okně Možnosti: Projekty a řešení > umístění.](./reference/projects-solutions-locations-options.md)

## <a name="solutions"></a>Řešení

Projekt je obsažen v *řešení*. Řešení navzdory svému názvu není "odpovědí". Je to jednoduše kontejner pro jeden nebo více souvisejících projektů, spolu s informacemi o sestavení, nastavením okna Visual Studio různými soubory, které nejsou přidružené ke konkrétnímu projektu.

### <a name="solution-file"></a>Soubor řešení

Visual Studio používá dva typy souborů (*.sln* a *.suo*) k ukládání nastavení pro řešení:

|Linka|Název|Description|
|---------------|----------|-----------------|
|.sln|Visual Studio řešení|Uspořádá v řešení projekty, položky projektu a položky řešení.|
|.suo|Možnosti uživatele řešení|Ukládá nastavení a přizpůsobení na úrovni uživatele, jako jsou zarážky.|

> [!IMPORTANT]
> Řešení je popsané textovým souborem (s *příponou .sln)* s vlastním jedinečným formátem. Není určený k ručním úpravám. Naopak soubor *.suo* je skrytý soubor, který se nezobrazuje ve výchozím nastavení Průzkumník souborů nastavení. Pokud chcete zobrazit skryté soubory, v **nabídce Zobrazení** v Průzkumník souborů zaškrtněte **políčko Skryté** položky.

### <a name="solution-folder"></a>Složka řešení

"Složka řešení" je virtuální složka, která je jenom **v Průzkumník řešení**, kde ji můžete použít k seskupení projektů v řešení. Pokud chcete najít soubor řešení na počítači, přejděte na **Nástroje** Možnosti Umístění projektů a  >    >    >  **řešení.** Další informace najdete v dialogovém [okně Možnosti: Projekty a řešení > umístění.](./reference/projects-solutions-locations-options.md)

> [!TIP]
> Příklad projektu a řešení vytvořeného od začátku s podrobnými pokyny a ukázkovým kódem najdete v tématu Úvod do projektů a [řešení.](../get-started/tutorial-projects-solutions.md)

## <a name="solution-explorer"></a>Průzkumník řešení

Po vytvoření nového projektu můžete pomocí nástroje **Průzkumník řešení** zobrazit a spravovat projekt a řešení a související položky. Následující obrázek znázorňuje **Průzkumník řešení** s řešením jazyka C#, které obsahuje dva projekty:

::: moniker range="vs-2017"

![Snímek obrazovky Průzkumník řešení se dvěma projekty](../ide/media/vs2015_solution_explorer.png)

Panel nástrojů v horní části **Průzkumník řešení** obsahuje tlačítka pro přepnutí ze zobrazení řešení do zobrazení složek, zobrazení skrytých souborů, sbalení všech uzlů a další.

::: moniker-end

::: moniker range=">=vs-2019"

![Snímek obrazovky Průzkumník řešení se dvěma projekty v Visual Studio](../ide/media/solution-explorer.png)

Panel nástrojů v horní části **Průzkumník řešení** obsahuje tlačítka pro přepnutí ze zobrazení řešení do zobrazení složek, filtrování čekajících [](managing-project-and-solution-properties.md) změn, zobrazení všech [](writing-code-in-the-code-and-text-editor.md)souborů, sbalení všech uzlů, zobrazení stránek vlastností, náhled kódu v editoru kódu a další.

::: moniker-end

Mnoho příkazů nabídky je k dispozici v místní nabídce po kliknutí pravým tlačítkem na různé položky **v Průzkumník řešení**. Mezi tyto příkazy patří sestavení projektu, správa balíčků NuGet, přidání odkazu, přejmenování souboru a spuštění testů– jen pro některé z nich.

U ASP.NET Core můžete přizpůsobit, jak se soubory vnořuje do **Průzkumník řešení**. Další informace najdete v tématu [Přizpůsobení vnořování souborů v Průzkumník řešení](file-nesting-solution-explorer.md).

> [!TIP]
> Pokud jste aplikaci zavřeli Průzkumník řešení chcete ji znovu otevřít, na řádku   >  **nabídek zvolte** Zobrazit Průzkumník řešení nebo stiskněte **Ctrl** + **Alt** + **L.** A pokud jste zavřeli boční karty a chcete je obnovit do výchozích umístění, zvolte na řádku nabídek Rozložení okna  >  **Resetovat** okno.

> [!NOTE]
> Pokud chcete zobrazit obrázky a ikony aplikací, které se Visual Studio, stáhněte si Visual Studio [**Image Library.**](https://www.microsoft.com/download/details.aspx?id=35825)

## <a name="see-also"></a>Viz také

- [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Filtrovaná řešení v Visual Studio](filtered-solutions.md)
- [Přenos, migrace a upgrade projektů](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Zdroje informací pro řešení Visual Studio chyb integrovaného vývojového prostředí](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projekty a řešení (Visual Studio pro Mac)](/visualstudio/mac/projects-and-solutions)
