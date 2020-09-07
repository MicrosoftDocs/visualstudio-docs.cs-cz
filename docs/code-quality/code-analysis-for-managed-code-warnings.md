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
ms.openlocfilehash: 8238de0760f300b6fa418a5e3eb47eac3db77272
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509013"
---
# <a name="net-code-analysis-rules"></a>Pravidla analýzy kódu .NET
Nástroj Analýza spravovaného kódu poskytuje upozornění indikující porušení pravidel ve spravovaných knihovnách kódu. Upozornění se uspořádají do oblastí pravidla, jako je návrh, lokalizace, výkon a zabezpečení. Každé upozornění znamená porušení pravidla analýzy spravovaného kódu. Tato část poskytuje podrobné diskuze a příklady pro každé upozornění analýzy spravovaného kódu.

 V následující tabulce je uveden typ informací, které jsou k dispozici pro každé upozornění.

|Položka|Popis|
|----------|-----------------|
|Typ|Název TypeName pro pravidlo|
|CheckId|Jedinečný identifikátor pravidla CheckId a kategorie se používají pro potlačení varování ve zdrojovém zobrazení.|
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
