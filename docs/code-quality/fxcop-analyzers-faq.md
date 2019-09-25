---
title: Analýza kódu FxCop a analyzátory FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 42581e632c08550fce3cd685949401a155a060f6
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253184"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Nejčastější dotazy k analyzátorům FxCop a FxCop

Může být trochu matoucí pochopit rozdíly mezi staršími analyzátory FxCop a FxCop. Tento článek se zaměřuje na některé otázky, které můžete mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaký je rozdíl mezi staršími analyzátory FxCop a FxCop?

Starší verze FxCop spustí analýzu po sestavení u zkompilovaného sestavení. Spouští se jako samostatný spustitelný soubor s názvem **FxCopCmd. exe**. FxCopCmd. exe načte zkompilované sestavení, spustí analýzu kódu a pak nahlásí výsledky (nebo *diagnostiku*).

Analyzátory FxCop jsou založené na .NET Compiler Platform ("Roslyn"). [Nainstalujete je jako balíček NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) , na který se odkazuje v projektu nebo řešení. Analyzátory FxCop spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Analyzátory FxCop se hostují v procesu kompilátoru, a to buď **CSc. exe** , nebo **Vbc. exe**, a při sestavení projektu se spustí analýza. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

> [!NOTE]
> [Analyzátory FxCop můžete nainstalovat také jako rozšíření sady Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). V tomto případě se analyzátory spustí při psaní v editoru kódu, ale nespustí se v době sestavení. Pokud chcete spustit analyzátory FxCop jako součást průběžné integrace (CI), nainstalujte je místo toho jako balíček NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Spouští se v příkazu Run Code Analysis analyzátory FxCop?

Ne. Když vyberete možnost **analyzovat** > **spuštění analýzy kódu**, spustí se starší verze analýzy. **Spuštění analýzy kódu** nemá žádný vliv na analyzátory založené na Roslyn, včetně analyzátorů FxCop založených na Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Spouští se v nástroji RunCodeAnalysis MSBuild rutiny analyzátorů?

Ne. Vlastnost **RunCodeAnalysis** v souboru projektu (například *. csproj*) se používá pouze ke spuštění starší verze FxCop. Spustí úlohu MSBuild po sestavení, která vyvolá **FxCopCmd. exe**. Jedná se o ekvivalent výběru možnosti **analyzovat** > **běh kódu** v aplikaci Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Jak tedy spustím analyzátory FxCop?

Pokud chcete spustit analyzátory FxCop, nejdřív pro ně [nainstalujte balíček NuGet](install-fxcop-analyzers.md) . Pak Sestavte projekt nebo řešení ze sady Visual Studio nebo pomocí nástroje MSBuild. Upozornění a chyby, které generují analyzátory FxCop, se zobrazí v okně **Seznam chyb** nebo v příkazovém okně.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Zobrazí se upozornění CA0507 i po instalaci balíčku NuGet analyzátory FxCop.

Pokud jste nainstalovali analyzátory FxCop, ale nadále se zobrazí upozornění CA0507 **"" spuštění analýzy kódu "se už nepoužívá ve prospěch analyzátorů FxCop, které běží během sestavení**, možná budete muset nastavit vlastnost MSBuild **RunCodeAnalysis** v [projektu. soubor](../ide/solutions-and-projects-in-visual-studio.md#project-file) na **false**. V opačném případě se starší verze analýzy spustí po každém sestavení.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Která pravidla se rozšířila na analyzátory FxCop?

Informace o tom, která pravidla analýzy starší verze byly [PřeFxCopa na analyzátory](install-fxcop-analyzers.md), najdete v tématu [stav portu FxCop pravidla](fxcop-rule-port-status.md).

## <a name="see-also"></a>Viz také:

- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Začínáme s analyzátory](fxcop-analyzers.yml)
- [Nainstalovat analyzátory FxCop](install-fxcop-analyzers.md)
