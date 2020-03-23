---
title: Instalace analyzátorů FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508768"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalace analyzátorů FxCop v sadě Visual Studio

Společnost Microsoft vytvořila sadu analyzátorů s názvem [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), která obsahuje nejdůležitější pravidla "FxCop" z starší analýzy. Tyto analyzátory mimo jiné kontrolují problémy se zabezpečením, výkonem a návrhem.

Můžete nainstalovat tyto Analyzátory FxCop buď jako balíček NuGet nebo jako rozšíření VSIX do Sady Visual Studio. Chcete-li se dozvědět o výhody a nevýhody každého, najdete v tématu [NuGet balíček vs VSIX rozšíření](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Balíček NuGet

::: moniker range=">=vs-2019"

Ve Visual Studiu 2019 verze 16.3 a novější, můžete nainstalovat [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet balíček přímo ze stránky vlastností analýzy kódu projektu:

1. Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení**, vyberte **Vlastnosti**a pak vyberte kartu **Analýza kódu.**

   ![Instalace balíčku analyzátorů FxCop ze stránky vlastností v sadě Visual Studio](media/install-fxcop-properties-page.png)

2. Vyberte **Install** (Nainstalovat).

   Visual Studio nainstaluje nejnovější verzi balíčku Microsoft.CodeAnalysis.FxCopAnalyzers. Sestavení se zobrazí v **Průzkumníku řešení** v části **Analyzátory** > **Analyzers**odkazů .

   ![Uzel analyzátorů v Průzkumníku řešení](media/solution-explorer-analyzers-node.png)

Pokud používáte starší verzi Visual Studia 2019, nainstalujte balíček pomocí [konzoly Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) nebo [uhlavního nastavení Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Určete, kterou verzi balíčku analyzátoru](#fxcopanalyzers-package-versions) chcete nainstalovat, na základě vaší verze sady Visual Studio.

2. Nainstalujte balíček v sadě Visual Studio pomocí [konzoly Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) nebo [pomocí uhlavního nastavení Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Stránka nuget.org pro každý balíček analyzátoru zobrazuje příkaz, který chcete vložit do **konzoly Správce balíčků**. K dispozici je i praktické tlačítko pro kopírování textu do schránky.
   >
   > ![NuGet.org stránka s příkazem Konzola Správce balíčků](media/nuget-package-manager-command.png)

   Sestavení analyzátoru jsou nainstalována a zobrazí se v **Průzkumníku řešení** v části **Analyzátory** > **Analyzers**odkazů .

::: moniker-end

### <a name="custom-installation"></a>Vlastní instalace

Pro vlastní instalaci, například k určení jiné verze balíčku, vyberte tlačítko tři tečky (...) na stránce vlastností analýzy kódu projektu. Toto tlačítko otevře správce balíčků NuGet s "Microsoft.CodeAnalysis.FxCopAnalyzers" jako vyhledávací řetězec.

![Instalace vlastního balíčku analyzátorů FxCop ze stránky vlastností v sadě Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> [Určete, kterou verzi balíčku analyzátoru](#fxcopanalyzers-package-versions) chcete nainstalovat, na základě vaší verze sady Visual Studio. Balíček můžete také nainstalovat z [uhlavního systému Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Verze balíčků FxCopAnalyzers

Pomocí následujících pokynů určete, kterou verzi balíčku analyzátorů FxCop chcete nainstalovat pro vaši verzi sady Visual Studio:

| Verze sady Visual Studio | Verze balíčku analyzátoru FxCop |
| - | - |
| Visual Studio 2019 (všechny verze)<br />Visual Studio 2017 verze 15.8 a novější | [nejnovější](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 verze 15.5 až 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 verze 15.3 až 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 verze 15.0 až 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Aktualizace Visual Studia 2015 2 a 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>Vsix

::: moniker range="vs-2017"

Ve Visual Studiu 2017 verze 15.5 a novější můžete nainstalovat rozšíření [Microsoft Code Analysis 2017,](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) které obsahuje všechny analyzátory FxCop pro spravované projekty.

1. V sadě Visual Studio vyberte **rozšíření a aktualizace** **nástrojů** > .

   Otevře se dialogové okno **Rozšíření a aktualizace.**

   > [!NOTE]
   > Případně si stáhněte rozšíření přímo z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Rozbalte **online** v levém podokně a vyberte **Visual Studio Marketplace**.

3. Do vyhledávacího pole zadejte "analýzu kódu" a vyhledejte rozšíření **Microsoft Code Analysis 2017.**

   ![Rozšíření analýzy kódu Microsoftu 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Rozšíření [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) obsahuje všechny analyzátory FxCop pro spravované projekty. Instalace tohoto rozšíření:

1. V sadě Visual Studio vyberte **rozšíření** > **Spravovat rozšíření**.

   Otevře se dialogové okno **Spravovat rozšíření.**

   > [!NOTE]
   > Případně si stáhněte rozšíření přímo z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Rozbalte **online** v levém podokně a vyberte **Visual Studio Marketplace**.

3. Do vyhledávacího pole zadejte "analýzu kódu" a vyhledejte rozšíření **Microsoft Code Analysis 2019.**

   ![Rozšíření analýzy kódu Microsoftu 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Vyberte **Download** (Stáhnout).

   Rozšíření je staženo.

5. Výběrem **možnosti OK** zavřete dialogové okno a zavřete všechny instance sady Visual Studio a spusťte **Instalační službu VSIX**.

   Otevře se dialogové okno **Instalační služba VSIX.**

   ::: moniker range="vs-2017"

   ![Instalační program VSIX pro analýzu kódu společnosti Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Chcete-li spustit instalaci, vyberte **změnit.**

   Po minutě nebo dvou se instalace dokončí.

7. Vyberte **Zavřít**a znovu spusťte Visual Studio.

::: moniker range="vs-2017"

Chcete-li zkontrolovat, zda je rozšíření nainstalováno, vyberte **možnost Rozšíření a** > **aktualizace nástrojů**. V dialogovém okně **Rozšíření a aktualizace** vyberte kategorii **Nainstalováno** vlevo a potom vyhledejte rozšíření podle názvu.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete zkontrolovat, jestli je rozšíření nainstalované, vyberte **Spravovat** > **rozšíření**. V dialogovém okně **Spravovat rozšíření** vyberte kategorii **Nainstalováno** vlevo a potom ji vyhledejte podle názvu.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v sadě Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Použití analyzátorů kódu v sadě Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrace ze starší analýzy do analyzátorů kódu](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
