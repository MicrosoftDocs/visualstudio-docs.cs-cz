---
title: Řešení a projekty
ms.date: 10/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db576170443952a3090d57fc8046b34428cc8095
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348340"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v sadě Visual Studio

Tento článek popisuje koncept *projektu* a *řešení* v sadě Visual Studio. Také stručně popisuje, jak vytvořit nový projekt a **Průzkumníka řešení** panelu nástrojů.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [projekty a řešení v sadě Visual Studio pro Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Když vytvoříte aplikaci, web, modul plug-in a tak dále v sadě Visual Studio začínáte *projektu*. Z logického pohledu projekt obsahuje všechny soubory zdrojového kódu, ikony, obrázky, datových souborů, atd., které jsou kompilovány do spustitelný soubor, knihovny nebo webu. Projekt obsahuje také nastavení kompilátoru a další konfigurační soubory, které mohou být potřebné různé služby nebo komponenty, které aplikace komunikuje s.

> [!NOTE]
> Není nutné používat řešení nebo projektů v sadě Visual Studio k úpravám, sestavení a ladění kódu. Můžete jednoduše otevřete složku, která obsahuje zdrojové soubory v sadě Visual Studio a můžete začít upravovat. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Projekt je definována v souboru XML s příponou jako například *.vbproj*, *.csproj*, nebo *.vcxproj*. Tento soubor obsahuje hierarchii virtuální složka a cesty pro všechny položky v projektu. Obsahuje také nastavení sestavení.

> [!TIP]
> Podívat se na obsah souboru projektu v sadě Visual Studio, nejprve uvolněte projekt tak, že vyberete název projektu v **Průzkumníka řešení** a zvolíte **uvolnit projekt** z nabídky kontextu nebo klikněte pravým tlačítkem. Potom znovu otevřete kontextovou nabídku a zvolte **upravit \<projectname\>**.

V sadě Visual Studio, soubor projektu používá **Průzkumníka řešení** zobrazíte obsah projektu a nastavení. Při kompilaci projektu využívá stroji MSBuild engine souboru projektu k vytvoření spustitelného souboru. Můžete také upravit projekty k vytvoření jiných typů výstup.

## <a name="solutions"></a>Řešení

Je součástí projektu *řešení*. Bez ohledu na jeho název řešení není "odpověď". Je prostě kontejner pro jeden nebo více souvisejících projektů, spolu s informacemi o sestavení, nastavení okna sady Visual Studio a všechny ostatní soubory, které nejsou spojeny s konkrétní projekt. Řešení je popsán textového souboru (rozšíření *.sln*) s svůj vlastní jedinečný formát; má nejsou určeny upravit ručně.

Visual Studio používá dva typy souborů (*.sln* a *.suo*) k ukládání nastavení řešení:

|Linka|Název|Popis|
|---------------|----------|-----------------|
|.sln|Řešení sady Visual Studio|Uspořádá projekty, položky projektu a řešení položky v řešení.|
|.suo|Uživatelské možnosti řešení|Ukládají se nastavení na úrovni uživatele a vlastní nastavení, jako například zarážky.|

## <a name="create-new-projects"></a>Vytvořit nové projekty

Nejjednodušší způsob, jak vytvořit nový projekt je začít z šablony projektu pro konkrétní typ aplikace nebo webu. Šablona projektu se skládá ze základní sady souborů předem generovaného kódu, konfigurační soubory, prostředky a nastavení. Tyto šablony se zobrazí v **nový projekt** dialogové okno při výběru **souboru** > **nový** > **projektu**. Další informace najdete v tématu [vytvářet řešení a projekty](../ide/creating-solutions-and-projects.md).

Můžete také vytvořit vlastní šablony projektů a položek. Další informace najdete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Spravovat projekty v Průzkumníkovi řešení

Když vytvoříte nový projekt, můžete použít **Průzkumníka řešení** k zobrazení a správě projektu a řešení a jejich přidružené položky. Následující ilustrace ukazuje **Průzkumníka řešení** s C# řešení, které obsahuje dva projekty:

![Průzkumník řešení](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>Viz také:

- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
- [Projekty a řešení (Visual Studio for Mac)](/visualstudio/mac/projects-and-solutions)
- [Přidání a odebrání položek projektu (Visual Studio for Mac)](/visualstudio/mac/add-and-remove-project-items)