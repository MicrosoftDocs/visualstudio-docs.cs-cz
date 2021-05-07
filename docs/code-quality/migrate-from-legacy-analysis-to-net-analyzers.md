---
title: Migrace z FxCop na zdrojovou analýzu (analyzátory .NET)
ms.custom: SEO-VS-2020
description: Zjistěte, jak poprvé analyzovat kód nebo jak migrovat z binární analýzy (FxCop) na nový způsob analýzy spravovaného kódu pomocí analýzy zdroje (analyzátory .NET).
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
manager: jmartens
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798229"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrace ze starší verze analýzy (FxCop) na zdrojovou analýzu (analyzátory .NET)

Analýza zdroje podle analyzátorů .NET Compiler Platform (Roslyn) nahrazuje starší [analýzu](../code-quality/code-analysis-for-managed-code-overview.md) spravovaného kódu. Pro novější šablony projektů, jako jsou .NET Core a .NET Standard projekty, není starší verze analýzy dostupná.

Mnoho pravidel starší verze analýzy (FxCop) už bylo přepsána pro analyzátory .NET, sadu analyzátorů kódu Roslyn. Analyzátory Roslyn spouštěly analýzu založenou na zdrojovém kódu během provádění kompilátoru. Výsledky analyzátoru se hlásí spolu s výsledky kompilátoru.

Další informace o rozdílech mezi starší verzí analýzy a zdrojovou analýzou najdete v následujících zdroji:

- [Porovnání analýzy zdrojového kódu a starší verze analýzy](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [Nejčastější dotazy k analyzátorům .NET](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Migrace

Pokud chcete migrovat na [zdrojovou analýzu, povolte nebo nainstalujte analyzátory .NET.](install-net-analyzers.md) Stejně jako porušení pravidel starší verze analýzy se porušení analýzy zdrojového kódu Seznam chyb okně v Visual Studio. Kromě toho se porušení analýzy zdrojového kódu  zobrazují také v editoru kódu jako podtržení kódem, který ho uráží. Barva přemostěčky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Pokud chcete zobrazit stav pravidel portovaných do nových analyzátorů .NET, podívejte se na část Portovaná a [nepřiportovaná pravidla.](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> Před Visual Studio 2019 16.8 a .NET 5.0 se tyto analyzátory dodaly `Microsoft.CodeAnalysis.FxCopAnalyzers` [jako balíček NuGet.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) Počínaje Visual Studio 2019 16.8 a .NET 5.0 jsou tyto analyzátory součástí [sady .NET SDK.](/dotnet/fundamentals/code-analysis/overview) Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Další informace najdete v tématu [Migrace z analyzátorů FxCop na analyzátory .NET.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="configuration"></a>Konfigurace

Další informace o tom, jak nakonfigurovat analyzátory .NET:

- Pokud chcete nakonfigurovat analyzátory .NET, přečtěte si téma [Konfigurace analyzátorů .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Informace o konfiguraci analyzátorů pomocí předdefinovaných pravidel s EditorConfig nebo souborem sady pravidel najdete v tématu [Povolení kategorie pravidel](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Viz také

- [Migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
