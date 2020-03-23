---
title: Řešení a projekty
ms.date: 10/05/2017
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
ms.openlocfilehash: ffa561667ea31f215306c7cac4b9820d7b386b5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303069"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v sadě Visual Studio

Tato stránka popisuje koncept *projektu* a *řešení* v sadě Visual Studio. Také stručně popisuje okno nástroje Průzkumníka řešení a jak vytvořit nový projekt.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Projekty a řešení ve Visual Studiu pro Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Když vytvoříte aplikaci nebo web v Sadě Visual Studio, začnete s *projektem*. V logickém smyslu projekt obsahuje všechny soubory, které jsou zkompilovány do spustitelného souboru, knihovny nebo webu. Tyto soubory mohou obsahovat zdrojový kód, ikony, obrázky, datové soubory a tak dále. Projekt také obsahuje nastavení kompilátoru a další konfigurační soubory, které mohou být potřebné pro různé služby nebo součásti, které program komunikuje.

### <a name="project-file"></a>Soubor projektu

Visual Studio používá [MSBuild](../msbuild/msbuild.md) k sestavení každého projektu v řešení a každý projekt obsahuje soubor projektu MSBuild. Přípona souboru odráží typ projektu, například projekt Jazyka C# (.csproj), projekt jazyka (.vbproj) nebo databázový projekt (.dbproj). Soubor projektu je dokument XML, který obsahuje všechny informace a pokyny, které msbuild potřebuje k vytvoření projektu, včetně obsahu, požadavků na platformu, informací o správě verzí, nastavení webového serveru nebo databázového serveru a úkolů Provést.

Soubory projektu jsou založeny na [schématu XML msbuild](../msbuild/msbuild-project-file-schema-reference.md). Chcete-li se podívat na obsah novějších [souborů projektu ve stylu sady SDK](../msbuild/how-to-use-project-sdk.md) v sadě Visual Studio, klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte upravit ** \<název\>projektu**. Chcete-li se podívat na obsah rozhraní .NET Framework a dalších projektů tohoto stylu, nejprve projekt uvolněte (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte **uvolnit projekt).** Potom klikněte pravým tlačítkem myši na projekt a zvolte **Upravit \<název\>projektu**.

> [!NOTE]
> Není třeba používat řešení nebo projekty v sadě Visual Studio upravit, sestavit a ladit kód. Můžete jednoduše otevřít složku, která obsahuje zdrojové soubory v sadě Visual Studio a začít upravovat. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Řešení

Projekt je obsažen v *řešení*. Navzdory svému názvu není řešení "odpovědí". Je to jednoduše kontejner pro jeden nebo více souvisejících projektů, spolu s informacemi o sestavení, nastavení okna sady Visual Studio a všechny různé soubory, které nejsou přidruženy k určitému projektu. Řešení je popsáno textovým souborem (přípona *.sln)* s vlastním jedinečným formátem; není určen k ruční úpravě.

Visual Studio používá dva typy souborů (*.sln* a *.suo*) k ukládání nastavení řešení:

|Linka|Name (Název)|Popis|
|---------------|----------|-----------------|
|.sln|Řešení Visual Studio|Uspořádá projekty, položky projektu a položky řešení v řešení.|
|.suo|Možnosti uživatele řešení|Ukládá nastavení na úrovni uživatele a vlastní nastavení, například zarážky.|

## <a name="create-new-projects"></a>Vytvořit nové projekty

Nejjednodušší způsob, jak vytvořit nový projekt, je začít od šablony projektu pro určitý typ aplikace nebo webu. Šablona projektu se skládá ze základní sady předem generovaných souborů kódu, konfiguračních souborů, datových zdrojů a nastavení. Tyto šablony jsou k dispozici v dialogovém okně, ve kterém vytvoříte nový projekt (**Soubor** > **nového** > **projektu**). Další informace naleznete [v tématu Vytvoření nového projektu v sadě Visual Studio](create-new-project.md) a Vytváření řešení a [projektů](../ide/creating-solutions-and-projects.md).

Pokud projekty často upravujete určitým způsobem, můžete vytvořit vlastní šablonu projektu, ze které pak můžete vytvořit nové projekty. Další informace naleznete v [tématu Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

Při vytváření nového projektu je ve výchozím nastavení uložen na *%USERPROFILE%\source\repos*. Toto umístění můžete změnit v části **Nastavení umístění Projekty** v části **Projekty** > **a** > **umístění****řešení** > . Další informace naleznete v [tématu Projekty a řešení, dialogové okno Možnosti](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Průzkumník řešení

Po vytvoření nového projektu můžete pomocí **Průzkumníka řešení** zobrazit a spravovat projekt a řešení a jejich přidružené položky. Následující obrázek znázorňuje **Průzkumníka řešení** s řešením Jazyka C#, který obsahuje dva projekty:

![Průzkumník řešení](../ide/media/vs2015_solution_explorer.png)

Mnoho příkazů nabídky je k dispozici v nabídce po kliknutí pravým tlačítkem myši u různých položek v **Průzkumníku řešení**. Tyto příkazy zahrnují vytváření projektu, správu balíčků NuGet, přidání odkazu, přejmenování souboru a spuštění testů, abychom jmenovali jen několik. Panel nástrojů v horní části **Průzkumníka řešení** obsahuje tlačítka pro přepnutí ze zobrazení řešení do zobrazení složky, zobrazení skrytých souborů, sbalení všech uzlů a další.

Pro ASP.NET základní projekty můžete přizpůsobit, jak jsou soubory vnořené v **Průzkumníku řešení**. Další informace naleznete [v tématu Customize file nesting in Solution Explorer](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Viz také

- [IDE visual studia](../get-started/visual-studio-ide.md)
- [Projekty a řešení (Visual Studio pro Mac)](/visualstudio/mac/projects-and-solutions)
- [Přidání a odebrání položek projektu (Visual Studio pro Mac)](/visualstudio/mac/add-and-remove-project-items)
