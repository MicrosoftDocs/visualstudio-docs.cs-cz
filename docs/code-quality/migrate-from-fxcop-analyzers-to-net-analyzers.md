---
title: Migrace z analyzátorů FxCop do analyzátorů .NET
ms.custom: SEO-VS-2020
description: Naučte se migrovat z analyzátorů FxCop do analyzátorů .NET.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112229"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrace z analyzátorů FxCop do analyzátorů .NET

Analyzátory zdroje podle .NET Compiler Platform ("Roslyn") nahrazují [starší verzi analýzy](code-analysis-for-managed-code-overview.md) spravovaného kódu. Mnoho pravidel analýzy starší verze (FxCop) již bylo přepsáno jako analyzátory zdrojů.

Před vydáním sady Visual Studio 2019 16,8 a .NET 5,0 byly tyto analyzátory dodávány jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Počínaje sadou Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Balíček NuGet bude brzy zastaralý.

## <a name="migration-steps"></a>Kroky migrace

Použijte následující postup, chcete-li migrovat projekt nebo řešení z nástroje `Microsoft.CodeAnalysis.FxCopAnalyzers` do analyzátorů .NET:

1. Odinstalovat `Microsoft.CodeAnalysis.FxCopAnalyzers` balíček NuGet

2. [Povolit nebo nainstalovat analyzátory .NET](install-net-analyzers.md)

3. Povolit další pravidla: `Microsoft.CodeAnalysis.NetAnalyzers` je mnohem více konzervativní v porovnání s `Microsoft.CodeAnalysis.FxCopAnalyzers` . Na rozdíl od balíčku FxCopAnalyzers má pouze několik pravidel správnosti, která jsou [ve výchozím nastavení povolena jako upozornění sestavení](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Můžete [Povolit další pravidla](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) přizpůsobením vlastnosti MSBuild [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) . Například nastavením vlastnosti `AllEnabledByDefault` povolíte ve výchozím nastavení všechna příslušná pravidla certifikační autority jako upozornění na sestavení.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Viz také

- [Analýza zdrojového kódu oproti starší analýze](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrace ze starší verze z analýzy do analyzátorů .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Povolit nebo nainstalovat analyzátory .NET](install-net-analyzers.md)
- [Nejčastější dotazy týkající se analyzátorů .NET](net-analyzers-faq.md)
- [Konfigurovat analyzátory .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
