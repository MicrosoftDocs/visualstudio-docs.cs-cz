---
title: Správa vlastností projektu a řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec48aac60a8f15527c92d19a38ca9f996dcfdd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651352"
---
# <a name="managing-project-and-solution-properties"></a>Správa vlastností projektů a řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty mají vlastnosti, které řídí mnoho aspektů kompilace, ladění, testování a nasazení. Některé vlastnosti jsou společné mezi všemi typy projektů a některé jsou jedinečné pro konkrétní jazyky nebo platformy. K vlastnostem projektu přistupujete kliknutím pravým tlačítkem myši na uzel projektu v Průzkumník řešení a zvolením vlastnosti nebo zadáním vlastností do vyhledávacího pole **Rychlé spuštění** v řádku nabídek.

 ![Místní nabídka projektu](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")

 Projekty .NET mají také uzel vlastnosti ve stromové struktuře projektu.

 ![Uzel vlastností ve stromu Průzkumník řešení](../ide/media/vs2015-props-se.png "VS2015_Props_SE")

> [!TIP]
> Řešení mají několik vlastností, a proto položky projektu. Tyto vlastnosti jsou k dispozici v [okně Vlastnosti](../ide/reference/properties-window.md), nikoli v **Návrháři projektu**.

## <a name="project-properties"></a>Vlastnosti projektu
 Vlastnosti projektu jsou uspořádány do skupin a každá skupina má svou vlastní stránku vlastností a stránky se mohou lišit pro různé jazyky a typy projektů.

### <a name="c-and-visual-basic-projects"></a>C#a Visual Basic projekty
 V C# a Visual Basic projekty jsou vlastnosti zpřístupněny v **Návrháři projektu**. Na následujícím obrázku je znázorněna stránka vlastností sestavení pro projekt WPF v C#nástroji:

 ![Návrhář projektu sady Visual Studio](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")

 Informace o jednotlivých stránkách vlastností v Návrháři projektu naleznete v tématu [reference Project Properties reference](../ide/reference/project-properties-reference.md).

### <a name="c-and-javascript-projects"></a>C++a projekty JavaScriptu
 C++projekty JavaScriptu mají jiné uživatelské rozhraní pro správu vlastností projektu. Tento obrázek ukazuje stránku C++ vlastností projektu (stránky JavaScriptu jsou podobné):

 ![Vlastnosti projektu&#43; &#43; Visual c++](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")

 Informace o C++ vlastnostech projektu naleznete v tématu [práce s vlastnostmi projektu](https://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). Další informace o vlastnostech JavaScriptu naleznete v tématu [stránky vlastností, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Vlastnosti řešení
 Chcete-li získat přístup k vlastnostem v řešení, klikněte pravým tlačítkem myši na uzel řešení v **Průzkumník řešení** a vyberte příkaz **vlastnosti**. V dialogovém okně můžete nastavit konfigurace projektu pro sestavení pro ladění nebo vydaných verzí, zvolit, které projekty by měly být spouštěny při stisknutí klávesy F5 a nastaveny možnosti analýzy kódu.

## <a name="see-also"></a>Viz také
 [Řešení a projekty v sadě Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
