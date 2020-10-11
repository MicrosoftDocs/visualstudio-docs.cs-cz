---
title: Souběžná instalace různých verzí sady Visual Studio
description: Přečtěte si, jak nainstalovat Visual Studio na počítač, který má už nainstalovanou starší nebo novější verzi sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
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
ms.openlocfilehash: ff62f07f3b1c5cc72488320b05d6ff9649fb5795
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928629"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Souběžná instalace různých verzí sady Visual Studio

Sadu Visual Studio můžete nainstalovat na počítači, ve kterém je již nainstalována dřívější nebo novější verze sady Visual Studio.

::: moniker range="vs-2017"

Než nainstalujete verze vedle sebe, Projděte si následující podmínky:

* Pokud používáte Visual Studio 2017 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2015, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2017.

* Pokud se pokusíte použít Visual Studio 2017 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2015 nebo v dřívější verzi, může být nutné upravit projekty a soubory tak, aby byly kompatibilní se sadou Visual Studio 2017. Další informace najdete na stránce [port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true) .

::: moniker-end

::: moniker range=">= vs-2019"

Než nainstalujete verze vedle sebe, Projděte si následující podmínky:

* Pokud používáte Visual Studio 2019 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2017, můžete později otevřít a upravit řešení znovu v předchozí verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2019.

* Pokud se pokusíte použít Visual Studio 2019 k otevření řešení, které bylo vytvořeno v aplikaci Visual Studio 2017 nebo v dřívější verzi, může být nutné upravit projekty a soubory tak, aby byly kompatibilní se sadou Visual Studio 2019. Další informace najdete na stránce [port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md) .

::: moniker-end

* Pokud odinstalujete verzi sady Visual Studio na počítači, ve kterém je nainstalována více než jedna verze, přidružení souborů pro sadu Visual Studio budou odebrána pro všechny verze.

* Visual Studio neupgraduje automaticky rozšíření, protože ne všechna rozšíření jsou kompatibilní. Rozšíření je nutné přeinstalovat z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo z vydavatele softwaru.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Souběžná instalace menších verzí sady Visual Studio

Při upgradu z jedné dílčí verze sady Visual Studio na další bude instalační program sady Visual Studio aktualizovat vaši aktuální instalaci na další verzi v tomto kanálu ve výchozím nastavení. Například při instalaci 16.6.4 ve verzi Preview se instalační program pokusí nahradit vaši aktuální instalaci 16.6.3 Preview, protože obě verze jsou v kanálu verze 16,6 Preview. To pomáhá zajistit, že starší verze sady Visual Studio nezabírají místo na svém počítači. V některých specifických případech může být užitečné nainstalovat dílčí verze vedle sebe. V našem příkladu by to znamenalo, že 16.6.3 i 16.6.4 ve stejném počítači.

1. Stáhněte si [soubor zaváděcího nástroje sady Visual Studio](/visualstudio/releases/2019/history#installing-an-earlier-release) pro podverzi, kterou byste chtěli nainstalovat souběžně s vašimi stávajícími verzemi sady Visual Studio.
2. Otevřete příkazový řádek v režimu správce. Provedete to tak, že otevřete nabídku Start systému Windows, zadáte "cmd", kliknete pravým tlačítkem na výsledek hledání příkazového řádku a vyberete **Spustit jako správce**. V příkazovém řádku změňte adresář na složku, ve které se nachází soubor zaváděcího nástroje sady Visual Studio.
3. Spusťte následující příkaz, který určí novou cestu ke složce pro umístění instalace a nahradí název souboru. exe odpovídajícím názvem zaváděcího programu pro verzi sady Visual Studio, kterou instalujete. Název souboru. exe by měl odpovídat nebo být podobný jednomu z následujících souborů:
   * vs_community.exe pro Visual Studio Community
   * vs_professional.exe pro Visual Studio Professional
   * vs_enterprise.exe pro Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Pomocí dialogových oken instalačního programu vyberte součásti, které pro instalaci potřebujete. Další informace najdete v tématu [instalace sady Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework verze a souběžné instalace

Projekty Visual Basic, Visual C# a Visual F# používají k určení verze .NET Framework, které projekt používá, možnost **cílové rozhraní** v **Návrháři projektu** . V případě projektu jazyka C++ lze cílový rámec ručně změnit úpravou souboru. vcxproj. Další informace najdete v tématu [Kompatibilita verzí](/dotnet/framework/migration-guide/version-compatibility) na stránce .NET Framework.

Při vytváření projektu můžete určit, která verze .NET Framework projekt cílí v seznamu **.NET Framework** v dialogovém okně **Nový projekt** .

Informace specifické pro jazyk najdete v příslušném tématu v následující tabulce.

::: moniker range="vs-2017"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C# | [Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true) |
| Visual F# | [Vývoj pomocí Visual F# v aplikaci Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true) |
|C++ | [Postupy: Změna cílové architektury a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Jazyk | Téma |
|--------------|-----------|
| Visual Basic | [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Vývoj pomocí Visual F# v aplikaci Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Postupy: Změna cílové architektury a sady nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Port, migrace a upgrade projektů sady Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
