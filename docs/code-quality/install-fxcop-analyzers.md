---
title: Instalace analyzátorů FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fec188ba61a7e4d3f27caad03f0a5d32b6758a32
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974995"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalace analyzátorů FxCop v aplikaci Visual Studio

Společnost Microsoft vytvořila sadu analyzátorů označovaných jako [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), které obsahují nejdůležitější pravidla "FxCop" ze starší verze analýzy. Tyto analyzátory kontrolují váš kód pro problémy se zabezpečením, výkonem a návrhem mimo jiné.

Tyto analyzátory FxCop můžete nainstalovat buď jako balíček NuGet, nebo jako rozšíření VSIX pro Visual Studio. Další informace o jednotlivých specialistech a jejich nevýhody najdete v tématu [NuGet Package vs. Rozšíření VSIX @ no__t-0.

## <a name="nuget-package"></a>Balíček NuGet

Balíček NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) můžete nainstalovat přímo ze stránky vlastností analýzy kódu projektu:

1. Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**, vyberte **vlastnosti**a pak vyberte kartu **Analýza kódu** .

   ![Instalace balíčku FxCop Analyzer z vlastností stránky v aplikaci Visual Studio](media/install-fxcop-properties-page.png)

2. Vyberte **Install** (Nainstalovat).

   Sada Visual Studio nainstaluje nejnovější verzi balíčku Microsoft. CodeAnalyzers. FxCopAnalyzers. Sestavení se zobrazí v **Průzkumník řešení** v části **odkazy** > **analyzátory**.

   ![Uzel analyzátorů v Průzkumník řešení](media/solution-explorer-analyzers-node.png)

### <a name="custom-installation"></a>Vlastní instalace

Pro vlastní instalaci, například chcete-li zadat jinou verzi balíčku, vyberte tlačítko se třemi tečkami (...) na stránce vlastností analýzy kódu projektu. Toto tlačítko otevře správce balíčků NuGet s názvem Microsoft. CodeAnalysis. FxCopAnalyzers jako hledaný řetězec.

![Instalace vlastních balíčků FxCop Analyzer z vlastností stránky v aplikaci Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Určete [verzi balíčku analyzátoru, která](#fxcopanalyzers-package-versions) se má nainstalovat, na základě vaší verze sady Visual Studio. Balíček můžete také nainstalovat z [uživatelského rozhraní Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Verze balíčků FxCopAnalyzers

Pomocí následujících pokynů určete, která verze balíčku FxCop Analyzer má být nainstalována pro vaši verzi sady Visual Studio:

| Verze Visual Studio | Verze balíčku analyzátoru FxCop |
| - | - |
| Visual Studio 2019 (všechny verze)<br />Visual Studio 2017 verze 15,8 a novější | [nejnovější](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 verze 15,5 až 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 verze 15,3 až 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 verze 15,0 až 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 Update 2 a 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Update 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

V systému Visual Studio 2017 verze 15,5 a novější můžete nainstalovat rozšíření [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) , které obsahuje všechny analyzátory FxCop pro spravované projekty.

1. V aplikaci Visual Studio vyberte **nástroje** > **rozšíření a aktualizace**.

   Otevře se dialogové okno **rozšíření a aktualizace** .

   > [!NOTE]
   > Další možností je stáhnout rozšíření přímo z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. V levém podokně rozbalte položku **online** a vyberte možnost **Visual Studio Marketplace**.

3. Do vyhledávacího pole zadejte text "Analýza kódu" a vyhledejte rozšíření **Microsoft Code analysis 2017** .

   ![Rozšíření Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Rozšíření [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) obsahuje všechny analyzátory FxCop pro spravované projekty. Instalace tohoto rozšíření:

1. V aplikaci Visual Studio vyberte **rozšíření** > **Spravovat rozšíření**.

   Otevře se dialogové okno **Spravovat rozšíření** .

   > [!NOTE]
   > Další možností je stáhnout rozšíření přímo z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. V levém podokně rozbalte položku **online** a vyberte možnost **Visual Studio Marketplace**.

3. Do vyhledávacího pole zadejte text "Analýza kódu" a vyhledejte rozšíření **Microsoft Code analysis 2019** .

   ![Rozšíření Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Vyberte **Stáhnout**.

   Rozšíření se stáhne.

5. Kliknutím na **tlačítko OK** zavřete dialogové okno a poté zavřete všechny instance aplikace Visual Studio a spusťte **instalační program VSIX**.

   Otevře se dialogové okno **instalátor VSIX** .

   ::: moniker range="vs-2017"

   ![Instalační program VSIX pro analýzu kódu Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Kliknutím na tlačítko **změnit** spusťte instalaci.

   Po jedné nebo dvou minutách se instalace dokončí.

7. Vyberte **Zavřít**a pak znovu otevřít Visual Studio.

::: moniker range="vs-2017"

Chcete-li ověřit, zda je rozšíření nainstalováno, vyberte možnost **nástroje** > **rozšíření a aktualizace**. V dialogovém okně **rozšíření a aktualizace** vyberte **nainstalovanou** kategorii na levé straně a potom vyhledejte rozšíření podle názvu.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li ověřit, zda je rozšíření nainstalováno, vyberte **rozšíření** > **Spravovat rozšíření**. V dialogovém okně **Spravovat rozšíření** vyberte v levé části kategorii **nainstalováno** a pak vyhledejte rozšíření podle názvu.

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Přehled analyzátorů kódu v aplikaci Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Použití analyzátorů kódu v aplikaci Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrace ze starší verze z analýz na analyzátory kódu](../code-quality/fxcop-analyzers.yml)
