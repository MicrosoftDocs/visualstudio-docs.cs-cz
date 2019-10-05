---
title: Analýza kódu pomocí analyzátorů Roslyn
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: af237fbc3ce7bcf098cd47065ed18d1dfd7f20a2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975013"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>Přehled .NET Compiler Platform analyzátory kódu

Analyzátory .NET Compiler Platform ("Roslyn") analyzují kód pro styl, kvalitu a udržovatelnost, návrh a další problémy. Sada Visual Studio obsahuje integrovanou sadu analyzátorů, které analyzují C# nebo Visual Basic kód při psaní. Předvolby pro tyto integrované analyzátory můžete nakonfigurovat na stránce [Možnosti textový editor](../ide/code-styles-and-code-cleanup.md) nebo v [souboru. editorconfig](../ide/editorconfig-code-style-settings-reference.md). Další analyzátory můžete nainstalovat jako rozšíření sady Visual Studio nebo balíček NuGet.

Pokud je porušení pravidel Nalezeno analyzátorem, jsou hlášeny v editoru kódu (jako *vlnovku* pod problematickým kódem) a v okně **Seznam chyb** .

Mnoho pravidel analyzátoru nebo *diagnostiky*má jednu nebo více souvisejících *oprav kódu* , které můžete použít pro opravu problému. Diagnostika analyzátoru, která je součástí sady Visual Studio, má přidruženou opravu kódu. Opravy kódu se zobrazují v nabídce ikony žárovky spolu s dalšími typy [rychlých akcí](../ide/quick-actions.md). Informace o těchto opravách kódu najdete v tématu [běžné rychlé akce](../ide/common-quick-actions.md).

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>Analýzy na základě .NET Compiler Platform oproti starší analýze

Analýza kódu .NET Compiler Platform ("Roslyn") nakonec nahradí [starší verzi analýzy](../code-quality/code-analysis-for-managed-code-overview.md) pro spravovaný kód. Spousta starších pravidel analýzy již byla přepsána jako analyzátory kódu založené na .NET Compiler Platform.

Podobně jako porušení pravidel pro analýzu starších verzí se v okně Seznam chyb v aplikaci Visual Studio zobrazí narušení analýzy kódu na základě .NET Compiler Platform. Kromě toho se v editoru kódu zobrazují také porušení .NET Compiler Platform analýzy kódu, jako *vlnovky* pod problematickým kódem. Barva vlnovky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#rule-severity) pravidla. Následující snímek obrazovky ukazuje tři porušení @ no__t-0one Red, One zelená a jedna šedá:

![Vlnovky v editoru kódu](media/diagnostics-severity-colors.png)

Analyzátory kódu založené na .NET Compiler Platform analyzují kód v době sestavování, jako je například analýza starší verze, pokud je povolená, ale také při psaní za provozu. Pokud povolíte [úplnou analýzu řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis), analyzátory kódu také poskytují analýzu v době návrhu soubory kódu, které nejsou otevřeny v editoru.

> [!TIP]
> Chyby při sestavování a varování z analyzátorů kódu se zobrazují pouze v případě, že analyzátory jsou nainstalovány jako balíček NuGet.

Pouze analyzátory kódu založené na .NET Compiler Platform sestavují stejné typy problémů jako v rámci starší analýzy, ale usnadňují vám opravu jednoho nebo všech výskytů porušení v souboru nebo projektu. Tyto akce se nazývají *opravy kódu*. Opravy kódu jsou specifické pro IDE; v aplikaci Visual Studio jsou implementovány jako [rychlé akce](../ide/quick-actions.md). Ne všechny diagnostické nástroje analyzátoru mají přidruženou opravu kódu.

> [!NOTE]
> Následující možnosti uživatelského rozhraní se vztahují jenom na starší verzi analýzy:
>
> - Možnost příkazu **analyzovat** >  spustit příkaz pro**analýzu kódu** .
> - **Spuštění při sestavení** a **potlačení výsledků z vygenerovaného kódu** se zaškrtne na kartě **Analýza kódu** stránky vlastností projektu.

Chcete-li rozlišovat mezi porušením analyzátorů kódu a analýzou starší verze v okně Seznam chyb, podívejte se do sloupce **Nástroj** . Pokud hodnota nástroje odpovídá jednomu ze sestavení analyzátoru v **Průzkumník řešení**, například **Microsoft. CodeQuality. analyzers**, narušení pochází z analyzátoru kódu. V opačném případě porušení vychází z analýzy starší verze.

![Sloupec nástroje v Seznam chyb](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Vlastnost **RunCodeAnalysis** MSBuild v souboru projektu se vztahuje pouze na starší verzi analýzy. Pokud nainstalujete analyzátory, nastavte **RunCodeAnalysis** na **hodnotu false** v souboru projektu, aby se zabránilo spuštění starší verze analýzy po sestavení.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Balíček NuGet versus rozšíření VSIX

Analyzátory .NET Compiler Platform lze instalovat podle projektu prostřednictvím balíčku NuGet nebo sady Visual Studio – v rámci rozšíření sady Visual Studio. Existují některé rozdíly v chování při [instalaci analyzátorů](../code-quality/install-roslyn-analyzers.md)mezi těmito dvěma způsoby.

### <a name="scope"></a>Scope

Pokud nainstalujete analyzátory jako rozšíření sady Visual Studio, vztahují se na úroveň řešení na všechny instance sady Visual Studio. Pokud nainstalujete analyzátory jako balíček NuGet, což je upřednostňovaná metoda, vztahují se pouze na projekt, ve kterém byl balíček NuGet nainstalován. V týmových prostředích jsou analyzátory nainstalované jako balíčky NuGet v oboru pro *všechny vývojáře* , kteří na daném projektu pracují.

### <a name="build-errors"></a>Chyby sestavení

Pokud chcete, aby byla pravidla vynutila při sestavování, včetně prostřednictvím příkazového řádku nebo v rámci sestavení kontinuální integrace (CI), nainstalujte analyzátory jako balíček NuGet. V sestavě sestavení se nezobrazují upozornění a chyby analyzátoru, pokud nainstalujete analyzátory jako rozšíření.

Následující snímek obrazovky ukazuje výstup sestavení z příkazového řádku z sestavení projektu, který obsahuje narušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušením pravidla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Závažnost pravidla

Nemůžete nastavit závažnost pravidel z analyzátorů, které se nainstalovaly jako rozšíření sady Visual Studio. Pokud chcete nakonfigurovat [závažnost pravidla](../code-quality/use-roslyn-analyzers.md#rule-severity), nainstalujte analyzátory jako balíček NuGet.

## <a name="categories"></a>Categories

Níže jsou uvedeny různé typy analyzátorů, které vám pomohou analyzovat váš kód:

- Doporučené analyzátory Microsoftu: [Analyzátory FxCop](../code-quality/fxcop-analyzers.yml)
- Analyzátory rozhraní IDE sady Visual Studio: [EditorConfig](../ide/code-styles-and-code-cleanup.md)
- Analyzátory třetích stran: [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator/), [analyzátory XUnit](https://www.nuget.org/packages/xunit.analyzers/), [analyzátor sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Instalace analyzátorů kódu v aplikaci Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Použití analyzátorů kódu v aplikaci Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Viz také:

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Zápis vlastního analyzátoru kódu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
