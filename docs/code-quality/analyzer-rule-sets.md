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
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974697"
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

Po [instalaci balíčku NuGet Analyzer](install-roslyn-analyzers.md)vyhledejte v adresáři *RuleSets* sadu předdefinovaných pravidel. Pokud jste například odkazovali na balíček nástroje `Microsoft.CodeAnalysis.FxCopAnalyzers` Analyzer, můžete najít jeho adresář *RuleSets* na adrese *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*. Odtud zkopírujte jeden nebo více RuleSets a vložte je do adresáře, který obsahuje projekt aplikace Visual Studio, nebo přímo do **Průzkumník řešení**.

Můžete také [přizpůsobit předdefinované pravidlo](how-to-create-a-custom-rule-set.md) , které je nastaveno na vaše preference. Můžete například změnit závažnost jednoho nebo více pravidel tak, aby se v **Seznam chyb**zobrazovaly chyby nebo upozornění.

## <a name="set-the-active-rule-set"></a>Nastavit aktivní sadu pravidel

Proces nastavení aktivní sady pravidel se trochu liší v závislosti na tom, zda máte projekt .NET Core/. NET Standard nebo projekt .NET Framework.

### <a name="net-core"></a>.NET Core

Chcete-li nastavit pravidlo jako aktivní sadu pravidel pro analýzu v projektech .NET Core nebo .NET Standard, přidejte do souboru projektu ručně vlastnost **CodeAnalysisRuleSet** . Například následující sady fragmentů kódu `HelloWorld.ruleset` jako aktivní sada pravidel.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Chcete-li nastavit pravidlo pro nastavení aktivní sady pravidel pro analýzu v .NET Framework projekty:

- V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.

- Na stránkách vlastností projektu vyberte kartu **Analýza kódu** .

::: moniker range="vs-2017"

- V části **Spustit tuto sadu pravidel**vyberte **Procházet**a pak vyberte požadovanou sadu pravidel, kterou jste zkopírovali do adresáře projektu.

::: moniker-end

::: moniker range=">=vs-2019"

- V části **aktivní pravidla**vyberte **Procházet**a pak vyberte požadovanou sadu pravidel, kterou jste zkopírovali do adresáře projektu.

::: moniker-end

   Pro tato pravidla, která jsou povolená ve vybrané sadě pravidel, se teď zobrazují jenom porušení pravidel.

## <a name="available-rule-sets"></a>Dostupné sady pravidel

Předdefinované sady pravidel analyzátoru zahrnují tři RuleSets, které mají vliv na všechna pravidla v balíčku @ no__t-0one, který jim umožňuje vše, jeden, který je zakazuje, a druhý, který respektuje výchozí závažnost jednotlivých pravidel a nastavení povolení:

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
