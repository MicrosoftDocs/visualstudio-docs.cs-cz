---
title: EditorConfig versus analyzátory
ms.date: 03/11/2019
description: Přečtěte si informace o analýze kódu na základě .NET Compiler Platform v aplikaci Visual Studio. Přečtěte si odpovědi na otázky týkající se souborů EditorConfig, sad pravidel a dalších témat.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6d67471027f36d0e22c055f4306ce2137d972463
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800483"
---
# <a name="code-analysis-faq"></a>Nejčastější dotazy k analýze kódu

Tato stránka obsahuje odpovědi na některé nejčastější dotazy týkající se analýzy kódu založené na .NET Compiler Platform v aplikaci Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analýza kódu oproti EditorConfig

**Otázka**: mám použít analýzu kódu nebo EditorConfig pro kontrolu stylu kódu?

Odpověď **: analýza** kódu a soubory EditorConfig fungují ručně. Při definování stylů kódu [v souboru EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) nebo na stránce [Možnosti textového editoru](../ide/code-styles-and-code-cleanup.md) ve skutečnosti konfigurujete analyzátory kódu, které jsou součástí sady Visual Studio. Soubory EditorConfig se dají použít k povolení nebo zakázání pravidel analyzátoru a také ke konfiguraci balíčků NuGet Analyzer.

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig oproti sadám pravidel

**Otázka**: mám nakonfigurovat analyzátory pomocí sady pravidel nebo souboru EditorConfig?

Odpověď: sady pravidel a soubory EditorConfig mohou existovat společně a **lze je použít** ke konfiguraci analyzátorů. Soubory EditorConfig a sady pravidel umožňují povolit a zakázat pravidla a nastavit jejich závažnost.

Soubory EditorConfig ale nabízejí další způsoby, jak pravidla konfigurovat:

- Pro analyzátory kvality kódu .NET vám EditorConfig soubory umožňují [definovat, které typy kódu se mají analyzovat](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
- Pro analyzátory ve stylu kódu .NET, které jsou součástí sady Visual Studio, umožňují soubory EditorConfig [definovat preferované styly kódu](/dotnet/fundamentals/code-analysis/code-style-rule-options) pro základ kódu.

Kromě sad pravidel a souborů EditorConfig jsou některé analyzátory nakonfigurovány pomocí textových souborů označených jako [Další soubory](../ide/build-actions.md#build-action-values) pro kompilátory jazyka C# a VB.

> [!NOTE]
> - Soubory EditorConfig se dají použít jenom k povolení pravidel a nastavení jejich závažnosti v sadě Visual Studio 2019 verze 16,3 a novější.
> - Soubory EditorConfig se nedají použít ke konfiguraci analýzy starší verze, zatímco sady pravidel můžou.

## <a name="code-analysis-in-ci-builds"></a>Analýza kódu v sestaveních CI

**Otázka:** Funguje .NET Compiler Platform kódu na základě kódu v sestaveních kontinuální integrace (CI)?

**A**: Ano. Pro analyzátory, které jsou nainstalované z balíčku NuGet, se tato pravidla vynucuje v době sestavení [,](roslyn-analyzers-overview.md#build-errors)včetně během sestavení CI. Analyzátory používané v sestaveních CI respektují konfiguraci pravidel ze sad pravidel i souborů EditorConfig. V současné době nejsou analyzátory kódu integrované do Visual Studio k dispozici jako balíček NuGet, a proto tato pravidla nelze vynutit v sestavení CI.

## <a name="ide-analyzers-versus-stylecop"></a>Porovnání analyzátorů IDE a StyleCop

**Otázka:** Jaký je rozdíl mezi analyzátory kódu INTEGROVANÉho vývojového Visual Studio a analyzátory StyleCop?

**A:** Integrované Visual Studio obsahuje integrované analyzátory, které hledejí problémy se stylem kódu i kvalitou. Tato pravidla vám pomůžou používat nové funkce jazyka při jejich zavádíte a zlepšíte udržovatelnost kódu. Analyzátory IDE se průběžně aktualizují s každou Visual Studio verzí.

[Analyzátory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) jsou analyzátory třetích stran nainstalované jako balíček NuGet, které kontroluji konzistenci stylu ve vašem kódu. Obecně platí, že pravidla StyleCop umožňují nastavit osobní předvolby základu kódu, aniž byste doporučovali jeden styl před jiným.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyzátory kódu versus starší verze analýzy

**Otázka:** Jaký je rozdíl mezi starší verzí analýzy a .NET Compiler Platform kódu založeným na verzích?

**A**: .NET Compiler Platform kódu založená na kódu analyzuje zdrojový kód v reálném čase a během kompilace, zatímco starší verze analýzy analyzuje binární soubory po dokončení sestavení. Další informace najdete v tématu [.NET Compiler Platform analýza na základě verzí a starší verze analýzy.](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

## <a name="fxcop-analyzers-versus-net-analyzers"></a>Analyzátory FxCop versus analyzátory .NET

**Otázka:** Jaký je rozdíl mezi analyzátory FxCop a analyzátory .NET?

**A:** Analyzátory FxCop i analyzátory .NET odkazovat na implementace analyzátoru .NET Compiler Platform (Roslyn) pravidel certifikační autority FxCop. Před vydáním sady Visual Studio 2019 16,8 a .NET 5,0 byly tyto analyzátory dodávány jako `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). Počínaje sadou Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Jsou také k dispozici jako `Microsoft.CodeAnalysis.NetAnalyzers` [balíček NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Zvažte prosím možnost [migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="treat-warnings-as-errors"></a>Zpracovávat upozornění jako chyby

**Otázka**: můj projekt používá možnost sestavení k považovat upozornění jako chyby. Po migraci ze starší verze analýzy do analýzy zdrojového kódu se nyní všechna upozornění analýzy kódu zobrazují jako chyby. Jak to můžu zabránit?

Odpověď **: Chcete-li** zabránit tomu, aby se výstraha analýzy kódu nacházela jako chyby, postupujte podle následujících kroků:

  1. Vytvořte soubor. props s následujícím obsahem:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Přidejte řádek do souboru projektu. csproj nebo. vbproj pro import souboru. props, který jste vytvořili v předchozím kroku. Tento řádek musí být umístěn před řádky, které importují soubory Analyzer. props. Například pokud má soubor. props název CodeAnalysis. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Stránka vlastností řešení analýzy kódu

**Otázka**: kde je stránka vlastností analýzy kódu pro řešení?

Odpověď **: stránka** vlastností analýzy kódu na úrovni řešení se odebrala a upřednostňuje spolehlivější sdílenou skupinu vlastností. Pro správu analýzy kódu na úrovni projektu je stránka vlastností analýza kódu stále k dispozici. (U spravovaných projektů doporučujeme také migrovat z RuleSets na EditorConfig pro konfiguraci pravidel.)  Pro sdílení RuleSets napříč několika/všemi projekty v rámci řešení nebo úložiště doporučujeme definovat skupinu vlastností s vlastností [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) v souboru Shared/Targets nebo *Directory. props/Directory. targets* . Pokud tyto běžné vlastnosti nebo cíle nechcete importovat do všech projektů, měli byste zvážit přidání takové skupiny vlastností do [souboru Directory. props nebo Directory. targets](../msbuild/customize-your-build.md) v adresáři řešení na nejvyšší úrovni, který je automaticky importován do všech souborů projektu definovaných v adresáři nebo v jeho podadresářích.

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů](roslyn-analyzers-overview.md)
- [Nastavení konvence psaní kódu .NET pro EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)