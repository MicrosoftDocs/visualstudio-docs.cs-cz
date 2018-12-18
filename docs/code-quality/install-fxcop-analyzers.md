---
title: Instalace analyzátorů FxCop
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7690d1c67797c3a13dc22364d93d8af686e4f90c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892048"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Nainstalujte analyzátory FxCop v sadě Visual Studio

Microsoft vytvořil sadu analyzátory, volá [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), který obsahuje nejdůležitější "FxCop" pravidla ze statické analýzy kódu, převést na analyzátory Roslyn. Tyto analyzátory zkontrolovat kód pro zabezpečení, výkonu a problémy návrhu, mimo jiné.

Tyto analyzátory FxCop můžete nainstalovat jako balíček NuGet nebo jako rozšíření VSIX do sady Visual Studio. Další informace o výhody a nevýhody jednotlivých najdete v tématu [vs balíčku NuGet. Rozšíření VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Chcete-li nainstalovat analyzátory FxCop jako balíček NuGet

1. [Určit verzi balíčku, která analyzer](#fxcopanalyzers-package-versions) k instalaci, podle vaší verze sady Visual Studio.

2. Nainstalujte balíček v sadě Visual Studio, buď pomocí [Konzola správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) nebo [uživatelské rozhraní Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Na stránce nuget.org pro každý balíček Analyzátor se dozvíte, příkaz a vložte do **Konzola správce balíčků**. Je i užitečný tlačítko ke zkopírování textu do schránky.
   >
   > ![NuGet.org stránky zobrazující příkaz konzoly Správce balíčků](media/nuget-package-manager-command.png)

   Sestavení analyzátoru jsou nainstalovány a jsou uvedeny v **Průzkumníka řešení** pod **odkazy** > **analyzátory**.

   ![Analyzátory uzlu v Průzkumníkovi řešení](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Verze balíčku FxCopAnalyzers

Určení verze balíčku analyzátory FxCop instalace pro vaši verzi sady Visual Studio pomocí následujících pokynů:

| Verze Visual Studio | Verze balíčku analyzátor FxCop |
| - | - |
| Visual Studio 2017 verze 15.5 nebo novější | 2.6.2, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2 |
| Visual Studio 2017 verze 15.3 k 15.4 | 2.3.0-Beta1, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1 |
| Visual Studio 2017 verze 15.0: 15.2 | 2.0.0-Beta2, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2 |
| Visual Studio 2015 update 2 a 3 | Verze 1.2.0-beta2, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2 |
| Visual Studio 2015 Update 1 | Verze 1.1.0, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1. |
| Visual Studio 2015 RTW | Verze 1.0.1, například https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1 |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Chcete-li nainstalovat analyzátory FxCop jako rozšíření VSIX

V sadě Visual Studio 2017 verze 15.5 nebo novější, můžete nainstalovat [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) rozšíření, které obsahuje všechny analyzátory FxCop pro spravované projekty.

1. V sadě Visual Studio, vyberte **nástroje** > **rozšíření a aktualizace**.

   **Rozšíření a aktualizace** zobrazí se dialogové okno.

   > [!NOTE]
   > Můžete také stáhnout přímo z rozšíření [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Rozbalte **Online** v levém podokně a pak vyberte **Visual Studio Marketplace**.

1. Do vyhledávacího pole zadejte "analýza kódu" a vyhledejte **Microsoft Code Analysis 2017** rozšíření.

   ![Rozšíření Microsoft analýzy kódu](media/extensions-and-updates-code-analysis.png)

1. Vyberte **Stáhnout**.

   Rozšíření je stažen.

1. Vyberte **OK** dialogové okno zavřete a pak zavřete všechny instance sady Visual Studio ke spuštění **instalátor VSIX**.

   **Instalátor VSIX** zobrazí se dialogové okno.

   ![Instalátor VSIX pro analýzu kódu Microsoft](media/vsix-installer-code-analysis.png)

1. Vyberte **změnit** spusťte instalaci.

1. Po jedné až dvou minutách dokončení instalace. Vyberte **Zavřít**.

1. Znovu otevřete Visual Studio.

Pokud chcete zkontrolovat, zda je rozšíření nainstalované, vyberte **nástroje** > **rozšíření a aktualizace**. V **rozšíření a aktualizace** dialogové okno, vyberte **nainstalováno** kategorie na levé straně a poté vyhledejte rozšíření podle názvu.

## <a name="see-also"></a>Viz také:

- [Přehled analyzátory Roslyn v sadě Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Používání analyzátorů Roslyn v sadě Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrace z FxCop do analyzátory Roslyn](../code-quality/fxcop-analyzers.yml)