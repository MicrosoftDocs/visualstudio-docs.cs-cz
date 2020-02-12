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
ms.openlocfilehash: 34225858e88f4ee969f0e51013bcdb04812d425f
ms.sourcegitcommit: a86ee68e3ec23869b6eaaf6c6b7946b1d9a88d01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77144770"
---
# <a name="overview-of-source-code-analyzers"></a>Přehled analyzátorů zdrojového kódu

Analyzátory kódu .NET Compiler Platform ("Roslyn") kontrolují C# svůj kód nebo Visual Basic v případě stylu, kvality a udržovatelnosti, návrhu a dalších problémů.

- Některé analyzátory jsou integrované do sady Visual Studio. ID diagnostiky nebo kód pro tyto analyzátory mají formát IDExxxx, například IDE0067. Většina těchto vestavěných analyzátorů kontroluje [styl kódu](../ide/code-styles-and-code-cleanup.md)a můžete nakonfigurovat předvolby na [stránce Možnosti textového editoru](../ide/code-styles-and-code-cleanup.md) nebo v [souboru EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Několik předdefinovaných analyzátorů se podívejte na kvalitu kódu.

- Další analyzátory můžete nainstalovat jako balíček NuGet nebo rozšíření sady Visual Studio. Například:

  - [Analyzátory FxCop](../code-quality/install-fxcop-analyzers.md), Doporučené analyzátory kvality kódu Microsoftu
  - Analyzátory třetích stran, například [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [analyzátory XUnit](https://www.nuget.org/packages/xunit.analyzers/)a [analyzátor sonar](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

Pokud je v analyzátoru zjištěna porušení pravidla, jsou uvedena v editoru kódu (jako *vlnovku* pod problematickým kódem) a v okně Seznam chyb.

Mnoho pravidel analyzátoru nebo *diagnostiky*má jednu nebo více souvisejících *oprav kódu* , které můžete použít pro opravu problému. Diagnostika analyzátoru, která je součástí sady Visual Studio, má přidruženou opravu kódu. Opravy kódu se zobrazují v nabídce ikony žárovky spolu s dalšími typy [rychlých akcí](../ide/quick-actions.md). Informace o těchto opravách kódu najdete v tématu [běžné rychlé akce](../ide/common-quick-actions.md).

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>Analýza zdrojového kódu oproti starší analýze

Zdrojová analýza pomocí analyzátorů Roslyn nahrazuje [starší verzi analýzy](../code-quality/code-analysis-for-managed-code-overview.md) spravovaného kódu. Spousta starších pravidel analýzy již byla přepsána jako analyzátory kódu Roslyn. Pro novější šablony projektů, jako jsou například .NET Core a .NET Standard projekty, není starší verze analýzy ani dostupná.

Podobně jako porušení pravidel pro analýzu starších verzí se v okně Seznam chyb v aplikaci Visual Studio zobrazí porušení analýzy zdrojového kódu. Kromě toho se porušení analýzy zdrojového kódu zobrazí také v editoru kódu jako *vlnovky* pod problematickým kódem. Barva vlnovky závisí na [nastavení závažnosti](../code-quality/use-roslyn-analyzers.md#rule-severity) pravidla. Následující obrázek ukazuje tři porušení&mdash;jedna červená, jedna zelená a jedna šedá:

![Vlnovky v editoru kódu v aplikaci Visual Studio](media/diagnostics-severity-colors.png)

Analyzátory kódu kontrolují kód v době sestavování, jako je například analýza starší verze, pokud je povolená, ale také živě při psaní. Pokud povolíte [úplnou analýzu řešení](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis), analyzátory kódu také poskytují analýzu v době návrhu soubory kódu, které nejsou otevřeny v editoru.

> [!TIP]
> Chyby při sestavování a varování z analyzátorů kódu se zobrazují pouze v případě, že analyzátory jsou nainstalovány jako balíček NuGet. Předdefinované analyzátory (například IDE0067 a IDE0068) nikdy neběží během sestavování.

Nejen Roslyn analyzátory kódu sestavují stejné typy problémů, které provádí starší analýza, ale usnadňují vám opravu jednoho nebo všech výskytů porušení v souboru nebo projektu. Tyto akce se nazývají *opravy kódu*. Opravy kódu jsou specifické pro IDE; v aplikaci Visual Studio jsou implementovány jako [rychlé akce](../ide/quick-actions.md). Ne všechny diagnostické nástroje analyzátoru mají přidruženou opravu kódu.

> [!NOTE]
> Možnost **analyzovat** > **Spustit příkaz Analýza kódu** se vztahuje pouze na starší verzi analýzy.

Chcete-li rozlišovat mezi porušením analyzátorů kódu a analýzou starší verze v Seznam chyb, podívejte se do sloupce **nástroje** . Pokud hodnota nástroje odpovídá jednomu ze sestavení analyzátoru v **Průzkumník řešení**, například **Microsoft. CodeQuality. analyzers**, narušení pochází z analyzátoru kódu. V opačném případě porušení vychází z analýzy starší verze.

![Sloupec nástroje v Seznam chyb](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> Vlastnost **RunCodeAnalysis** MSBuild v souboru projektu se vztahuje pouze na starší verzi analýzy. Pokud nainstalujete analyzátory, nastavte **RunCodeAnalysis** na **hodnotu false** v souboru projektu, aby se předešlo tomu, že se starší verze analýzy spustí po sestavení.
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>Balíček NuGet versus rozšíření VSIX

Analyzátory kódu Roslyn se dají nainstalovat na projekt prostřednictvím balíčku NuGet. Některé jsou také k dispozici jako rozšíření sady Visual Studio. v takovém případě se vztahují na jakékoli řešení, které jste otevřeli v aplikaci Visual Studio. Existují některé rozdíly v chování při [instalaci analyzátorů](../code-quality/install-roslyn-analyzers.md)mezi těmito dvěma způsoby.

### <a name="scope"></a>Rozsah

Pokud nainstalujete analyzátory jako rozšíření sady Visual Studio, budou použity na úrovni řešení a na všechny instance aplikace Visual Studio. Pokud nainstalujete analyzátory jako balíček NuGet, což je upřednostňovaná metoda, vztahují se pouze na projekt, ve kterém byl balíček NuGet nainstalován. V týmových prostředích jsou analyzátory nainstalované jako balíčky NuGet v oboru pro *všechny vývojáře* , kteří na daném projektu pracují.

### <a name="build-errors"></a>Chyby sestavení

Pokud chcete, aby byla pravidla vynutila při sestavování, včetně prostřednictvím příkazového řádku nebo v rámci sestavení kontinuální integrace (CI), nainstalujte analyzátory jako balíček NuGet. V sestavě sestavení se nezobrazují upozornění a chyby analyzátoru, pokud nainstalujete analyzátory jako rozšíření.

Následující obrázek ukazuje výstup sestavení příkazového řádku z sestavení projektu, který obsahuje porušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušením pravidla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Závažnost pravidla

Nemůžete nakonfigurovat závažnost pravidel z analyzátorů, které se nainstalovaly jako rozšíření sady Visual Studio. Pokud chcete nakonfigurovat [závažnost pravidla](../code-quality/use-roslyn-analyzers.md#rule-severity), nainstalujte analyzátory jako balíček NuGet.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Instalace analyzátorů kódu v aplikaci Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Použití analyzátorů kódu v aplikaci Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Viz také

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Zápis vlastního analyzátoru kódu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Sada .NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
