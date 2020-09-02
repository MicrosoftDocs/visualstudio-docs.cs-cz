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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591304"
---
# <a name="manage-project-and-solution-properties"></a>Správa vlastností projektu a řešení

Projekty mají vlastnosti, které řídí mnoho aspektů kompilace, ladění, testování a nasazení. Některé vlastnosti jsou společné mezi všemi typy projektů a některé jsou jedinečné pro konkrétní jazyky nebo platformy. Přístup k vlastnostem projektu získáte tak, že kliknete pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a zvolíte **vlastnosti** nebo zadáte **vlastnosti** do vyhledávacího pole na řádku nabídek a z výsledků zvolíte **okno Vlastnosti** .

![Místní nabídka projektu](../ide/media/vs2015_proj_prop_menu.gif)

Projekty .NET mohou mít také uzel vlastností ve stromové struktuře projektu.

![Uzel vlastností ve stromu Průzkumník řešení](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [Správa vlastností řešení a projektu (Visual Studio pro Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Vlastnosti projektu

Vlastnosti projektu jsou uspořádány do skupin a každá skupina má svou vlastní stránku vlastností. Stránky se mohou lišit pro různé jazyky a typy projektů.

### <a name="c-visual-basic-and-f-projects"></a>Projekty C#, Visual Basic a F #

V projektech C#, Visual Basic a F # jsou vlastnosti zpřístupněny v **Návrháři projektu**. Následující ilustrace znázorňuje stránku vlastností **sestavení** pro projekt WPF v jazyce C#:

![Návrhář projektu sady Visual Studio](../ide/media/vs2015_proppage_build.png)

Informace o jednotlivých stránkách vlastností v **Návrháři projektu**naleznete v tématu [reference Project Properties reference](../ide/reference/project-properties-reference.md).

> [!TIP]
> Řešení mají několik vlastností, a proto položky projektu. Tyto vlastnosti jsou k dispozici v [okno Vlastnosti](../ide/reference/properties-window.md), nikoli v **Návrháři projektu**.

### <a name="c-and-javascript-projects"></a>Projekty C++ a JavaScript

Projekty C++ a JavaScript mají jiné uživatelské rozhraní pro správu vlastností projektu. Tento obrázek ukazuje stránku vlastností projektu C++ (stránky JavaScriptu jsou podobné):

![Visual C++&#43;&#43; – vlastnosti projektu](../ide/media/vs2015_projprops_cpp.png)

Informace o vlastnostech projektu C++ naleznete v tématu [work with Project Properties (C++)](/cpp/build/working-with-project-properties). Další informace o vlastnostech JavaScriptu naleznete v tématu [stránky vlastností, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Vlastnosti řešení

Chcete-li získat přístup k vlastnostem v řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte příkaz **vlastnosti**. V dialogovém okně můžete nastavit konfigurace projektu pro sestavení pro **ladění** nebo **vydání** , zvolit, které projekty by měly být spouštěny při stisknutí klávesy **F5** a nastaveny možnosti analýzy kódu.

## <a name="see-also"></a>Viz také

- [Řešení a projekty v aplikaci Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Správa vlastností řešení a projektu (Visual Studio pro Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
