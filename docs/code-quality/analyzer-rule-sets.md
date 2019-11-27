---
title: Sady pravidel a soubory editorconfig pro FxCop Analyzer
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2cf385aaf24db2172a61ddbe7ecf77dcbe40f3c
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74537774"
---
# <a name="enable-a-category-of-rules"></a>Povolení kategorie pravidel

Balíčky analyzátoru můžou zahrnovat předdefinované soubory [EditorConfig](use-roslyn-analyzers.md#rule-severity) a [sady pravidel](using-rule-sets-to-group-code-analysis-rules.md) , které usnadňují a usnadňují povolování kategorií pravidel, jako jsou pravidla zabezpečení nebo návrhu. Balíček [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet Analyzer zahrnuje obě sady pravidel (počínaje verzí 2.6.2) a soubory EditorConfig (počínaje verzí 2.9.5). Povolením konkrétní kategorie pravidel můžete identifikovat cílené problémy a konkrétní podmínky.

> [!NOTE]
> Povolení pravidel analyzátoru a nastavení jejich závažnosti pomocí souboru EditorConfig se podporuje počínaje verzí Visual Studio 2019 verze 16,3.

Balíček NuGet pro FxCop Analyzer obsahuje předdefinované sady pravidel a soubory EditorConfig pro následující kategorie pravidel:

- Všechna pravidla
- Tok dat
- Návrh
- Dokumentace
- Globalizace
- Interoperabilita
- Udržovatelnost
- Ming
- Výkon
- Portovaná z FxCop
- Spolehlivost
- Zabezpečení –
- Použití

Každá z těchto kategorií pravidel má EditorConfig nebo soubor sady pravidel:

- Povolit všechna pravidla v kategorii (a zakázat všechna ostatní pravidla)
- použít výchozí závažnost a nastavení povolení pro každé pravidlo (a zakázat všechna ostatní pravidla)

> [!TIP]
> Kategorie všechna pravidla obsahuje další EditorConfig nebo soubor sady pravidel pro zákaz všech pravidel. Tento soubor použijte k rychlému odstranění všech upozornění analyzátoru nebo chyb v projektu.

> [!TIP]
> Pokud migrujete ze starší analýzy "FxCop" na analýzu kódu na základě .NET Compiler Platform, soubory EditorConfig a sady pravidel vám umožní pokračovat v používání podobných konfigurací pravidel pro ty, [které jste použili dříve](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Předdefinované soubory EditorConfig

Předdefinované soubory EditorConfig pro balíček Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer jsou umístěné v adresáři *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<verze\>\editorconfig* . Například soubor EditorConfig, který povolí všechna pravidla zabezpečení, se nachází v *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<verze\>\editorconfig\SecurityRulesEnabled\\. EditorConfig*.

Zkopírujte zvolený soubor. editorconfig do kořenového adresáře vašeho projektu.

## <a name="predefined-rule-sets"></a>Předdefinované sady pravidel

Předdefinované soubory sady pravidel pro balíček Microsoft. CodeAnalysis. FxCopAnalyzers Analyzer jsou umístěné v adresáři *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<verze\>\rulesets* . Například soubor sady pravidel, který povolí všechna pravidla zabezpečení, se nachází v *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<verze\>\rulesets\SecurityRulesEnabled.ruleset*.

Zkopírujte jednu nebo více sad pravidel a vložte je do adresáře, který obsahuje projekt aplikace Visual Studio, nebo přímo do **Průzkumník řešení**.

Můžete také [přizpůsobit předdefinované pravidlo](how-to-create-a-custom-rule-set.md) , které je nastaveno na vaše preference. Můžete například změnit závažnost jednoho nebo více pravidel tak, aby se v **Seznam chyb**zobrazovaly chyby nebo upozornění.

### <a name="set-the-active-rule-set"></a>Nastavit aktivní sadu pravidel

Proces nastavení aktivní sady pravidel se trochu liší v závislosti na tom, zda máte projekt .NET Core/. NET Standard nebo projekt .NET Framework.

#### <a name="net-core"></a>.NET Core

Chcete-li nastavit pravidlo jako aktivní sadu pravidel pro analýzu v projektech .NET Core nebo .NET Standard, přidejte do souboru projektu ručně vlastnost **CodeAnalysisRuleSet** . Například následující sady fragmentů kódu `HelloWorld.ruleset` jako aktivní sada pravidel.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>Viz také:

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Přehled analyzátorů .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Nainstalovat analyzátory](install-roslyn-analyzers.md)
- [Konfigurovat analyzátory](use-roslyn-analyzers.md)
- [Použití sad pravidel k seskupení pravidel analýzy kódu](using-rule-sets-to-group-code-analysis-rules.md)
