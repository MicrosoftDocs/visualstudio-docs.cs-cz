---
title: Řešení a projekty
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b1783adadd1bfab32bfbbdcfb5ae28df7c0aae4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661196"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Řešení a projekty v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytváření aplikace, aplikace, webu, webové aplikace, skriptu, modulu plug-in atd. v aplikaci Visual Studio začnete s *projektem*. V logickém smyslu projekt obsahuje všechny soubory zdrojového kódu, ikony, obrázky, datové soubory a cokoli jiného, které budou zkompilovány do spustitelného programu nebo webu, nebo je pro provedení kompilace nutná jiná.  Projekt obsahuje také všechna nastavení kompilátoru a další konfigurační soubory, které mohou být vyžadovány různými službami nebo komponentami, se kterými bude program komunikovat.

 Ve smyslu literálu je projekt souborem XML (*. vbproj, \*. csproj, \*. vcxproj), který definuje hierarchii virtuálních složek společně s cestami ke všem položkám, které obsahuje, a všechna nastavení sestavení. V aplikaci Visual Studio se soubor projektu používá Průzkumník řešení k zobrazení obsahu a nastavení projektu. Při kompilaci projektu používá modul MSBuild při vytváření spustitelného souboru soubor projektu. Můžete také přizpůsobit projekty na produkt jiné druhy výstupu.

 Projekt je obsažen v logickém smyslu a v systému souborů v rámci *řešení*, které může obsahovat jeden nebo více projektů, společně s informacemi o sestavení, nastavením okna sady Visual Studio a dalšími soubory, které nejsou přidruženy k žádnému projektu. Ve smyslu literálu je řešením textový soubor s vlastním jedinečným formátem; obecně není určena k úpravám rukou.

 Řešení má přidružený soubor *. suo, který ukládá nastavení, předvolby a informace o konfiguraci pro každého uživatele, který v projektu pracoval.

 Následující diagram znázorňuje vztah mezi projekty a řešeními a položkami, které logicky obsahují.

 ![Projekty a řešení sady Visual Studio](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Můžete také vytvořit vlastní šablony projektů a položek. Další informace naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Vytváření nových projektů
 Nejjednodušší způsob, jak vytvořit nový projekt, je začít s předem definovanou šablonou projektu, která se skládá ze základní sady předem generovaných souborů kódu, konfiguračních souborů, prostředků a nastavení, které vám pomohou začít vytvářet konkrétní typ aplikace nebo webu v konkrétní programovací jazyk. Tyto šablony jsou to, co se zobrazuje v **dialogovém okně Nový projekt** , když v hlavní nabídce vyberete **soubor &#124; nový &#124; projekt** nebo  **&#124; nový &#124; web** a potom přejdete na. Další informace najdete v tématech [vytváření řešení a projektů](../ide/creating-solutions-and-projects.md) a [NIB vytváření projektů ze šablon](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Správa projektů v Průzkumník řešení
 Po vytvoření nového projektu použijete **Průzkumník řešení** k zobrazení a správě projektů a řešení a jejich přidružených položek. Následující ilustrace ukazuje Průzkumník serveru s C# řešením, které obsahuje dva projekty.

 ![Průzkumník řešení](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>V tomto oddílu

- [Vytváření řešení a projektů](../ide/creating-solutions-and-projects.md)

- [Přidávání a odebírání projektových položek](../ide/adding-and-removing-project-items.md)

- [Správa vlastností projektů a řešení](../ide/managing-project-and-solution-properties.md)

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)

- [Vlastnosti aplikace](../ide/application-properties.md)

- [Správa sestavení a podepsání manifestu](../ide/managing-assembly-and-manifest-signing.md)

- [Postupy: Určení ikony aplikace (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [Cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Viz také
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)
