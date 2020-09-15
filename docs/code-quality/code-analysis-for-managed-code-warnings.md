---
title: Upozornění Analýzy kódu pro spravovaný kód
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 566b9827f42f646cd9350cfc015a460485212a09
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094327"
---
# <a name="net-code-analysis-rules"></a>Pravidla analýzy kódu .NET
Analýza kódu .NET poskytuje pravidla, která indikují porušení kvality kódu nebo návrhy na zlepšení kvality kódu. Pravidla jsou uspořádaná do oblastí pravidel, jako je návrh, lokalizace, výkon a zabezpečení. Některá pravidla jsou specifická pro použití rozhraní .NET API, zatímco zbývající pravidla se týkají obecného kvality kódu. Tato část poskytuje podrobné diskuze a příklady pro každé pravidlo.

 V následující tabulce je uveden typ informací, které jsou k dispozici pro jednotlivé diagnostiky.

|Položka|Popis|
|----------|-----------------|
|Typ|Název TypeName pro pravidlo|
|RuleId|Jedinečný identifikátor pravidla RuleId a kategorie se používají pro potlačení varování ve zdrojovém zobrazení.|
|Kategorie|Kategorie upozornění|
|Zásadní změna|Zda je oprava pro porušení pravidla zásadní změnou. Zásadní změna znamená, že sestavení, které má závislost na cíli, který způsobil porušení, nebude znovu zkompilováno s novou opravenou verzí nebo může v době běhu selhat z důvodu změny. Je-li k dispozici více oprav a nejméně jedna oprava je zásadní změna a jedna oprava není, je určena možnost "průlom" i "nemožnost".|
|Příčina|Konkrétní spravovaný kód, který způsobí, že pravidlo vygeneruje upozornění.|
|Popis|Popisuje problémy, které jsou za upozorněním.|
|Jak vyřešit porušení|Vysvětluje, jak změnit zdrojový kód pro splnění pravidla a zabránit tomu, aby vygenerovalo upozornění.|
|Kdy potlačit upozornění|Popisuje, kdy je bezpečné potlačit upozornění od pravidla.|
|Příklad kódu|Příklady, které porušují pravidlo a opravené příklady, které splňují pravidlo.|
|Související upozornění|Související upozornění.|

## <a name="in-this-section"></a>V tomto oddílu

|Kategorie|Popis|
|-|-|
|[Pravidla podle ID](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Zobrazí všechna pravidla podle RuleID.|
|[Pravidla návrhu](../code-quality/design-warnings.md)|Pravidla, která podporují správný návrh knihovny podle pokynů pro návrh .NET.|
|[Pravidla dokumentace](../code-quality/documentation-warnings.md)|Pravidla, která podporují dobře dokumentovaný návrh knihovny, umožňují správné použití dokumentačních komentářů XML.|
|[Pravidla globalizace](../code-quality/globalization-warnings.md)|Pravidla, která podporují knihovny a aplikace připravené pro použití ve světě.|
|[Pravidla udržovatelnosti](../code-quality/maintainability-warnings.md)|Pravidla, která podporují údržbu knihovny a aplikace.|
|[Pravidla pojmenování](../code-quality/naming-warnings.md)|Pravidla, která podporují dodržování konvencí pojmenování v pokynech pro návrh .NET.|
|[Pravidla výkonu](../code-quality/performance-warnings.md)|Pravidla, která podporují knihovny a aplikace s vysokým výkonem.|
|[Pravidla přenositelnosti a interoperability](../code-quality/interoperability-warnings.md)|Pravidla, která podporují přenositelnost napříč různými platformami a interakce s klienty modelu COM.|
|[Publikovat pravidla](../code-quality/publish-warnings.md)|Pravidla, která podporují vhodné publikování aplikací .NET.|
|[Pravidla spolehlivosti](../code-quality/reliability-warnings.md)|Pravidla, která podporují spolehlivost knihovny a aplikace, jako je třeba správné využití paměti a vláken.|
|[Pravidla zabezpečení](../code-quality/security-warnings.md)|Pravidla, která podporují bezpečnější knihovny a aplikace.|
|[Pravidla použití](../code-quality/usage-warnings.md)|Pravidla, která podporují příslušné použití rozhraní .NET.|
