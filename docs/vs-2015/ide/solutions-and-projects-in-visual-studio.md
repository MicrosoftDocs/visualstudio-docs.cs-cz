---
title: Řešení a projekty
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 068fe27df565f83312040fa0bcf6412e4984d9fd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067139"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytváření aplikace, aplikace, webu, webové aplikace, script, modulu plug-in a tak podobně v sadě Visual Studio začínáte *projektu*. Z logického pohledu projekt obsahuje všechny soubory zdrojového kódu, ikony, obrázků, datové soubory a cokoliv jiného, co se zkompiluje do spustitelný program nebo webu, jinak je potřeba, aby bylo možné provést kompilace.  Projekt obsahuje také všechna nastavení kompilátoru a další konfigurační soubory, které mohou být potřebné různé služby nebo komponenty, které váš program bude komunikovat s.

 V literálu smysl projektu je soubor XML (*.vbproj, \*.csproj, \*.vcxproj), který definuje virtuální složka hierarchii společně s cesty pro všechny položky "obsahuje" a všechna nastavení sestavení. V sadě Visual Studio je soubor projektu používáno Průzkumníkem řešení zobrazíte obsah projektu a nastavení. Při kompilaci projektu využívá stroji MSBuild engine souboru projektu k vytvoření spustitelného souboru. Projekty do produktu můžete také upravit další druhy výstup.

 Projekt je obsažená, z logického pohledu a v systému souborů v rámci *řešení*, která může obsahovat jeden nebo více projektů, spolu s informacemi o sestavení, nastavení okna sady Visual Studio a všechny ostatní soubory, které nejsou související s žádným projektem. V literálu smysl řešení je textový soubor s svůj vlastní jedinečný formát; zpravidla není určen upravit ručně.

 Řešení je přidružená *.suo soubor, který uchovává nastavení, předvoleb a informace o konfiguraci pro každý uživatel, který pracoval na projektu.

 Následující diagram znázorňuje vztah mezi projekty a řešení a položky, které logicky obsahují.

 ![Řešení a projektů sady Visual Studio](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Můžete také vytvořit vlastní šablony projektů a položek. Další informace najdete v tématu [vytváření projektů a šablon položek](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Vytváření nových projektů
 Nejjednodušší způsob, jak vytvořit nový projekt, je začít s předem definovaných projektové šablony, která obsahuje základní sadu souborů předem generovaného kódu, konfigurační soubory, prostředky, a nastavení, které vám pomůžou začít vytvářet konkrétní typ aplikace nebo webu konkrétní programovací jazyk. Tyto šablony se zobrazí v **dialogové okno nového projektu** při výběru **souboru &#124; nový &#124; projektu** nebo **souboru &#124; nový &#124; webu** z hlavní nabídky a potom přejděte. Další informace najdete v tématu [vytváření řešení a projekty](../ide/creating-solutions-and-projects.md) a [NIB vytváření projektů ze šablon](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Správa projektů v Průzkumníku řešení
 Po vytvoření nového projektu použijete **Průzkumníka řešení** zobrazení a správa projektů a řešení a jejich přidružené položky. Následující obrázek znázorňuje řešení C#, které obsahuje dva projekty Průzkumníka serveru.

 ![Průzkumník řešení](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>V tomto oddílu

-   [Vytváření řešení a projektů](../ide/creating-solutions-and-projects.md)

-   [Přidávání a odebírání projektových položek](../ide/adding-and-removing-project-items.md)

-   [Správa vlastností projektů a řešení](../ide/managing-project-and-solution-properties.md)

-   [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)

-   [Vlastnosti aplikace](../ide/application-properties.md)

-   [Správa sestavení a podepsání manifestu](../ide/managing-assembly-and-manifest-signing.md)

-   [Postupy: Určení ikony aplikace (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

-   [Cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

-   [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Viz také
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)
