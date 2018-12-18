---
title: Správa vlastností projektu a řešení
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77ac77ca999ef627c0f3c9e763b7e5799b97d679
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349241"
---
# <a name="manage-project-and-solution-properties"></a>Správa vlastností projektu a řešení

Projekty mají vlastnosti, které řídí mnoho aspektů kompilace, ladění, testování a nasazení. Některé vlastnosti jsou společné mezi všechny typy projektů a některé jsou jedinečné pro konkrétní jazyky a platformy. Přístup k vlastnosti projektu kliknutím pravým tlačítkem myši na uzel projektu v **Průzkumníka řešení** a zvolíte **vlastnosti**, nebo pomocí klávesové zkratky "properties" do **Snadné spuštění** vyhledávací pole v řádku nabídek.

![Kontextové nabídky projektu](../ide/media/vs2015_proj_prop_menu.gif)

Projekty .NET také může mít vlastnosti uzel ve stromu projektu, samotného.

![Vlastnosti uzlu stromové struktury Průzkumníka řešení](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [správu řešení a projektu vlastnosti (Visual Studio pro Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Vlastnosti projektu

Vlastnosti projektu jsou uspořádány do skupin a každá skupina má svou vlastní stránku vlastností. Na stránkách se může lišit pro různé jazyky a typy projektů.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic a F# projekty

V C#, Visual Basic a F# projekty, jsou přístupné vlastnosti **Návrháře projektu**. Je vidět na následujícím obrázku **sestavení** stránku vlastností pro projekt WPF v C#:

![Návrhář projektu sady Visual Studio](../ide/media/vs2015_proppage_build.png)

Informace o jednotlivých stránek vlastností v **Návrháře projektu**, naleznete v tématu [referenční dokumentace k vlastnostem projektu](../ide/reference/project-properties-reference.md).

> [!TIP]
> Řešení mít několik vlastností a tak projektové položky. Tyto vlastnosti jsou přístupné z [okno vlastností](../ide/reference/properties-window.md), nikoli **Návrháře projektu**.

### <a name="c-and-javascript-projects"></a>Projekty C++ a JavaScript

Projekty C++ a JavaScript mít různé uživatelské rozhraní pro správu vlastností projektu. Tento obrázek znázorňuje stránky vlastností projektu jazyka C++ (stránky JavaScript jsou podobné):

![Visual C&#43; &#43; vlastnosti projektu](../ide/media/vs2015_projprops_cpp.png)

Informace o vlastnostech projektů C++, naleznete v tématu [práce s vlastnostmi projektu (C++)](/cpp/ide/working-with-project-properties). Další informace o vlastnostech jazyka JavaScript naleznete v tématu [stránky vlastností, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Vlastnosti řešení

Přístup k vlastnostem na řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumníka řešení** a zvolte **vlastnosti**. V dialogovém okně můžete nastavit konfigurace projektu pro **ladění** nebo **vydání** sestavení, zvolte projekty, které by měl být spuštění projektu při **F5** stisknutí a nastavit na kód možnosti analýzy.

## <a name="see-also"></a>Viz také:

- [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Správa vlastností řešení a projektu (Visual Studio for Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
