---
title: Sady pravidel nástroje FxCop Analyzer
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1567dd088ecc060f031e59827ff33024e9e955
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185949"
---
# <a name="rule-sets-for-analyzer-packages"></a>Sady pravidel pro balíčky analyzátoru

Předdefinované sady pravidel jsou součástí některých balíčků analyzátorů NuGet. Například sady pravidel, které jsou součástí balíčku NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (počínaje verzí 2.6.2), povolují nebo zakazují pravidla na základě jejich kategorie, jako je například zabezpečení, pojmenování nebo výkon. Použití sad pravidel usnadňuje rychlé zobrazení pouze těch porušení pravidel, která se vztahují k určité kategorii pravidla.

Sada pravidel je seskupení pravidel analýzy kódu, která identifikují cílené problémy a konkrétní podmínky. Sady pravidel umožňují povolit nebo zakázat pravidla a nastavit závažnost pro porušení jednotlivých pravidel. Balíček NuGet pro FxCop Analyzer obsahuje předdefinované sady pravidel pro následující kategorie pravidel:

- návrh
- dokumentace
- udržovatelnosti
- pojmenování
- výkon
- spolehlivost
- zabezpečení
- využití

Pokud migrujete ze starší analýzy "FxCop" na analýzu kódu na základě .NET Compiler Platform, tyto sady pravidel vám umožní pokračovat v používání podobných konfigurací pravidel pro [ty, které jste použili dříve](rule-set-reference.md).

## <a name="use-analyzer-package-rule-sets"></a>Použít sady pravidel balíčku analyzátoru

Po [instalaci balíčku NuGet Analyzer](install-roslyn-analyzers.md)vyhledejte v adresáři *RuleSets* sadu předdefinovaných pravidel. Pokud jste například odkazovali `Microsoft.CodeAnalysis.FxCopAnalyzers` na balíček analyzátoru, můžete najít jeho adresář *RuleSets* ve *verzi% USERPROFILE%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\< \rulesets\>* . Odtud zkopírujte jeden nebo více RuleSets a vložte je do adresáře, který obsahuje projekt aplikace Visual Studio, nebo přímo do **Průzkumník řešení**.

Můžete také [přizpůsobit předdefinované pravidlo](how-to-create-a-custom-rule-set.md) , které je nastaveno na vaše preference. Můžete například změnit závažnost jednoho nebo více pravidel tak, aby se v **Seznam chyb**zobrazovaly chyby nebo upozornění.

## <a name="set-the-active-rule-set"></a>Nastavit aktivní sadu pravidel

Proces nastavení aktivní sady pravidel se trochu liší v závislosti na tom, zda máte projekt .NET Core/. NET Standard nebo projekt .NET Framework.

### <a name="net-core"></a>.NET Core

Chcete-li nastavit pravidlo jako aktivní sadu pravidel pro analýzu v projektech .NET Core nebo .NET Standard, přidejte do souboru projektu ručně vlastnost **CodeAnalysisRuleSet** . Například následující sady `HelloWorld.ruleset` fragmentů kódu jako aktivní sada pravidel.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Chcete-li nastavit pravidlo pro nastavení aktivní sady pravidel pro analýzu v .NET Framework projekty, klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte možnost **vlastnosti**. Na stránkách vlastností projektu vyberte kartu **Analýza kódu** . V části **Spustit tuto sadu pravidel**vyberte **Procházet**a pak vyberte požadovanou sadu pravidel, kterou jste zkopírovali do adresáře projektu. Pro tato pravidla, která jsou povolená ve vybrané sadě pravidel, se teď zobrazují jenom porušení pravidel.

## <a name="available-rule-sets"></a>Dostupné sady pravidel

Předdefinované sady pravidel analyzátoru zahrnují tři RuleSets, které mají vliv na všechna pravidla v&mdash;balíčku, a to tak, že jsou všechny, které je zakazují, a jeden, který respektuje výchozí závažnost jednotlivých pravidel a nastavení povolení:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault. RuleSet

Kromě toho existují dvě sady pravidel pro každou kategorii pravidel v balíčku, jako je například výkon nebo zabezpečení. Jedna sada pravidel povoluje všechna pravidla pro kategorii a jedna sada pravidel respektuje výchozí závažnost a nastavení povolení pro každé pravidlo v kategorii.

Balíček [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer obsahuje sady pravidel pro následující kategorie:

- návrh
- dokumentace
- udržovatelnosti
- pojmenování
- výkon
- spolehlivost
- zabezpečení
- využití

## <a name="see-also"></a>Viz také:

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Nainstalovat analyzátory](install-roslyn-analyzers.md)
- [Konfigurovat analyzátory](use-roslyn-analyzers.md)
- [Použití sad pravidel k seskupení pravidel analýzy kódu](using-rule-sets-to-group-code-analysis-rules.md)
