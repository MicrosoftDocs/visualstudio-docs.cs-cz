---
title: Analýza kódu FxCop a analyzátory FxCop
ms.date: 09/06/2018
description: Pochopte rozdíl mezi staršími analyzátory FxCop a FxCop v aplikaci Visual Studio. Podívejte se na odpovědi na otázky týkající se použití těchto analyzátorů.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e6768ad7f1ee87f75592c736b03bf6fd64e28c2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348955"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Nejčastější dotazy k analyzátorům FxCop a FxCop

Může být trochu matoucí pochopit rozdíly mezi staršími analyzátory FxCop a FxCop. Tento článek se zaměřuje na některé otázky, které můžete mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaký je rozdíl mezi staršími analyzátory FxCop a FxCop?

Starší verze FxCop spustí analýzu po sestavení u zkompilovaného sestavení. Spouští se jako samostatný spustitelný soubor s názvem **FxCopCmd.exe**. FxCopCmd.exe načte zkompilované sestavení, spustí analýzu kódu a pak nahlásí výsledky (nebo *diagnostiku* ).

Analyzátory FxCop jsou založené na .NET Compiler Platform ("Roslyn"). [Nainstalujete je jako balíček NuGet](install-fxcop-analyzers.md#nuget-package) , na který se odkazuje v projektu nebo řešení. Analyzátory FxCop spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Analyzátory FxCop se hostují v procesu kompilátoru, a to buď **csc.exe** , nebo **vbc.exe** , a při sestavení projektu spusťte analýzu. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

> [!NOTE]
> [Analyzátory FxCop můžete nainstalovat také jako rozšíření sady Visual Studio](install-fxcop-analyzers.md#vsix). V tomto případě se analyzátory spustí při psaní v editoru kódu, ale nespustí se v době sestavení. Pokud chcete spustit analyzátory FxCop jako součást průběžné integrace (CI), nainstalujte je místo toho jako balíček NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Spouští se v příkazu Run Code Analysis analyzátory FxCop?

Před vydáním sady Visual Studio 2019 16,5 vydaná při výběru **analyzovat**  >  **kód spustit analýzu** provede starší analýzu. Spuštění sady Visual Studio 2019 16,5, možnost **Spustit příkaz Analýza kódu** spustí analyzátory založené na Roslyn pro vybraný projekt nebo řešení. Pokud jste nainstalovali analyzátory FxCop založené na Roslyn, budou také provedeny. Další informace najdete v tématu [Postupy: ruční spuštění analýzy kódu pro spravovaný kód](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Spouští se v nástroji RunCodeAnalysis MSBuild rutiny analyzátorů?

Ne. Vlastnost **RunCodeAnalysis** v souboru projektu (například *. csproj* ) se používá pouze ke spuštění starší verze FxCop. Spustí úlohu MSBuild po sestavení, která vyvolá **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Jak tedy spustím analyzátory FxCop?

Pokud chcete spustit analyzátory FxCop, nejdřív pro ně [nainstalujte balíček NuGet](install-fxcop-analyzers.md) . Pak Sestavte projekt nebo řešení ze sady Visual Studio nebo pomocí nástroje MSBuild. Upozornění a chyby, které generují analyzátory FxCop, se zobrazí v okně **Seznam chyb** nebo v příkazovém okně.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Zobrazí se upozornění CA0507 i po instalaci balíčku NuGet analyzátory FxCop.

Pokud jste nainstalovali analyzátory FxCop, ale nadále se zobrazí upozornění CA0507 **"" spuštění analýzy kódu "se už nepoužívá**. doporučujeme, abyste v [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) nastavili vlastnost MSBuild **RunCodeAnalysis** na **hodnotu NEPRAVDA**. V opačném případě se starší verze analýzy spustí po každém sestavení.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Která pravidla se rozšířila na analyzátory FxCop?

Informace o tom, která pravidla analýzy starší verze byly [PřeFxCopa na analyzátory](install-fxcop-analyzers.md), najdete v tématu [stav portu FxCop pravidla](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Upozornění analýzy kódu jsou považována za chyby.

Pokud váš projekt používá možnost sestavení k ponechání upozornění jako chyby, může se zobrazit upozornění analyzátoru FxCop jako chyby. Chcete-li zabránit tomu, aby upozornění analýzy kódu byla považována za chyby, postupujte podle pokynů v [části Nejčastější dotazy k analýze kódu](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrace na analyzátory FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Instalace analyzátorů FxCop](install-fxcop-analyzers.md)
