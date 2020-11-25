---
title: FxCop Code Analysis (binární analýza) a analyzátory .NET (analýza zdroje)
ms.date: 09/06/2018
description: Pochopení rozdílu mezi staršími verzemi FxCop (binární analýza) a analyzátory .NET (analýza zdroje) v aplikaci Visual Studio. Podívejte se na odpovědi na otázky týkající se použití těchto analyzátorů.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d581ef60ebfe9ff5aeceae4c16ee4294eae5d850
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112226"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Nejčastější dotazy týkající se starších verzí FxCop a analyzátorů .NET

Může být trochu matoucí porozumět rozdílům mezi staršími FxCop (binární analýzou) a analyzátorem .NET (analýza zdroje). Tento článek se zaměřuje na některé otázky, které můžete mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Jaký je rozdíl mezi staršími verzemi FxCop a analyzátory .NET?

Starší verze FxCop spustí analýzu po sestavení u zkompilovaného sestavení. Spouští se jako samostatný spustitelný soubor s názvem **FxCopCmd.exe**. FxCopCmd.exe načte zkompilované sestavení, spustí analýzu kódu a pak nahlásí výsledky (nebo *diagnostiku*).

Analyzátory .NET jsou založené na .NET Compiler Platform ("Roslyn"). [Povolíte je ze sady .NET SDK nebo je nainstalujete jako balíček NuGet](install-net-analyzers.md) , na který odkazuje projekt nebo řešení. Analyzátory spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Analyzátory jsou hostovány v rámci procesu kompilátoru, buď **csc.exe** nebo **vbc.exe**, a při sestavení projektu spusťte analýzu. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Jaký je rozdíl mezi analyzátory FxCop a analyzátory .NET?

Analyzátory FxCop a analyzátory .NET .NET Compiler Platform odkazují na implementace analyzátoru pro FxCop pravidla certifikační autority ("Roslyn"). Před vydáním sady Visual Studio 2019 16,8 a .NET 5,0 byly tyto analyzátory dodávány jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Počínaje sadou Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Zvažte prosím možnost [migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Spouští příkaz run Code Analysis rutiny .NET Analyzer?

Před vydáním sady Visual Studio 2019 16,5 vydaná při výběru **analyzovat**  >  **kód spustit analýzu** provede starší analýzu. Spuštění sady Visual Studio 2019 16,5, možnost **Spustit příkaz Analýza kódu** spustí analyzátory založené na Roslyn pro vybraný projekt nebo řešení. Pokud jste nainstalovali analyzátory .NET, budou také provedeny. Další informace najdete v tématu [Postupy: ruční spuštění analýzy kódu pro spravovaný kód](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Spouští se v nástroji RunCodeAnalysis MSBuild rutiny analyzátorů?

Ne. Vlastnost **RunCodeAnalysis** v souboru projektu (například *. csproj*) se používá pouze ke spuštění starší verze FxCop. Spustí úlohu MSBuild po sestavení, která vyvolá **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Jak tedy spustím analyzátory .NET?

Chcete-li spustit analyzátory .NET, nejprve [je povolte ze sady .NET SDK nebo je nainstalujte jako balíček NuGet](install-net-analyzers.md). Pak Sestavte projekt nebo řešení ze sady Visual Studio nebo pomocí nástroje MSBuild. Upozornění a chyby, které generují analyzátory Roslyn, se zobrazí v okně **Seznam chyb** nebo v příkazovém okně.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Zobrazí se upozornění CA0507 i po instalaci balíčku NuGet pro analyzátory .NET

Pokud jste nainstalovali analyzátory .NET, ale nadále získáte upozornění CA0507 " **" spuštění analýzy kódu ", je vystaralá od analyzátorů FxCop, které běží během sestavení"**, možná budete muset nastavit vlastnost **RunCodeAnalysis** MSBuild v [souboru projektu](../ide/solutions-and-projects-in-visual-studio.md#project-file) na **hodnotu false**. V opačném případě se starší verze analýzy spustí po každém sestavení.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Která pravidla se přepravují na analyzátory .NET?

Informace o tom, která pravidla analýzy starší verze byly předaná do analyzátorů .NET, najdete v tématu [stav portu pravidla FxCop](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Upozornění analýzy kódu jsou považována za chyby.

Pokud váš projekt používá možnost sestavení k ponechání upozornění jako chyb, může se zobrazit upozornění analyzátoru jako chyby. Chcete-li zabránit tomu, aby upozornění analýzy kódu byla považována za chyby, postupujte podle pokynů v [části Nejčastější dotazy k analýze kódu](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrace na analyzátory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Nainstalovat analyzátory .NET](install-net-analyzers.md)
