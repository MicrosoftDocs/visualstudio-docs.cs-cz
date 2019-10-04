---
title: Vypnout analýzu kódu
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d769accce87b789b207d9cf337d5b9adc46e413e
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71963324"
---
# <a name="how-to-disable-code-analysis-in-visual-studio"></a>Postup zakázání analýzy kódu v aplikaci Visual Studio

::: moniker range=">=vs-2019"

Tato stránka vám pomůže zakázat analýzu kódu v aplikaci Visual Studio. Existují určitá omezení, která je možné zakázat, a postup pro vypnutí analýzy kódu se liší v závislosti na několika faktorech:

- Typ projektu (.NET Core/Standard oproti .NET Framework)

  Projekty .NET Core a .NET Standard mají možnosti na stránce vlastností analýzy kódu, která umožňuje vypnout analýzu kódu z analyzátorů nainstalovaných jako balíček NuGet. Další informace naleznete v tématu [projekty .NET Core a .NET Standard](#net-core-and-net-standard-projects). Chcete-li vypnout analýzu zdrojového kódu pro projekty .NET Framework, přečtěte si téma [.NET Framework projekty](#net-framework-projects).

- Balíček NuGet analyzátoru versus VSIX nebo integrované analyzátory

  V současné době nemůžete zakázat analýzu živých kódů pro integrované analyzátory, například ID pravidla IDE0067. Podobně nemůžete zakázat analýzu živých kódů pro analyzátory, které byly nainstalovány jako součást rozšíření aplikace Visual Studio (VSIX). Chcete-li potlačit chyby a upozornění z vestavěných analyzátorů založených na VSIX, vyberte možnost **analyzovat** > **sestavení a potlačit aktivní problémy** na řádku nabídek. *Můžete* zakázat živá a vestavěnou analýzu analyzátorů nainstalovaných jako součást balíčku NuGet.

- Analýza zdrojového kódu oproti starší analýze

  Toto téma se vztahuje na analýzu zdrojového kódu a nikoli na starší (binární) analýzu. Informace o zakázání starší verze analýzy najdete v tématu [How: Povolí nebo zakáže analýzu staršího kódu @ no__t-0.

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core a .NET Standard

Počínaje verzí Visual Studio 2019 verze 16,3 jsou k dispozici dvě zaškrtávací políčka na stránce vlastností analýzy kódu, která umožňuje určit, zda jsou analyzátory založené na NuGet spuštěny v době sestavení a v době návrhu. Tyto možnosti jsou specifické pro konkrétní projekt.

![Povolení nebo zakázání živé analýzy kódu nebo sestavení v aplikaci Visual Studio](media/run-on-build-run-live-analysis.png)

Chcete-li otevřít tuto stránku, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Vyberte kartu **Analýza kódu** .

- Chcete-li zakázat analýzu zdrojů v čase sestavení, zrušte možnost **Spustit při sestavení** .
- Chcete-li zakázat živou analýzu zdroje, zrušte volbu možnosti **Spustit při analýze za provozu** .

> [!NOTE]
> Vestavěné analyzátory založené na VSIX budou nadále poskytovat živou analýzu kódu i v případě, že není zaškrtnuta rutina **Spustit při živé analýze** . Pokud chcete potlačit chyby a upozornění z těchto analyzátorů, vyberte možnost **analyzovat** > **sestavení a potlačit aktivní problémy** na řádku nabídek.

## <a name="net-framework-projects"></a>.NET Framework projekty

Pro vypnutí analýzy zdrojového kódu pro analyzátory nainstalované jako součást balíčku NuGet přidejte do [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file)jednu nebo více následujících vlastností nástroje MSBuild.

| Vlastnost MSBuild | Popis | Výchozí |
| - | - | - |
| `RunAnalyzersDuringBuild` | Určuje, zda analyzátory založené na NuGet jsou spouštěny v době sestavení. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Určuje, zda analyzátory založené na NuGet analyzují kód v době návrhu za provozu. | `true` |
| `RunAnalyzers` | Zakáže analyzátory založené na NuGet v době sestavování i návrhu. Tato vlastnost má přednost před `RunAnalyzersDuringBuild` a `RunAnalyzersDuringLiveAnalysis`. | `true` |

Příklady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Zdrojová analýza

Nemůžete vypnout [analýzu zdrojů](roslyn-analyzers-overview.md) v aplikaci Visual Studio 2017. Pokud chcete vymazat chyby analyzátoru z Seznam chyb, můžete potlačit všechna aktuální porušení výběrem možnosti **analyzovat** > **Spustit analýzu kódu a potlačit aktivní problémy** na řádku nabídek. Další informace najdete v tématu [potlačení porušení](use-roslyn-analyzers.md#suppress-violations).

Počínaje verzí Visual Studio 2019 verze 16,3 můžete vypnout analýzu zdrojového kódu na základě NuGet. Zvažte upgrade na Visual Studio 2019.

## <a name="legacy-analysis"></a>Starší verze analýzy

Starší verzi, analýzu času sestavení lze zakázat na stránce vlastností **analýzy kódu** . Další informace najdete v tématu [jak: Povolí nebo zakáže analýzu staršího kódu @ no__t-0.

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Potlačit porušení](use-roslyn-analyzers.md#suppress-violations)
- [Postupy: Povolit a zakázat analýzu starších kódů @ no__t-0
