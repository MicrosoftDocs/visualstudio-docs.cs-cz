---
title: Sady pravidel v analyzátoru
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7df084a81de2afc522fc3b82141cf8c5c59205ca
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204542"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Sady pravidel pro analyzátory Roslyn

Sady předdefinovaných pravidel jsou zahrnuty některé balíčky NuGet analyzátor. Například sady pravidel, které jsou součástí [balíček Microsoft.CodeAnalysis.FxCopAnalyzers NuGet analyzátor](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) (počínaje verzí 2.6.2) povolení nebo zakázání pravidla na základě jejich kategorie, jako je zabezpečení, názvy, nebo výkon. Použití sad pravidel usnadňuje se krátce zobrazit pouze těchto porušení pravidel, které se vztahují k určité kategorie pravidla.

Pokud migrujete ze starší verze "FxCop" statické analýzy kódu pro analyzátory Roslyn, povolte tyto sady pravidel můžete nadále používat stejnou konfiguraci pravidlo, které jste použili dříve.

## <a name="use-analyzer-rule-sets"></a>Použití sad pravidel v analyzátoru

Poté co [instalaci balíčku NuGet analyzátor](install-roslyn-analyzers.md), vyhledejte předem definované pravidlo, nastavte jeho *sady pravidel* adresáři, například *% USERPROFILE %\\.nuget\packages\ Microsoft.codequality.analyzers\<verze > \rulesets*. Odtud lze přetáhnout a vyřadit, nebo zkopírujte a vložte jednu nebo více pravidel do projektu sady Visual Studio v **Průzkumníka řešení**.

Chcete-li aktivní sadu pravidel pro analýzu sadu pravidel, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a zvolte **vlastnosti**. Na stránkách vlastností projektu, vyberte **analýzy kódu** kartu. V části **spustit tuto sadu pravidel**vyberte **Procházet**a potom vyberte požadované pravidlo sadu, kterou jste zkopírovali do adresáře projektu. Teď vidíte pouze porušení pravidel pro tato pravidla, které jsou povolené v vybranou sadu pravidel.

Můžete také [přizpůsobení sady předdefinovaných pravidel](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) dle požadavků. Například můžete změnit závažnost jedno nebo více pravidel tak, aby narušení se zobrazují jako chyby nebo varování v **seznam chyb**.

## <a name="available-rule-sets"></a>Sad pravidel k dispozici

Analyzátor předdefinované sady pravidel patří tři sady pravidel, které ovlivňují všechna pravidla v balíčku&mdash;ten, který umožňuje uspořádat, ten, který zakáže všechny a ten, který respektuje každé pravidlo výchozí závažnost a povolení nastavení:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Kromě toho existují dvě sady pravidel pro každou kategorii pravidla v balíčku, například výkon a zabezpečení. Jedna sada pravidel povolí všechna pravidla pro kategorii a jedna sada pravidel respektuje výchozí nastavení závažnosti a povolení pro každé pravidlo v dané kategorii.

 [Balíček Microsoft.CodeAnalysis.FxCopAnalyzers NuGet analyzátor](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) zahrnuje sady pravidel v těchto kategoriích, tak, aby odpovídaly sady pravidel, která je k dispozici pro starší verze "FxCop" statické analýzy kódu:

- návrh
- dokumentace
- udržovatelnosti
- pojmenování
- výkon
- spolehlivost
- zabezpečení
- využití

## <a name="see-also"></a>Viz také:

- [Přehled analyzátory pro .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Instalace analyzátorů .NET Compiler Platform](install-roslyn-analyzers.md)
- [Konfigurovat a používat pravidla analyzátoru Roslyn](use-roslyn-analyzers.md)
- [Použití sady pravidel k seskupování pravidel analýzy kódu](using-rule-sets-to-group-code-analysis-rules.md)