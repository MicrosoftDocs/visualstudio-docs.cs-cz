---
title: Migrace z FxCop do zdrojové analýzy (analyzátory .NET)
ms.custom: SEO-VS-2020
description: Naučte se, jak poprvé analyzovat kód nebo jak migrovat z binární analýzy (FxCop) na nový způsob analýzy spravovaného kódu pomocí analýzy zdrojů (analyzátory .NET).
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
ms.openlocfilehash: 96a0c0b7fa1f2c703cefde31070ed98c5edddcb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859759"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migrace ze starší verze Analysis (FxCop) do služby source Analysis (analyzátory .NET)

Analyzátory zdroje podle .NET Compiler Platform ("Roslyn") nahrazují [starší verzi analýzy](../code-quality/code-analysis-for-managed-code-overview.md) spravovaného kódu. Pro novější šablony projektů, jako jsou například .NET Core a .NET Standard projekty, není dostupná starší analýza.

Mnoho pravidel pro starší verzi Analysis (FxCop) již bylo přepsáno pro analyzátory .NET, což je sada Roslynch analyzátorů kódu. Analyzátory Roslyn spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

Další informace o rozdílech mezi staršími verzemi analýzy a analýzou zdroje najdete v následujících tématech:

- [Analýza zdrojového kódu oproti starší analýze](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

- [Nejčastější dotazy týkající se analyzátorů .NET](../code-quality/net-analyzers-faq.md)

## <a name="migration"></a>Migrace

Pokud chcete migrovat na zdrojovou analýzu, [povolte nebo nainstalujte analyzátory .NET](install-net-analyzers.md). Podobně jako porušení pravidel pro analýzu starších verzí se v okně Seznam chyb v aplikaci Visual Studio zobrazí porušení analýzy zdrojového kódu. Kromě toho se porušení analýzy zdrojového kódu zobrazí také v editoru kódu jako *vlnovky* pod problematickým kódem. Barva vlnovky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Pokud chcete zobrazit stav pravidel, která se přepravují na nové analyzátory .NET, přečtěte si téma [ported a untransported Rules](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> Před vydáním sady Visual Studio 2019 16,8 a .NET 5,0 byly tyto analyzátory dodávány jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Počínaje sadou Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Další informace najdete v tématu [migrace z analyzátorů FxCop do analyzátorů .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Konfigurace

Další informace o tom, jak nakonfigurovat analyzátory .NET:

- Pokud chcete nakonfigurovat analyzátory .NET, přečtěte si téma [Konfigurace analyzátorů .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Informace o konfiguraci analyzátorů pomocí předdefinovaných pravidel s EditorConfig nebo souborem sady pravidel najdete v tématu [Povolení kategorie pravidel](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Viz také

- [Migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
