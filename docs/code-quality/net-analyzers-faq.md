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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800481"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Nejčastější dotazy týkající se starších verzí FxCop a analyzátorů .NET

Může být trochu matoucí porozumět rozdílům mezi staršími FxCop (binární analýzou) a analyzátorem .NET (analýza zdroje). Tento článek se zaměřuje na některé otázky, které můžete mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Jaký je rozdíl mezi staršími verzemi FxCop a analyzátory .NET?

Starší verze FxCop spustí analýzu po sestavení u zkompilovaného sestavení. Spouští se jako samostatný spustitelný soubor s názvem **FxCopCmd.exe**. FxCopCmd.exe načte zkompilované sestavení, spustí analýzu kódu a pak nahlásí výsledky (nebo *diagnostiku*).

Analyzátory .NET jsou založené na .NET Compiler Platform ("Roslyn"). [Povolíte je ze sady .NET SDK nebo je nainstalujete jako balíček NuGet](install-net-analyzers.md) , na který odkazuje projekt nebo řešení. Analyzátory spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Analyzátory jsou hostovány v rámci procesu kompilátoru, buď **csc.exe** nebo **vbc.exe**, a při sestavení projektu spusťte analýzu. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Jaký je rozdíl mezi analyzátory FxCop a analyzátory .NET?

Analyzátory FxCop a analyzátory .NET .NET Compiler Platform odkazují na implementace analyzátoru pro FxCop pravidla certifikační autority ("Roslyn"). Před vydáním sady Visual Studio 2019 16,8 a .NET 5,0 byly tyto analyzátory dodávány jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Počínaje sadou Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Zvažte [migraci z analyzátorů FxCop na analyzátory .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Spustí příkaz Spustit Code Analysis analyzátory .NET?

Před Visual Studio verze 16.5 z roku 2019 se při výběru možnosti Analyzovat spuštění Code Analysis spustí starší  >  verze analýzy. Od Visual Studio 2019 16.5 spustí možnost **Code Analysis** nabídky analyzátory založené na Roslynu pro vybraný projekt nebo řešení. Pokud jste nainstalovali analyzátory .NET, spustí se také. Další informace najdete v tématu [Postupy: Ruční Code Analysis spravovaného kódu.](how-to-run-code-analysis-manually-for-managed-code.md)

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Spouštěly analyzátory vlastností projektu RunCodeAnalysis msbuild?

No. Vlastnost **RunCodeAnalysis** v souboru projektu (například *.csproj)* slouží pouze ke spuštění starší verze FxCop. Spustí úlohu msbuild po sestavení, která vyvolá **FxCopCmd.exe**.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Jak tedy můžu spustit analyzátory .NET?

Pokud chcete spustit analyzátory .NET, nejprve je povolte ze sady .NET SDK nebo je nainstalujte [jako balíček NuGet.](install-net-analyzers.md) Pak sestavte projekt nebo řešení z Visual Studio nebo pomocí nástroje msbuild. Upozornění a chyby vygenerované analyzátory Roslyn se zobrazí v okně **Seznam chyb** nebo v příkazovém okně.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>I po instalaci balíčku NuGet analyzátorů .NET se mi zobrazí upozornění CA0507

Pokud jste nainstalovali analyzátory .NET, ale přesto se zobrazí upozornění CA0507, že příkaz Spustit Code Analysis je zastaralý ve prospěch analyzátorů **FxCop,** které se spouštěly během sestavování, možná budete muset v souboru projektu nastavit vlastnost [](../ide/solutions-and-projects-in-visual-studio.md#project-file) **RunCodeAnalysis** msbuild na hodnotu **false.** Jinak se starší verze analýzy provede po každém sestavení.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Která pravidla byla portována do analyzátorů .NET?

Informace o tom, která starší pravidla analýzy byla portována do analyzátorů .NET, najdete v tématu [Stav portu pravidla Fxcop.](fxcop-rule-port-status.md)

## <a name="code-analysis-warnings-are-treated-as-errors"></a>S upozorněními analýzy kódu se zachází jako s chybami.

Pokud váš projekt používá možnost sestavení k zacházení s upozorněními jako s chybami, mohou se upozornění analyzátoru zobrazovat jako chyby. Chcete-li zabránit tomu, aby upozornění analýzy kódu byla považována za chyby, postupujte podle pokynů v [části Nejčastější dotazy k analýze kódu](../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Migrace na analyzátory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Instalace analyzátorů .NET](install-net-analyzers.md)
