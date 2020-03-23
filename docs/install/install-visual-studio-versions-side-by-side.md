---
title: Souběžná instalace různých verzí sady Visual Studio
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114643"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Souběžná instalace různých verzí sady Visual Studio

Visual Studio můžete nainstalovat do počítače, ve které je starší nebo novější verze sady Visual Studio, která je již nainstalovaná.

::: moniker range="vs-2017"

Před instalací verzí vedle sebe zkontrolujte následující podmínky:

* Pokud používáte Visual Studio 2017 k otevření řešení, které bylo vytvořeno v Sadě Visual Studio 2015, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2017.

* Pokud se pokusíte pomocí Visual Studia 2017 otevřít řešení, které bylo vytvořeno v sadě Visual Studio 2015 nebo starší verze, bude pravděpodobně nutné upravit vaše projekty a soubory tak, aby byly kompatibilní s Visual Studio 2017. Další informace naleznete na stránce [Port, migrate a upgrade aplikace Visual Studio Projects.](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)

::: moniker-end

::: moniker range=">= vs-2019"

Před instalací verzí vedle sebe zkontrolujte následující podmínky:

* Pokud používáte Visual Studio 2019 k otevření řešení, které bylo vytvořeno v Sadě Visual Studio 2017, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2019.

* Pokud se pokusíte pomocí Visual Studia 2019 otevřít řešení, které bylo vytvořeno v sadě Visual Studio 2017 nebo starší verze, bude pravděpodobně nutné upravit vaše projekty a soubory tak, aby byly kompatibilní s Visual Studio 2019. Další informace naleznete na stránce [Port, migrate a upgrade aplikace Visual Studio Projects.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

* Pokud odinstalujete verzi sady Visual Studio v počítači, který má nainstalovanou více než jednu verzi, budou přidružení souborů sady Visual Studio odebrána pro všechny verze.

* Visual Studio automaticky neupgraduje rozšíření, protože ne všechna rozšíření jsou kompatibilní. Rozšíření je nutné přeinstalovat z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo vydavatele softwaru.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Verze rozhraní .NET Framework a souběžné instalace

Projekty Visual Basic, Visual C# a Visual F# používají možnost **Cílové rozhraní** v **Návrháři projektu** k určení, kterou verzi rozhraní .NET Framework používá projekt. U projektu jazyka C++ můžete ručně změnit cílovou architekturu úpravou souboru .vcxproj. Další informace naleznete v části Kompatibilita verzí na stránce [rozhraní .NET Framework.](/dotnet/framework/migration-guide/version-compatibility)

Při vytváření projektu můžete určit, kterou verzi rozhraní .NET Framework cílí projekt v seznamu **rozhraní .NET Framework** v dialogovém okně **Nový projekt.**

Informace o jazyce naleznete v příslušném tématu v následující tabulce.

::: moniker range="vs-2017"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Vývoj s Visual F# v sadě Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Postup: Úprava cílového rozhraní a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md?view=vs-2017)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Vytváření izolovaných aplikací C/C++ a souběžných sestav](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Vývoj s Visual F# v sadě Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Postup: Úprava cílového rozhraní a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Vytváření izolovaných aplikací C/C++ a souběžných sestav](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
