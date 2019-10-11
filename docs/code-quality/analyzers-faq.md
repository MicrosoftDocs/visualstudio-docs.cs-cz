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
ms.openlocfilehash: 12e6681490c6c933369d3fef064ec88f240e3a99
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172763"
---
# <a name="code-analysis-faq"></a>Nejčastější dotazy k analýze kódu

Tato stránka obsahuje odpovědi na některé nejčastější dotazy týkající se analýzy kódu založené na .NET Compiler Platform v aplikaci Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analýza kódu oproti EditorConfig

**OTÁZKA**: Mám použít analýzu kódu nebo EditorConfig pro kontrolu stylu kódu?

**A**: Analýza kódu a soubory EditorConfig fungují ručně. Při definování stylů kódu [v souboru EditorConfig](../ide/editorconfig-code-style-settings-reference.md) nebo na stránce [Možnosti textového editoru](../ide/code-styles-and-code-cleanup.md) ve skutečnosti konfigurujete analyzátory kódu, které jsou součástí sady Visual Studio. Soubory EditorConfig lze použít k povolení nebo zakázání pravidel analyzátoru a také ke konfiguraci některých balíčků analyzátoru NuGet, jako jsou například [analyzátory FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig oproti sadám pravidel

**OTÁZKA**: Mám analyzátory nakonfigurovat pomocí sady pravidel nebo souboru EditorConfig?

**A**: Sady pravidel a soubory EditorConfig můžou existovat společně a dají se použít ke konfiguraci analyzátorů. Soubory EditorConfig a sady pravidel umožňují povolit a zakázat pravidla a nastavit jejich závažnost.

Soubory EditorConfig ale nabízejí další způsoby, jak pravidla konfigurovat:

- Pro analyzátory FxCop vám soubory EditorConfig umožňují [definovat, které typy kódu se mají analyzovat](fxcop-analyzer-options.md).
- Pro analyzátory ve stylu kódu, které jsou součástí sady Visual Studio, EditorConfig soubory umožňují [definovat preferované styly kódu](../ide/editorconfig-code-style-settings-reference.md) pro základ kódu.

Kromě sad pravidel a souborů EditorConfig jsou některé analyzátory nakonfigurovány pomocí textových souborů označených jako [Další soubory](../ide/build-actions.md#build-action-values) pro kompilátory C# a VB.

> [!NOTE]
> - Soubory EditorConfig se dají použít jenom k povolení pravidel a nastavení jejich závažnosti v sadě Visual Studio 2019 verze 16,3 a novější.
> - Soubory EditorConfig se nedají použít ke konfiguraci analýzy starší verze, zatímco sady pravidel můžou.

## <a name="code-analysis-in-ci-builds"></a>Analýza kódu v sestaveních CI

**OTÁZKA**: Funguje analýza kódu na základě .NET Compiler Platform v sestaveních průběžné integrace (CI)?

**A**: Ano. Pro analyzátory, které jsou nainstalovány z balíčku NuGet, jsou tato pravidla [vynutila v době sestavování](roslyn-analyzers-overview.md#build-errors), včetně během sestavení CI. Analyzátory používané v sestaveních CI mají na zřeteli konfiguraci pravidel ze sad pravidel i souborů EditorConfig. Analyzátory kódu, které jsou součástí sady Visual Studio, nejsou aktuálně k dispozici jako balíček NuGet, takže tato pravidla se v sestavení CI nedají vymáhat.

## <a name="ide-analyzers-versus-stylecop"></a>Analyzátory IDE versus StyleCop

**OTÁZKA**: Jaký je rozdíl mezi analyzátory kódu integrovaného vývojového prostředí (IDE) sady Visual Studio a analyzátory StyleCop?

**A**: Integrované vývojové prostředí (IDE) sady Visual Studio obsahuje integrované analyzátory, které hledají jak styl kódu, tak i problémy s kvalitou. Tato pravidla vám pomůžou používat nové jazykové funkce při jejich zavedení a zlepšení udržovatelnosti kódu. Analyzátory IDE se průběžně aktualizují s každou verzí sady Visual Studio.

[Analyzátory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) jsou nainstalované analyzátory třetích stran jako balíček NuGet, který kontroluje konzistenci stylů ve vašem kódu. Obecně platí, že pravidla StyleCop umožňují nastavit osobní předvolby pro základ kódu bez doporučení jednoho stylu nad jiným.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyzátory kódu oproti starší analýze

**OTÁZKA**: Jaký je rozdíl mezi staršími verzemi analýzy a analýz kódu založenými na .NET Compiler Platform?

Odpověď **: Analýza kódu na základě**.NET Compiler Platform analyzuje zdrojový kód v reálném čase a během kompilace, zatímco starší verze analýzy analyzuje binární soubory po dokončení sestavení. Další informace najdete v [nejčastějších dotazech](fxcop-analyzers-faq.md)k [analýze na základě .NET Compiler Platform](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) a analyzátoru FxCop.

## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

**OTÁZKA**: Můj projekt používá možnost sestavení k považovat upozornění jako chyby. Po migraci ze starší verze analýzy do analýzy zdrojového kódu se nyní všechna upozornění analýzy kódu zobrazují jako chyby. Jak to můžu zabránit?

**A**: Chcete-li zabránit tomu, aby byla upozornění analýzy kódu považována za chyby, postupujte takto:

  1. Vytvořte soubor. props s následujícím obsahem:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Přidejte řádek do souboru projektu. csproj nebo. vbproj pro import souboru. props, který jste vytvořili v předchozím kroku. Tento řádek musí být umístěn před řádky, které importují soubory FxCop Analyzer. props. Například pokud má soubor. props název CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Viz také:

- [Přehled analyzátorů](roslyn-analyzers-overview.md)
- [EditorConfig nastavení konvence psaní kódu .NET](../ide/editorconfig-code-style-settings-reference.md)
