---
title: Analýza kódu FxCop a analyzátory FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136382"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Nejčastější dotazy ohledně FxCop a FxCop analyzátory

Může být trochu matoucí znát rozdíly mezi starší verzi FxCop a FxCop analyzátory. Tento článek se zaměřuje na řešení některých dotazů, které můžete mít.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Jaký je rozdíl mezi starší verzi FxCop a FxCop analyzátory?

Starší verzi FxCop spustí po sestavení analýzy zkompilovaného sestavení. Spuštění jako samostatný spustitelný soubor volá **FxCopCmd.exe**. FxCopCmd.exe načte zkompilovaného sestavení, spuštění analýzy kódu a hlásí výsledky (nebo *diagnostiky*).

Analyzátory FxCop jsou založené na platformě .NET Compiler Platform ("Roslyn"). Můžete [instalace jako balíček NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) , na který odkazuje na projekt nebo řešení. Analýza analyzátory FxCop spuštění zdrojového kódu na základě při spuštění kompilátoru. Analyzátory FxCop jsou hostované buď v rámci procesu kompilátoru **csc.exe** nebo **vbc.exe**, a spuštění analýzy při sestavení projektu. Výsledky analýzy jsou hlášeny současně s výsledky kompilátoru.

> [!NOTE]
> Můžete také [nainstalovat analyzátory FxCop jako rozšíření sady Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). V takovém případě spustit analyzátory psaní v editoru kódu, ale nejsou spuštění v okamžiku sestavení. Pokud chcete spustit analyzátory FxCop jako součást kontinuální integrace (CI), je nainstalujte jako balíček NuGet místo.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Příkaz spustit analýzu kódu spustit analyzátory FxCop?

Ne. Když vyberete **analyzovat** > **spustit analýzu kódu** v sadě Visual Studio 2017, provádí statickou analýzu kódu nebo starší verzi FxCop. **Spustit analýzu kódu** nemá žádný vliv na roslynu analyzátory, včetně analyzátory FxCop založené na platformě Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Vlastnosti projektu nástroje msbuild RunCodeAnalysis spouští analyzátory?

Ne. **RunCodeAnalysis** vlastnost v souboru projektu (například *.csproj*) slouží pouze ke spuštění starší verzi FxCop. Spuštění úlohy nástroje msbuild po sestavení, která volá **FxCopCmd.exe**. Jedná se o ekvivalent pro výběr **analyzovat** > **spustit analýzu kódu** v sadě Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Jak můžu pak spustit analyzátory FxCop?

Nejprve spustit analyzátory FxCop [nainstalujte balíček NuGet](install-fxcop-analyzers.md) pro ně. Pak sestavení projektu nebo řešení v sadě Visual Studio nebo pomocí nástroje msbuild. Upozornění a chyby, které generují analyzátory FxCop se zobrazí v **seznam chyb** nebo příkazové okno.

## <a name="see-also"></a>Viz také:

- [Přehled analyzátory pro .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Začínáme s analyzátory](fxcop-analyzers.yml)
- [Nainstalujte analyzátory FxCop](install-fxcop-analyzers.md)
