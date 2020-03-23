---
title: Správa vlastností projektu a řešení
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591304"
---
# <a name="manage-project-and-solution-properties"></a>Správa vlastností projektu a řešení

Projekty mají vlastnosti, které řídí mnoho aspektů kompilace, ladění, testování a nasazování. Některé vlastnosti jsou běžné u všech typů projektů a některé jsou jedinečné pro konkrétní jazyky nebo platformy. K vlastnostem projektu se dostanete tak, že kliknete pravým tlačítkem myši na uzel projektu v **Průzkumníkovi řešení** a vyberete **vlastnosti** nebo zadáte **vlastnosti** do vyhledávacího pole na řádku nabídek a z výsledků zvolíte **Okno vlastností.**

![Kontextová nabídka projektu](../ide/media/vs2015_proj_prop_menu.gif)

Projekty .NET mohou mít také uzel vlastností v samotném stromu projektu.

![Uzel Vlastnosti ve stromu Průzkumník řešení](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Správa řešení a vlastností projektu (Visual Studio pro Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Vlastnosti projektu

Vlastnosti projektu jsou uspořádány do skupin a každá skupina má vlastní stránku vlastností. Stránky se mohou lišit pro různé jazyky a typy projektů.

### <a name="c-visual-basic-and-f-projects"></a>Projekty jazyka C#, Visual Basic a F#

V projektech jazyka C#, Visual Basic a F# jsou vlastnosti vystaveny v **návrháři projektu**. Následující obrázek **znázorňuje** stránku vlastností Sestavení pro projekt WPF v c#:

![Návrhář projektu Visual Studio](../ide/media/vs2015_proppage_build.png)

Informace o jednotlivých stránkách vlastností v **Návrháři projektu**naleznete v [tématu Project properties reference](../ide/reference/project-properties-reference.md).

> [!TIP]
> Řešení mají několik vlastností, stejně jako položky projektu; Tyto vlastnosti jsou přístupné v [okně Vlastnosti](../ide/reference/properties-window.md), nikoli **v Návrháři projektů**.

### <a name="c-and-javascript-projects"></a>Projekty C++ a JavaScriptu

Projekty jazyka C++ a JavaScript mají jiné uživatelské rozhraní pro správu vlastností projektu. Tento obrázek znázorňuje stránku vlastností projektu jazyka C++ (stránky JavaScriptu jsou podobné):

![Vlastnosti projektu Visual C&#43;&#43; ](../ide/media/vs2015_projprops_cpp.png)

Informace o vlastnostech projektu jazyka C++ naleznete v [tématu Práce s vlastnostmi projektu (C++).](/cpp/build/working-with-project-properties) Další informace o vlastnostech JavaScriptu naleznete v [tématu Property pages, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Vlastnosti řešení

Chcete-li získat přístup k vlastnostem řešení, klepněte pravým tlačítkem myši na uzel řešení v **Průzkumníku řešení** a zvolte **vlastnosti**. V dialogovém okně můžete nastavit konfigurace projektu pro **sestavení ladění** nebo **vydání,** zvolit, které projekty by měly být spouštěcím projektem při stisknutí **klávesy F5,** a nastavit možnosti analýzy kódu.

## <a name="see-also"></a>Viz také

- [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Správa vlastností řešení a projektu (Visual Studio pro Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
