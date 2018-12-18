---
title: Upozornění Analýzy kódu pro spravovaný kód
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 600b5c7822232581cd01bd9bbf7616f4d1e9bb7c
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859065"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Upozornění Analýzy kódu pro spravovaný kód
Nástroj pro analýzu spravovaného kódu poskytuje upozornění, které označují porušení pravidel v knihovnách spravovaného kódu. Upozornění jsou uspořádány do pravidla oblasti, jako jsou návrh, lokalizaci, výkonu a zabezpečení. Každému varování oznamuje porušení pravidla analýzy spravovaného kódu. Tato část poskytuje podrobné diskuze a příklady pro každé upozornění analýzy spravovaného kódu.

 V následující tabulce jsou uvedeny typ informací, která je k dispozici pro každé upozornění.

|Položka|Popis|
|----------|-----------------|
|Typ|Název typu pravidla.|
|CheckId|Jedinečný identifikátor pro pravidlo. ID kontroly a kategorie se používají pro-source potlačení upozornění.|
|Kategorie|Kategorie upozornění.|
|Narušující změna|Určuje, zda oprava porušení tohoto pravidla je zásadní změnu. Zásadní změna znamená, že sestavení, které obsahuje závislost na cíl, který způsobil porušení nebude znovu zkompilovat pomocí nové verze nelze upravovat nebo může v době běhu selhat z důvodu této změny. Při více opravy jsou k dispozici a alespoň jednu opravu je zásadní změnu a jednu opravu není, jsou určeny "Přerušení" i "Bez přerušení".|
|příčina|Konkrétní spravovaný kód, který způsobí, že pravidlo generování upozornění.|
|Popis|Tento článek popisuje problémy, které jsou za upozornění.|
|Jak vyřešit porušení|Vysvětluje, jak změnit zdrojový kód a splňovat pravidla zabránit generování upozornění.|
|Kdy potlačit upozornění|Popisuje, když je bezpečný pro potlačení upozornění z pravidla.|
|Příklad kódu|Příklady, které porušují pravidlo a opravit příklady, které splňují pravidla.|
|Související upozornění|Související upozornění.|

## <a name="in-this-section"></a>V tomto oddílu

|||
|-|-|
|[Upozornění podle CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Obsahuje seznam všech upozornění podle CheckId|
|[Upozornění kryptografie](../code-quality/cryptography-warnings.md)|Upozornění, které podporují bezpečnější knihovny a aplikace prostřednictvím správné použití šifrování.|
|[Upozornění ohledně návrhu](../code-quality/design-warnings.md)|Upozornění, které podporují správná knihovna návrhu uvedené pokyny k návrhu architektury .NET.|
|[Upozornění globalizace](../code-quality/globalization-warnings.md)|Upozornění, které podporují aplikací a knihoven nasadit kdekoli na světě.|
|[Upozornění interoperability](../code-quality/interoperability-warnings.md)|Upozornění, které podporují u klientů modelu COM interakci.|
|[Upozornění udržovatelnosti](../code-quality/maintainability-warnings.md)|Upozornění, které podporují údržby knihovny a aplikace.|
|[Upozornění mobility](../code-quality/mobility-warnings.md)|Upozornění, které podporují power účinného využití.|
|[Upozornění na pojmenování](../code-quality/naming-warnings.md)|Upozornění, které podporují dodržování konvencí pokyny k návrhu architektury .NET.|
|[Upozornění výkonu](../code-quality/performance-warnings.md)|Upozornění, které podporují výkonné knihovny a aplikace.|
|[Upozornění přenositelnosti](../code-quality/portability-warnings.md)|Upozornění, které podporují přenositelnost napříč různými platformami.|
|[Upozornění spolehlivosti](../code-quality/reliability-warnings.md)|Upozornění, které podporují spolehlivost knihovny a aplikace, jako třeba správné využití paměti a podproces.|
|[Upozornění zabezpečení](../code-quality/security-warnings.md)|Upozornění, které podporují bezpečnější knihovny a aplikace.|
|[Upozornění využití](../code-quality/usage-warnings.md)|Upozornění, které podporují správné použití rozhraní .NET Framework.|
|[Chyby zásad Analýzy kódu](../code-quality/code-analysis-policy-errors.md)|Chyby, ke kterým dochází při splnění zásad analýzy kódu nejsou při vrácení se změnami.|