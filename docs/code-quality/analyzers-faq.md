---
title: EditorConfig versus analyzátory
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae41d9ac30567a32780af422c3af1e2b0d6a63ae
ms.sourcegitcommit: b761a4a457646d04adfda510c8837734ee4d8f17
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929762"
---
# <a name="code-analysis-faq"></a>Nejčastější dotazy k analýze kódu

Tato stránka obsahuje odpovědi na některé nejčastější dotazy týkající se analýzy kódu založené na .NET Compiler Platform v aplikaci Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analýza kódu oproti EditorConfig

**OTÁZKA**: Mám použít analýzu kódu nebo EditorConfig pro kontrolu stylu kódu?

**A**: Analýza kódu a soubory. editorconfig fungují ručně. Pokud definujete styly kódu [v souboru. editorconfig](../ide/editorconfig-code-style-settings-reference.md) nebo na stránce [Možnosti textového editoru](../ide/code-styles-and-code-cleanup.md) , budete ve skutečnosti konfigurovat analyzátory kódu, které jsou součástí sady Visual Studio. Soubory EditorConfig lze také použít ke konfiguraci některých balíčků analyzátoru NuGet, jako jsou například [analyzátory FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig oproti sadám pravidel

**OTÁZKA**: Mám analyzátory nakonfigurovat pomocí sady pravidel nebo souboru. editorconfig?

**A**: Sady pravidel a soubory. editorconfig se vzájemně vylučují, jak je nakonfigurovat analyzátory. Můžou existovat společně. [Sady pravidel](analyzer-rule-sets.md) umožňují povolit a zakázat pravidla a nastavit jejich závažnost. Soubory EditorConfig nabízejí další způsoby konfigurace pravidel. Pro analyzátory FxCop vám soubory. editorconfig umožňují [definovat, které typy kódu se mají analyzovat](fxcop-analyzer-options.md). Pro analyzátory, které jsou součástí sady Visual Studio, umožňují soubory. editorconfig [definovat preferované styly kódu](../ide/editorconfig-code-style-settings-reference.md) pro základ kódu.

Kromě sad pravidel a souborů. editorconfig jsou některé analyzátory nakonfigurovány pomocí textových souborů označených jako [Další soubory](../ide/build-actions.md#build-action-values) pro kompilátory C# a VB.

> [!NOTE]
> Soubory EditorConfig se nedají použít ke konfiguraci analýzy starší verze, zatímco sady pravidel můžou.

## <a name="code-analysis-in-ci-builds"></a>Analýza kódu v sestaveních CI

**OTÁZKA**: Funguje analýza kódu na základě .NET Compiler Platform v sestaveních průběžné integrace (CI)?

**A**: Ano. Pro analyzátory, které jsou nainstalovány z balíčku NuGet, jsou tato pravidla [vynutila v době sestavování](roslyn-analyzers-overview.md#build-errors), včetně během sestavení CI. Analyzátory používané v sestaveních CI mají na zřeteli konfiguraci pravidel ze [sad pravidel](analyzer-rule-sets.md) i [souborů. editorconfig](configure-fxcop-analyzers.md). Analyzátory kódu, které jsou součástí sady Visual Studio, nejsou aktuálně k dispozici jako balíček NuGet, takže tato pravidla se v sestavení CI nedají vymáhat.

## <a name="ide-analyzers-versus-stylecop"></a>Analyzátory IDE versus StyleCop

**OTÁZKA**: Jaký je rozdíl mezi analyzátory kódu integrovaného vývojového prostředí (IDE) sady Visual Studio a analyzátory StyleCop?

**A**: Integrované vývojové prostředí (IDE) sady Visual Studio obsahuje integrované analyzátory, které hledají jak styl kódu, tak i problémy s kvalitou. Tato pravidla vám pomůžou používat nové jazykové funkce při jejich zavedení a zlepšení udržovatelnosti kódu. Analyzátory IDE se průběžně aktualizují s každou verzí sady Visual Studio.

[Analyzátory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) jsou nainstalované analyzátory třetích stran jako balíček NuGet, který kontroluje konzistenci stylů ve vašem kódu. Obecně platí, že pravidla StyleCop umožňují nastavit osobní předvolby pro základ kódu bez doporučení jednoho stylu nad jiným.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyzátory kódu oproti starší analýze

**OTÁZKA**: Jaký je rozdíl mezi staršími verzemi analýzy a analýz kódu založenými na .NET Compiler Platform?

Odpověď **: Analýza kódu na základě**.NET Compiler Platform analyzuje zdrojový kód v reálném čase a během kompilace, zatímco starší verze analýzy analyzuje binární soubory po dokončení sestavení. Další informace najdete v [nejčastějších dotazech](fxcop-analyzers-faq.md)k [analýze na základě .NET Compiler Platform](roslyn-analyzers-overview.md#net-compiler-platform-based-analysis-versus-legacy-analysis) a analyzátoru FxCop.

## <a name="see-also"></a>Viz také:

- [Přehled analyzátorů](roslyn-analyzers-overview.md)
- [EditorConfig nastavení konvence psaní kódu .NET](../ide/editorconfig-code-style-settings-reference.md)