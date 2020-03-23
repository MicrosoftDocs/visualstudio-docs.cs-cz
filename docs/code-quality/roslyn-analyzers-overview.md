---
title: Analýza kódu pomocí analyzátorů Roslyn
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431277"
---
# <a name="overview-of-source-code-analyzers"></a>Přehled analyzátorů zdrojového kódu

Analyzátory kódu .NET Compiler Platform ("Roslyn") kontrolují kód jazyka C# nebo Visual Basic pro styl, kvalitu a udržovatelnost, návrh a další problémy.

- Některé analyzátory jsou integrovány do sady Visual Studio. Diagnostické ID nebo kód pro tyto analyzátory je ve formátu IDExxxx, například IDE0067. Většina těchto vestavěných analyzátorů kontroluje [styl kódu](../ide/code-styles-and-code-cleanup.md)a předvolby můžete konfigurovat na [stránce možností textového editoru](../ide/code-styles-and-code-cleanup.md) nebo v [souboru EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Několik vestavěných analyzátorů se dívá na kvalitu kódu.

- Můžete nainstalovat další analyzátory jako balíček NuGet nebo rozšíření sady Visual Studio. Například:

  - [FxCop analyzátory](../code-quality/install-fxcop-analyzers.md), Microsoft doporučené analyzátory kvality kódu
  - Analyzátory třetích stran, například [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [Analyzátory XUnit](https://www.nuget.org/packages/xunit.analyzers/)a [Analyzátor sonaru](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Pokud analyzátor zjistí porušení pravidel, jsou hlášeny v editoru kódu (jako *klikyhákpod* problematickým kódem) a v okně Seznam chyb.

Mnoho pravidel analyzátoru nebo *diagnostiky*mají jednu nebo více *souvisejících oprav kódu,* které můžete použít k opravě problému. Diagnostika analyzátoru, které jsou integrovány do sady Visual Studio každý mají přidružený kód opravit. Opravy kódu jsou zobrazeny v nabídce ikony žárovky spolu s dalšími typy [rychlých akcí](../ide/quick-actions.md). Informace o těchto opravách kódu naleznete [v tématu Běžné rychlé akce](../ide/common-quick-actions.md).

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analýza zdrojového kódu versus starší analýza

Zdrojová analýza analyzátory Roslyn nahrazuje [starší analýzu](../code-quality/code-analysis-for-managed-code-overview.md) spravovaného kódu. Mnoho starších pravidel analýzy již bylo přepsáno jako analyzátory kódu Roslyn. U novějších šablon projektů, jako jsou projekty .NET Core a .NET Standard, není analýza starší verze ani k dispozici.

Stejně jako porušení pravidel starší analýzy se porušení analýzy zdrojového kódu zobrazují v okně Seznam chyb v sadě Visual Studio. Kromě toho porušení analýzy zdrojového kódu také zobrazit v editoru kódu jako *klikyháky* pod problematický kód. Barva vlnovky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#rule-severity) pravidla. Následující obrázek znázorňuje&mdash;tři porušení, jedno červené, jedno zelené a jedno šedé:

![Vlnky v editoru kódu v sadě Visual Studio](media/diagnostics-severity-colors.png)

Analyzátory kódu kontrolují kód v době sestavení, jako je starší analýza, pokud je povolená, ale také živé při psaní. Můžete nakonfigurovat rozsah analýzy živého kódu, který se provede pouze pro aktuální dokument, všechny otevřené dokumenty nebo celé řešení. Viz [Postup: Konfigurace rozsahu analýzy živého kódu](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Chyby a upozornění z analyzátorů kódu se zobrazí pouze v případě, že analyzátory jsou nainstalovány jako balíček NuGet. Předdefinované analyzátory (například IDE0067 a IDE0068) nikdy spustit během sestavení.

Nejen, že analyzátory kódu Roslyn hlásí stejné typy problémů, které provádí starší analýza, ale usnadňují opravu jednoho nebo všech výskytů porušení v souboru nebo projektu. Tyto akce se nazývají *opravy kódu*. Opravy kódu jsou specifické pro ide; v sadě Visual Studio jsou implementovány jako [rychlé akce](../ide/quick-actions.md). Ne všechny diagnostiky analyzátoru mají přidruženou opravu kódu.

> [!NOTE]
> Před vydáním Visual Studia 2019 16.5 provede možnost nabídky **Analyzovat** > **analýzu kódu analýzu** spuštění starší verze. Spuštění visual studio 2019 16.5, **spustit analýzu kódu** možnost nabídky spustí analyzátory založené na Roslyn pro vybraný projekt nebo řešení.

Chcete-li rozlišovat mezi porušeníz analyzátory kódu a starší analýzy v seznamu chyb, podívejte se na **sloupec Nástroj.** Pokud hodnota nástroje odpovídá jednomu ze sestavení analyzátoru v **Průzkumníku řešení**, například **Microsoft.CodeQuality.Analyzers**, porušení pochází z analyzátoru kódu. V opačném případě porušení pochází z starší analýzy.

![Sloupec nástroje v seznamu chyb](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Vlastnost **RunCodeAnalysis** MSBuild v souboru projektu se vztahuje pouze na starší analýzu. Pokud nainstalujete analyzátory, nastavte **RunCodeAnalysis** na **false** v souboru projektu, aby se zabránilo starší analýzy spuštění po sestavení.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Balíček NuGet versus rozšíření VSIX

Analyzátory kódu Roslyn lze nainstalovat na projekt prostřednictvím balíčku NuGet. Některé jsou také k dispozici jako rozšíření sady Visual Studio, v takovém případě se vztahují na jakékoli řešení, které otevřete v sadě Visual Studio. Mezi těmito dvěma způsoby [instalace analyzátorů](../code-quality/install-roslyn-analyzers.md)existují některé klíčové rozdíly v chování .

### <a name="scope"></a>Rozsah

Pokud nainstalujete analyzátory jako rozšíření sady Visual Studio, platí na úrovni řešení a na všechny instance sady Visual Studio. Pokud nainstalujete analyzátory jako balíček NuGet, což je upřednostňovaná metoda, platí pouze pro projekt, kde byl nainstalován balíček NuGet. V týmových prostředích analyzátory nainstalované jako balíčky NuGet jsou v oboru pro *všechny vývojáře,* kteří pracují na tomto projektu.

### <a name="build-errors"></a>Chyby sestavení

Chcete-li mít pravidla vynucená v době sestavení, včetně prostřednictvím příkazového řádku nebo jako součást sestavení průběžné integrace (CI), nainstalujte analyzátory jako balíček NuGet. Upozornění a chyby analyzátoru se nezobrazují v sestavě sestavení, pokud nainstalujete analyzátory jako rozšíření.

Následující obrázek znázorňuje výstup sestavení příkazového řádku z vytváření projektu, který obsahuje porušení pravidel analyzátoru:

![Výstup MSBuild s porušením pravidel](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Závažnost pravidla

Závažnost pravidel nelze konfigurovat z analyzátorů, které byly nainstalovány jako rozšíření sady Visual Studio. Chcete-li nakonfigurovat [závažnost pravidla](../code-quality/use-roslyn-analyzers.md#rule-severity), nainstalujte analyzátory jako balíček NuGet.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Instalace analyzátorů kódu v sadě Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Použití analyzátorů kódu v sadě Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Viz také

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Napište vlastní analyzátor kódu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Sada .NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
