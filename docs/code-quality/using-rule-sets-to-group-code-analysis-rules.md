---
title: Množiny pravidel analýzy kódu
ms.date: 04/02/2018
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
ms.openlocfilehash: ca48d0cad8ad6e22aa2264390d230590438e8579
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506463"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Použití sad pravidel k seskupení pravidel analýzy kódu

Při konfiguraci analýzy kódu v sadě Visual Studio můžete vybrat ze seznamu předdefinovaných *sad pravidel*. Sada pravidel je seskupení pravidel analýzy kódu, která identifikují cílené problémy a specifické podmínky pro daný projekt. Můžete například použít sadu pravidel, která je navržena pro prohledávání kódu pro veřejně dostupná rozhraní API. Můžete také použít sadu pravidel, která zahrnuje všechna dostupná pravidla.

Můžete přizpůsobit sadu pravidel přidáním nebo odstraněním pravidel nebo změnou závažnosti pravidla tak, aby se zobrazila jako upozornění nebo chyby v **Seznam chyb**. Sada vlastních pravidel může splnit potřebu konkrétního vývojového prostředí. Při přizpůsobení sady pravidel poskytuje editor sady pravidel nástroje pro vyhledávání a filtrování, které vám pomůžou postupovat.

Sady pravidel jsou k dispozici pro [analýzu spravovaného kódu](analyzer-rule-sets.md), [starší verzi analýzy spravovaného kódu](how-to-configure-code-analysis-for-a-managed-code-project.md)a [ C++ analýzu kódu](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run).

## <a name="rule-set-format"></a>Formát sady pravidel

Sada pravidel je určena ve formátu XML v souboru *. ruleset* . Pravidla, která se skládají z ID a *Akce*, jsou seskupena podle ID analyzátoru a oboru názvů v souboru.

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

Sada pravidel pro projekt je určena vlastností **CodeAnalysisRuleSet** v souboru projektu sady Visual Studio. Například:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/rule-set-reference.md)
