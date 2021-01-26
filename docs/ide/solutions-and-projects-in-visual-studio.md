---
title: Informace o řešeních a projektech
description: Přečtěte si o projektech a řešeních sady Visual Studio, způsobu vytváření nových projektů ze šablony a o tom, jak zobrazit & spravovat projekty v Průzkumník řešení.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2a64b613ca19632a7827686ab0552e6e23620c1
ms.sourcegitcommit: 3922edfe67063e1ede418cdbf6aa6293117c4855
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98773333"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v aplikaci Visual Studio

Tato stránka popisuje koncept *projektu* a *řešení* v aplikaci Visual Studio. Také stručně pokrývá okno Průzkumník řešení nástrojů a postup vytvoření nového projektu.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [projekty a řešení v Visual Studio pro Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Při vytváření aplikace nebo webu v aplikaci Visual Studio začnete s *projektem*. V logickém smyslu projekt obsahuje všechny soubory, které jsou zkompilovány do spustitelného souboru, knihovny nebo webu. Tyto soubory mohou zahrnovat zdrojový kód, ikony, obrázky, datové soubory a tak dále. Projekt obsahuje také nastavení kompilátoru a další konfigurační soubory, které mohou být vyžadovány různými službami nebo komponentami, se kterými váš program komunikuje.

### <a name="project-file"></a>Soubor projektu

Visual Studio používá [MSBuild](../msbuild/msbuild.md) k sestavení jednotlivých projektů v řešení a každý projekt obsahuje soubor projektu MSBuild. Přípona souboru odráží typ projektu, například projekt C# (. csproj), Visual Basic projekt (. vbproj) nebo databázový projekt (. dbproj). Soubor projektu je dokument XML, který obsahuje všechny informace a pokyny, které nástroj MSBuild potřebuje k sestavení projektu, včetně obsahu, požadavků na platformu, informací o verzích, webového serveru nebo databázového serveru a úkolů, které mají být provedeny.

Soubory projektu jsou založeny na [schématu XML jazyka MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Chcete-li se podívat na obsah novějších [souborů projektů ve stylu sady SDK v sadě](../msbuild/how-to-use-project-sdk.md) Visual Studio, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **Upravit \<projectname\>**. Chcete-li se podívat na obsah .NET Framework a dalších projektů tohoto stylu, nejprve uvolněte projekt (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **Uvolnit projekt**). Potom klikněte pravým tlačítkem na projekt a zvolte možnost **Upravit \<projectname\>**.

> [!NOTE]
> K úpravám, sestavování a ladění kódu nemusíte používat řešení nebo projekty v aplikaci Visual Studio. Jednoduše otevřete složku, která obsahuje zdrojové soubory v aplikaci Visual Studio, a začněte upravovat. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="create-new-projects"></a>Vytvořit nové projekty

Nejjednodušší způsob, jak vytvořit nový projekt, je použít šablonu projektu pro typ projektu, který chcete. Šablona projektu obsahuje základní sadu předem generovaných souborů kódu, konfiguračních souborů, prostředků a nastavení.   >    >  Pro výběr šablony projektu použijte soubor nový **projekt** . Další informace najdete v tématu [Vytvoření nového projektu](create-new-project.md).

Můžete také vytvořit vlastní šablonu projektu, kterou můžete použít k vytvoření nových projektů z. Další informace naleznete v tématu [Create Project and Item Templates](../ide/creating-project-and-item-templates.md).

Když vytvoříte nový projekt, Visual Studio ho uloží do výchozího umístění *%USERPROFILE%\source\repos*. Pokud chcete toto umístění změnit, přejděte na **nástroje**  >  **Možnosti**  >  **projekty a**  >  **umístění** řešení. Další informace najdete v [dialogovém okně Možnosti: projekty a řešení > umístění](./reference/projects-solutions-locations-options.md).

## <a name="solutions"></a>Řešení

Projekt je obsažen v rámci *řešení*. Bez ohledu na jeho název není řešení "Answer". Je to jednoduše kontejner pro jeden nebo více souvisejících projektů, společně s informacemi o sestavení, nastavení okna sady Visual Studio a s dalšími soubory, které nejsou přidružené k určitému projektu.

### <a name="solution-file"></a>Soubor řešení

Visual Studio používá dva typy souborů (*. sln* a *. suo*) k ukládání nastavení řešení:

|Linka|Název|Popis|
|---------------|----------|-----------------|
|. sln|Řešení sady Visual Studio|Uspořádá projekty, položky projektu a položky řešení v řešení.|
|. suo|Možnosti uživatele řešení|Ukládá nastavení a přizpůsobení na úrovni uživatele, například zarážky.|

> [!IMPORTANT]
> Řešení je popsáno v textovém souboru (s příponou *. sln*) s vlastním jedinečným formátem. není určeno k úpravám rukou. Naopak soubor *. suo* je skrytý soubor, který není zobrazen pod výchozím nastavením Průzkumníka souborů. Skryté soubory zobrazíte tak, že v nabídce **Zobrazit** v Průzkumníkovi souborů zaškrtnete políčko **skryté položky** .

### <a name="solution-folder"></a>Složka řešení

"Složka řešení" je virtuální složkou, která je pouze v **Průzkumník řešení**, kde ji můžete použít k seskupení projektů v řešení. Pokud chcete na počítači najít soubor řešení, přejděte na možnosti **nástroje**  >    >  **projekty a**  >  **umístění** řešení. Další informace najdete v [dialogovém okně Možnosti: projekty a řešení > umístění](./reference/projects-solutions-locations-options.md).

> [!TIP]
> Příklad projektu a řešení vytvořeného od začátku, dokončení s podrobnými pokyny a ukázkový kód naleznete v tématu [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md).

## <a name="solution-explorer"></a>Průzkumník řešení

Po vytvoření nového projektu můžete použít **Průzkumník řešení** k zobrazení a správě projektu a řešení a jejich přidružených položek. Následující ilustrace ukazuje **Průzkumník řešení** s řešením C#, které obsahuje dva projekty:

::: moniker range="vs-2017"

![Snímek obrazovky Průzkumník řešení se dvěma projekty](../ide/media/vs2015_solution_explorer.png)

Panel nástrojů v horní části **Průzkumník řešení** obsahuje tlačítka pro přepínání ze zobrazení řešení do zobrazení složky, zobrazení skrytých souborů, sbalení všech uzlů a další.

::: moniker-end

::: moniker range="vs-2019"

![Snímek obrazovky Průzkumník řešení se dvěma projekty v aplikaci Visual Studio 2019.](../ide/media/solution-explorer.png)

Panel nástrojů v horní části **Průzkumník řešení** obsahuje tlačítka pro přepínání ze zobrazení řešení do zobrazení složky, filtrování nedokončených změn, zobrazení všech souborů, sbalení všech uzlů, zobrazení stránek [vlastností](managing-project-and-solution-properties.md) , náhled kódu v [editoru kódu](writing-code-in-the-code-and-text-editor.md)a další.

::: moniker-end

Řada příkazů nabídky je k dispozici v kontextové nabídce pravého tlačítka myši na různých položkách v **Průzkumník řešení**. Mezi tyto příkazy patří sestavení projektu, Správa balíčků NuGet, přidání odkazu, přejmenování souboru a spuštění testů, stačí jenom pár název.

U ASP.NET Core projektů můžete přizpůsobit, jak jsou soubory vnořené v **Průzkumník řešení**. Další informace najdete v tématu [přizpůsobení vnořování souborů v Průzkumník řešení](file-nesting-solution-explorer.md).

> [!TIP]
> Pokud jste Průzkumník řešení zavřeli a chcete ho znovu otevřít, zvolte **Zobrazit**  >  **Průzkumník řešení** na řádku nabídek nebo stiskněte klávesovou **zkratku CTRL** + **+** + **L**. A pokud jste uzavřeli vedlejší karty a chcete je obnovit do jejich výchozích umístění **, vyberte**  >  z panelu nabídek možnost **rozložení okna obnovit okno** .

> [!NOTE]
> Chcete-li zobrazit obrázky a ikony aplikace, které se zobrazí v aplikaci Visual Studio, Stáhněte si [**knihovnu imagí sady Visual Studio**](https://www.microsoft.com/download/details.aspx?id=35825).

## <a name="see-also"></a>Viz také

- [Seznámení s projekty a řešení](../get-started/tutorial-projects-solutions.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Filtrovaná řešení v aplikaci Visual Studio](filtered-solutions.md)
- [Přenos, migrace a upgrade projektů](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Prostředky pro řešení potíží s chybami IDE sady Visual Studio](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projekty a řešení (Visual Studio pro Mac)](/visualstudio/mac/projects-and-solutions)