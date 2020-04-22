---
title: EditorConfig versus analyzátory
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760130"
---
# <a name="code-analysis-faq"></a>Nejčastější dotazy k analýze kódu

Tato stránka obsahuje odpovědi na některé často kladené otázky týkající se analýzy kódu na platformě .NET Compiler Platform v sadě Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analýza kódu versus EditorConfig

**Otázka:** Mám použít analýzu kódu nebo EditorConfig pro kontrolu stylu kódu?

**A**: Analýza kódu a EditorConfig soubory pracují ruku v ruce. Když definujete styly kódu [v souboru EditorConfig](../ide/editorconfig-code-style-settings-reference.md) nebo na stránce [Možnosti textového editoru,](../ide/code-styles-and-code-cleanup.md) ve skutečnosti konfigurujete analyzátory kódu, které jsou integrovány do sady Visual Studio. EditorConfig soubory lze použít k povolení nebo zakázání pravidla analyzátoru, a také nakonfigurovat některé balíčky analyzátoru NuGet, jako jsou [fxcop analyzátory](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig versus sady pravidel

**Otázka:** Mám nakonfigurovat analyzátory pomocí sady pravidel nebo souboru EditorConfig?

**A**: Sady pravidel a EditorConfig soubory mohou existovat vedle sebe a lze použít ke konfiguraci analyzátory. Soubory EditorConfig i sady pravidel umožňují povolit a zakázat pravidla a nastavit jejich závažnost.

Soubory EditorConfig však nabízejí další způsoby konfigurace pravidel:

- Pro analyzátory FxCop, EditorConfig soubory umožňují [definovat, které typy kódu k analýze](fxcop-analyzer-options.md).
- Pro analyzátory stylu kódu, které jsou integrovány do sady Visual Studio, editorconfig soubory umožňují [definovat upřednostňované styly kódu](../ide/editorconfig-code-style-settings-reference.md) pro základ kódu.

Kromě sady pravidel a EditorConfig soubory, některé analyzátory jsou konfigurovány pomocí textových souborů označených jako [další soubory](../ide/build-actions.md#build-action-values) pro c# a VB kompilátory.

> [!NOTE]
> - EditorConfig soubory lze použít pouze k povolení pravidel a nastavit jejich závažnost v Sadě Visual Studio 2019 verze 16.3 a novější.
> - EditorConfig soubory nelze použít ke konfiguraci starší analýzy, vzhledem k tomu, že sady pravidel může.

## <a name="code-analysis-in-ci-builds"></a>Analýza kódu v sestaveních CI

**Otázka:** Funguje analýza kódu založená na platformě kompilátoru .NET v sestaveních průběžné integrace (CI)?

**A:** Ano. Pro analyzátory, které jsou nainstalovány z balíčku NuGet, tato pravidla jsou [vynucena v době sestavení](roslyn-analyzers-overview.md#build-errors), včetně během sestavení CI. Analyzátory používané v CI sestavení respektovat konfiguraci pravidel z obou sad pravidel a EditorConfig soubory. V současné době analyzátory kódu, které jsou integrovány do sady Visual Studio nejsou k dispozici jako balíček NuGet, a proto tato pravidla nejsou vynutitelné v sestavení CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analyzátory IDE versus StyleCop

**Otázka:** Jaký je rozdíl mezi analyzátory kódu IDE sady Visual Studio a analyzátory StyleCop?

**A**: Visual Studio IDE obsahuje integrované analyzátory, které hledají styl kódu a problémy s kvalitou. Tato pravidla vám pomohou používat nové jazykové funkce při jejich zavedení a zlepšit udržovatelnost kódu. Analyzátory IDE jsou průběžně aktualizovány s každou verzí sady Visual Studio.

[Analyzátory StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) jsou analyzátory třetích stran nainstalované jako balíček NuGet, které kontrolují konzistenci stylu ve vašem kódu. Obecně pravidla StyleCop umožňují nastavit osobní předvolby pro základ kódu bez doporučování jednoho stylu nad jiným.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analyzátory kódu versus starší analýza

**Otázka:** Jaký je rozdíl mezi starší analýzou a analýzou kódu na platformě .NET Compiler?

**A**: Analýza kódu založené na platformě .NET Compiler platformy analyzuje zdrojový kód v reálném čase a během kompilace, zatímco starší analýza analyzuje binární soubory po dokončení sestavení. Další informace naleznete v [tématu .NET Compiler Platform-based analysis versus legacy analysis](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) and [FxCop analyzátory FAQ](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Považovat upozornění za chyby

**Otázka:** Můj projekt používá možnost sestavení k tomu, aby s upozorněními zacházel jako s chybami. Po migraci ze starší analýzy na analýzu zdrojového kódu se všechna upozornění na analýzu kódu nyní zobrazují jako chyby. Jak tomu mohu zabránit?

**A**: Chcete-li zabránit upozornění analýzy kódu z považovány za chyby, postupujte takto:

  1. Vytvořte soubor .props s následujícím obsahem:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Přidejte řádek do souboru projektu .csproj nebo .vbproj a importujte soubor .props, který jste vytvořili v předchozím kroku. Tento řádek musí být umístěn před všechny řádky, které importují soubory Analyzátoru FxCop .props. Pokud je například soubor .props pojmenován codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Stránka vlastností řešení analýzy kódu

**Otázka:** Kde je stránka vlastností Analýza kódu pro řešení?

**A**: Stránka vlastností Analýza kódu na úrovni řešení byla odebrána ve prospěch spolehlivější skupiny sdílených vlastností. Pro správu analýzy kódu na úrovni projektu je stále k dispozici stránka vlastností Analýza kódu. (Pro spravované projekty doporučujeme také migraci z pravidel na EditorConfig pro konfiguraci pravidla.)  Pro sdílení pravidel mezi více nebo všechny projekty v řešení nebo úložiště, doporučujeme definovat skupinu vlastností s CodeAnalysisRuleSet vlastnost ve sdíleném souboru rekvizity/cíle nebo Directory.props/Directory.targets souboru. Pokud nemáte žádné takové společné rekvizity nebo cíle, které importují všechny projekty, měli byste zvážit [přidání takové skupiny vlastností do adresáře Directory.props nebo Directory.targets v adresáři řešení nejvyšší úrovně, který je automaticky importován ve všech souborech projektu definovaných v adresáři nebo jeho podadresářích](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets).

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů](roslyn-analyzers-overview.md)
- [Nastavení konvence kódování .NET pro EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
