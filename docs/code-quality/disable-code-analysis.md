---
title: Vypnout analýzu kódu
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431394"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Jak zakázat analýzu zdrojového kódu pro spravovaný kód

::: moniker range=">=vs-2019"

Tato stránka vám pomůže zakázat analýzu kódu v sadě Visual Studio. Existují omezení, co můžete zakázat, a postup pro vypnutí analýzy kódu se liší v závislosti na několika faktorech:

- Typ projektu (.NET Core/Standard versus .NET Framework)

  .NET Core a .NET Standardní projekty mají možnosti na stránce vlastností analýzy kódu, které umožňují vypnout analýzu kódu z analyzátorů nainstalovaných jako balíček NuGet. Další informace naleznete v tématu [.NET Core a .NET Standard projekty](#net-core-and-net-standard-projects). Chcete-li vypnout analýzu zdrojového kódu pro projekty rozhraní .NET Framework, přečtěte si informace [o projektech rozhraní .NET Framework](#net-framework-projects).

- Analýza zdroje versus starší analýza

  Toto téma se týká analýzy zdrojového kódu a nikoli starší (binární) analýzy. Informace o zakázání starší analýzy naleznete v tématu [How to: Enable and disable legacy code analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Projekty .NET Core a .NET Standard

Počínaje Visual Studio 2019 verze 16.3, existují dvě zaškrtávací políčka k dispozici na stránce vlastností analýzy kódu, které umožňují řídit, zda analyzátory spustit v době sestavení a čas návrhu. Tyto možnosti jsou specifické pro projekt.

![Povolení nebo zakázání analýzy živého kódu nebo při sestavení v sadě Visual Studio](media/run-on-build-run-live-analysis.png)

Chcete-li otevřít tuto stránku, klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**. Vyberte kartu **Analýza kódu.**

- Chcete-li zakázat zdrojovou analýzu v době sestavení, zaškrtněte políčko **Spustit na sestavení** možnost.
- Chcete-li zakázat analýzu živého zdroje, zaškrtněte políčko **Spustit analýzu živého** provozu.

> [!NOTE]
> Počínaje Visual Studio 2019 verze 16.5, pokud dáváte přednost pracovní postup spuštění analýzy kódu na vyžádání, můžete zakázat spuštění analyzátoru během živé analýzy a/nebo sestavení a ručně spustit analýzu kódu jednou na projektu nebo řešení na vyžádání. Informace o ručním spuštění analýzy kódu naleznete v [tématu How to: Run Code Analysis Manually for Managed Code](how-to-run-code-analysis-manually-for-managed-code.md).  

## <a name="net-framework-projects"></a>Projekty rozhraní .NET Framework

Chcete-li vypnout analýzu zdrojového kódu pro analyzátory, přidejte do [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file)jednu nebo více následujících vlastností MSBuild .

| MSBuild, vlastnost | Popis | Výchozí |
| - | - | - |
| `RunAnalyzersDuringBuild` | Určuje, zda jsou analyzátory spuštěny v době sestavení. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Určuje, zda analyzátory analyzují kód živě v době návrhu. | `true` |
| `RunAnalyzers` | Zakáže analyzátory v době sestavení i návrhu. Tato vlastnost má `RunAnalyzersDuringBuild` přednost `RunAnalyzersDuringLiveAnalysis`před a . | `true` |

Příklady:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Zdrojová analýza

[Zdrojovou analýzu](roslyn-analyzers-overview.md) nelze v sadě Visual Studio 2017 vypnout. Pokud chcete vymazat chyby analyzátoru ze seznamu chyb, můžete potlačit všechna aktuální porušení výběrem **možnosti Analyzovat** > **spustit analýzu kódu a potlačit aktivní problémy** na řádku nabídek. Další informace naleznete v tématu [Potlačení porušení](use-roslyn-analyzers.md#suppress-violations).

Počínaje Visual Studio 2019 verze 16.3, můžete vypnout analýzu zdrojového kódu nebo spustit na vyžádání. Zvažte upgrade na Visual Studio 2019.

## <a name="legacy-analysis"></a>Starší verze analýzy

Můžete zakázat starší, analýza sestavení na stránce **vlastností analýzy kódu.** Další informace naleznete v [tématu How to: Enable and disable legacy code analysis](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Viz také

- [Potlačit porušení](use-roslyn-analyzers.md#suppress-violations)
- [Postup: Povolení a zakázání analýzy starších kódů](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
