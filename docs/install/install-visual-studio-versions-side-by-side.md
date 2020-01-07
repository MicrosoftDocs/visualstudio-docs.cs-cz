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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62acf1c5e8cab960d4b670f7a05481644e9ffc1e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594081"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Souběžná instalace různých verzí sady Visual Studio

Sadu Visual Studio můžete nainstalovat na počítači, ve kterém je již nainstalována dřívější nebo novější verze sady Visual Studio.

::: moniker range="vs-2017"

Než nainstalujete verze vedle sebe, Projděte si následující podmínky:

* Pokud používáte Visual Studio 2017 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2015, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2017.

* Pokud se pokusíte použít Visual Studio 2017 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2015 nebo v dřívější verzi, může být nutné upravit projekty a soubory tak, aby byly kompatibilní se sadou Visual Studio 2017. Další informace najdete na stránce [port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) .

::: moniker-end

::: moniker range=">= vs-2019"

Než nainstalujete verze vedle sebe, Projděte si následující podmínky:

* Pokud používáte Visual Studio 2019 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2017, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2019.

* Pokud se pokusíte použít Visual Studio 2019 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2017 nebo v dřívější verzi, může být nutné upravit projekty a soubory tak, aby byly kompatibilní se sadou Visual Studio 2019. Další informace najdete na stránce [port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md) .

::: moniker-end

* Pokud odinstalujete verzi sady Visual Studio na počítači, ve kterém je nainstalována více než jedna verze, přidružení souborů pro sadu Visual Studio budou odebrána pro všechny verze.

* Visual Studio neprovádí automatický upgrade rozšíření vzhledem k tomu, že ne všechna rozšíření jsou kompatibilní. Je třeba přeinstalovat rozšíření od [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo vydavatele softwaru.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework verze a souběžné instalace

Projekty Visual Basic, C#vizuálu a Visual F# používají možnost **target Framework** v **Návrháři projektu** k určení verze .NET Framework, kterou projekt používá. Pro projekt jazyka C++ můžete ručně změnit cílové rozhraní úpravou souboru .vcxproj. Další informace najdete v tématu [Kompatibilita verzí](/dotnet/framework/migration-guide/version-compatibility) na stránce .NET Framework.

Když vytvoříte projekt, můžete určit, kterou verzi rozhraní .NET Framework je projekt cílen v **rozhraní .NET Framework** v seznamu **nový projekt** dialogové okno.

Informace specifické pro jazyk najdete v příslušném tématu v následující tabulce.

::: moniker range="vs-2017"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Stránka Aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Vývoj s využitím vizuálu F# v aplikaci Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Postupy: Změna cílové architektury a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md?view=vs-2017)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [SestavováníC++ aplikací založených na jazyce C/Isolated a souběžných sestavení](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Stránka Aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Vývoj s využitím vizuálu F# v aplikaci Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Postupy: Změna cílové architektury a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [SestavováníC++ aplikací založených na jazyce C/Isolated a souběžných sestavení](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
