---
title: Migrace ze starší verze Analysis (FxCop) do zdrojové analýzy (FxCop analyzátory)
description: Naučte se, jak poprvé analyzovat kód nebo jak migrovat z binární analýzy (FxCop) na nový způsob analýzy spravovaného kódu pomocí analýzy zdrojů (FxCop Analyzer).
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
manager: jillfra
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937579"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrace ze starší verze Analysis (FxCop) do zdrojové analýzy (FxCop analyzátory)

Analyzátory zdroje podle .NET Compiler Platform ("Roslyn") nahrazují [starší verzi analýzy](../code-quality/code-analysis-for-managed-code-overview.md) spravovaného kódu. Pro novější šablony projektů, jako jsou například .NET Core a .NET Standard projekty, není dostupná starší analýza.

Mnoho pravidel pro starší verzi Analysis (FxCop) již bylo přepsáno pro analyzátory FxCop, což je sada analyzátorů kódu Roslyn. [Analyzátory FxCop nainstalujete jako balíček NuGet](install-fxcop-analyzers.md#nuget-package) , na který se odkazuje v projektu nebo řešení. Analyzátory FxCop spouštějí analýzu založenou na zdrojovém kódu během provádění kompilátoru. Výsledky analyzátoru jsou hlášeny spolu s výsledky kompilátoru.

Další informace o rozdílech mezi staršími verzemi analýzy a analýzou zdroje najdete v následujících tématech:

- [Analýza zdrojového kódu oproti starší analýze](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [Nejčastější dotazy týkající se analyzátorů FxCop](../code-quality/fxcop-analyzers-faq.md)

Pokud chcete migrovat na zdrojovou analýzu, [nainstalujte analyzátory FxCop](../code-quality/install-fxcop-analyzers.md). Podobně jako porušení pravidel pro analýzu starších verzí se v okně Seznam chyb v aplikaci Visual Studio zobrazí porušení analýzy zdrojového kódu. Kromě toho se porušení analýzy zdrojového kódu zobrazí také v editoru kódu jako *vlnovky* pod problematickým kódem. Barva vlnovky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#rule-severity) pravidla. Pokud chcete zobrazit stav pravidel, která se přepravují na nové analyzátory FxCop, přečtěte si téma [ported a untransported Rules](../code-quality/fxcop-rule-port-status.md).

Další informace o tom, jak nakonfigurovat analyzátory FxCop:

- Pokud chcete nakonfigurovat analyzátory FxCop, přečtěte si téma [Konfigurace analyzátorů FxCop](../code-quality/configure-fxcop-analyzers.md).

- Informace o konfiguraci analyzátorů pomocí předdefinovaných pravidel s EditorConfig nebo souborem sady pravidel najdete v tématu [Povolení kategorie pravidel](../code-quality/analyzer-rule-sets.md).