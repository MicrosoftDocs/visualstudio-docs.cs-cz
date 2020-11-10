---
title: Množiny pravidel analýzy kódu
ms.date: 04/02/2018
description: Přečtěte si o předdefinovaných a přizpůsobených sadách pravidel v sadě Visual Studio Code Analysis. Přečtěte si, jak zadat sady pravidel v souborech a jak konfigurovat sady pravidel v projektech.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d17e8321aa6567a6ae0936291a73d5cb854b5c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436885"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Použití sad pravidel k seskupení pravidel analýzy kódu

Při konfiguraci analýzy kódu v sadě Visual Studio můžete vybrat ze seznamu předdefinovaných *sad pravidel*. Sada pravidel je seskupení pravidel analýzy kódu, která identifikují cílené problémy a specifické podmínky pro daný projekt. Můžete například použít sadu pravidel, která je navržena pro prohledávání kódu pro veřejně dostupná rozhraní API. Můžete také použít sadu pravidel, která zahrnuje všechna dostupná pravidla.

Můžete přizpůsobit sadu pravidel přidáním nebo odstraněním pravidel nebo změnou závažnosti pravidla tak, aby se zobrazila jako upozornění nebo chyby v **Seznam chyb**. Sada vlastních pravidel může splnit potřebu konkrétního vývojového prostředí. Při přizpůsobení sady pravidel poskytuje editor sady pravidel nástroje pro vyhledávání a filtrování, které vám pomůžou postupovat.

Sady pravidel jsou k dispozici pro [analýzu spravovaného kódu](/dotnet/fundamentals/code-analysis/code-quality-rule-options), [starší verzi analýzy spravovaného kódu](how-to-configure-code-analysis-for-a-managed-code-project.md)a [analýzu kódu v jazyce C++](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Formát sady pravidel

Sada pravidel je určena ve formátu XML v souboru *. ruleset* . Pravidla, která se skládají z ID a *Akce* , jsou seskupena podle ID analyzátoru a oboru názvů v souboru.

Obsah souboru *. ruleset* vypadá podobně jako tento kód XML:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Je snazší [Upravit sadu pravidel](../code-quality/working-in-the-code-analysis-rule-set-editor.md) v **editoru grafických sad pravidel** než ručně.

## <a name="specify-a-rule-set-for-a-project"></a>Zadat sadu pravidel pro projekt

Sada pravidel pro projekt je určena vlastností **CodeAnalysisRuleSet** v souboru projektu sady Visual Studio. Příklad:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)