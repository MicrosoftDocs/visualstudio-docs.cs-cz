---
title: Vypnout analýzu kódu
ms.date: 09/01/2020
description: Naučte se, jak vypnout analýzu zdrojového kódu sady Visual Studio v projektech .NET Core, .NET Standard a .NET Framework.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: e808cb623fa47c9971e1cdceb15a02b5bf46e901
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348551"
---
# <a name="disable-source-code-analysis-for-net"></a>Zakázat analýzu zdrojového kódu pro .NET

::: moniker range=">=vs-2019"

Tato stránka vám pomůže zakázat analýzu kódu v aplikaci Visual Studio. Existují určitá omezení, která je možné zakázat, a postup pro vypnutí analýzy kódu se liší v závislosti na několika faktorech:

- Typ projektu (.NET Core/Standard oproti .NET Framework)

  Projekty .NET Core a .NET Standard mají možnosti na stránce vlastností analýzy kódu, která umožňuje vypnout analýzu kódu z analyzátorů nainstalovaných jako balíček NuGet. Další informace naleznete v tématu [projekty .NET Core a .NET Standard](#net-core-and-net-standard-projects). Chcete-li vypnout analýzu zdrojového kódu pro projekty .NET Framework, přečtěte si téma [.NET Framework projekty](#net-framework-projects).

- Analýza zdrojového kódu oproti starší analýze

  Toto téma se vztahuje na analýzu zdrojového kódu a nikoli na starší (binární) analýzu. Informace o zakázání starší verze analýzy naleznete v tématu [How to: Enable and Disable Legacy Code Analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core a .NET Standard

Počínaje verzí Visual Studio 2019 verze 16,3 jsou k dispozici dvě zaškrtávací políčka na stránce vlastností analýzy kódu, která umožňuje určit, zda jsou analyzátory spouštěny v době sestavení a v době návrhu. Tyto možnosti jsou specifické pro projekt.

![Povolení nebo zakázání živé analýzy kódu nebo sestavení v aplikaci Visual Studio](media/run-on-build-run-live-analysis.png)

Chcete-li otevřít tuto stránku, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Vyberte kartu **Analýza kódu** .

- Chcete-li zakázat analýzu zdrojů v čase sestavení, zrušte možnost **Spustit při sestavení** .
- Chcete-li zakázat živou analýzu zdroje, zrušte volbu možnosti **Spustit při analýze za provozu** .

> [!NOTE]
> V rámci sady Visual Studio 2019 verze 16,5, pokud upřednostňujete pracovní postup provádění analýzy kódu na vyžádání, můžete vypnout provádění analyzátoru během živé analýzy nebo sestavit a ručně aktivovat analýzu kódu na základě projektu nebo řešení na vyžádání. Informace o ručním spuštění analýzy kódu naleznete v tématu [How to: Run Code Analysis for Managed Code Manual](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework projekty

Chcete-li vypnout analýzu zdrojového kódu pro analyzátory, přidejte do [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file)jednu nebo více následujících vlastností nástroje MSBuild.

| Vlastnost MSBuild | Popis | Výchozí |
| - | - | - |
| `RunAnalyzersDuringBuild` | Určuje, zda jsou analyzátory spouštěny v době sestavení. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Určuje, zda analyzátory analyzují kód v době návrhu za provozu. | `true` |
| `RunAnalyzers` | Zakáže analyzátory při sestavování i při návrhu. Tato vlastnost má přednost před `RunAnalyzersDuringBuild` a `RunAnalyzersDuringLiveAnalysis` . | `true` |

Příklady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Zdrojová analýza

Nemůžete vypnout [analýzu zdrojů](roslyn-analyzers-overview.md) v aplikaci Visual Studio 2017. Pokud chcete vymazat chyby analyzátoru z **Seznam chyb** , můžete potlačit všechna aktuální porušení výběrem možnosti **analyzovat**  >  **Spustit analýzu kódu a potlačit aktivní problémy** na řádku nabídek. Další informace najdete v tématu [potlačení porušení](use-roslyn-analyzers.md#suppress-violations).

Počínaje verzí Visual Studio 2019 verze 16,3 můžete vypnout analýzu zdrojového kódu nebo ji spustit na vyžádání. Zvažte upgrade na Visual Studio 2019.

## <a name="legacy-analysis"></a>Starší verze analýzy

Starší verzi, analýzu času sestavení lze zakázat na stránce vlastností **analýzy kódu** . Další informace najdete v tématu [Postup: povolení a zákaz analýzy starších kódů](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Viz také

- [Potlačit porušení](use-roslyn-analyzers.md#suppress-violations)
- [Postupy: povolení a zákaz analýzy starších kódů](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
