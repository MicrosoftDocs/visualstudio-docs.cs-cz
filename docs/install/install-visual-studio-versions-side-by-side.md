---
title: Souběžná instalace různých verzí sady Visual Studio
description: Přečtěte si, jak nainstalovat Visual Studio na počítač, který má už nainstalovanou starší nebo novější verzi sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.openlocfilehash: 0814b6ebfacd5b4cf24d0f451967903b9551808f
ms.sourcegitcommit: 22789927ec8e877b7d2b67a555d6df97d84103e0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2021
ms.locfileid: "105981274"
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

Při upgradu z jedné dílčí verze sady Visual Studio na další bude instalační program sady Visual Studio ve výchozím nastavení aktualizovat aktuální instalaci na nejnovější verzi v tomto kanálu. Předpokládejme například, že 16.9.4 byl právě vydán. Instalační program se pokusí nahradit vaši aktuální instalaci 16.9.3 (nebo nižší) pomocí 16.9.4, protože obě verze jsou součástí kanálu pro vydání sady [Visual Studio 2019](https://docs.microsoft.com/visualstudio/productinfo/release-rhythm). Nahrazení starší verze novější verzí během aktualizace pomáhá zajistit, že starší verze sady Visual Studio nezabírají místo na svém počítači. V některých případech ale může být užitečné nainstalovat různé dílčí vydané verze sady Visual Studio vedle sebe. Můžete například chtít, aby 16.9.3 i 16.9.4 ve stejném počítači. 

::: moniker range="vs-2017"

1. Stáhněte si nejnovější zaváděcí nástroj pro sadu Visual Studio 2017 verze 15,9 ze stránky [předchozích verzí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) pro verzi, kterou chcete nainstalovat souběžně s existující verzí sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Stáhněte si soubor zaváděcího nástroje sady Visual Studio 2019 buď na [stránce stažení sady Visual](https://visualstudio.microsoft.com/downloads) Studio, nebo na stránce verze sady [Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) pro podverzi, kterou chcete nainstalovat souběžně s existující verzí sady Visual Studio.

::: moniker-end


2. Otevřete příkazový řádek v režimu správce. Provedete to tak, že otevřete nabídku Start systému Windows, zadáte "cmd", kliknete pravým tlačítkem na výsledek hledání příkazového řádku a vyberete **Spustit jako správce**. V příkazovém řádku změňte adresář na složku, ve které se nachází soubor zaváděcího nástroje sady Visual Studio.

::: moniker range="vs-2017"

3. Spusťte následující příkaz, který určí novou cestu ke složce pro umístění instalace a nahradí název souboru. exe odpovídajícím názvem zaváděcího programu pro verzi sady Visual Studio, kterou instalujete. Název souboru. exe by měl odpovídat nebo být podobný jednomu z následujících souborů:

   * vs_enterprise.exe pro Visual Studio Enterprise
   * vs_professional.exe pro Visual Studio Professional

::: moniker-end

::: moniker range="vs-2019"

3. Spusťte následující příkaz, který určí novou cestu ke složce pro umístění instalace a nahradí název souboru. exe odpovídajícím názvem zaváděcího programu pro verzi sady Visual Studio, kterou instalujete. Název souboru. exe by měl odpovídat nebo být podobný jednomu z následujících souborů:

   * vs_enterprise.exe pro Visual Studio Enterprise
   * vs_professional.exe pro Visual Studio Professional
   * vs_community.exe pro Visual Studio Community

::: moniker-end 
  
   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
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
