---
title: Analýza kódu pomocí analyzátorů Roslyn
ms.date: 09/01/2020
description: Seznamte se s analýzou zdrojového kódu v Visual Studio. Seznamte se s opravami kódu a různými typy analyzátorů a úrovněmi závažnosti.
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798333"
---
# <a name="overview-of-source-code-analysis"></a>Přehled analýzy zdrojového kódu

.NET Compiler Platform (Roslyn) kontroluji kód jazyka C# nebo Visual Basic z pohledu problémů se stylem, kvalitou, udržovatelností, návrhem a dalšími problémy. Tato kontrola nebo analýza se provádí během návrhu ve všech otevřených souborech.

Analyzátory lze rozdělit do následujících skupin:

- [Analyzátory](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories) stylu kódu jsou integrované do Visual Studio. ID diagnostiky neboli kód pro tyto analyzátory má formát IDExxxx, například IDE0067. Předvolby můžete konfigurovat na stránce možností [textového editoru](../ide/code-styles-and-code-cleanup.md) nebo v [souboru EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options). Od verze .NET 5.0 jsou analyzátory stylu kódu součástí sady .NET SDK a je možné je striktně vynutit jako upozornění nebo chyby sestavení. Další informace najdete [tady.](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis)

- [Analyzátory](/dotnet/fundamentals/code-analysis/quality-rules/index) kvality kódu jsou teď součástí sady .NET 5 SDK a ve výchozím nastavení jsou povolené. ID diagnostiky nebo kód pro tyto analyzátory má formát CAxxxx, například CA1822. Další informace najdete v tématu [Přehled analýzy kvality kódu .NET.](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)

- Analyzátory třetích stran je možné nainstalovat jako balíček NuGet nebo Visual Studio rozšíření. Analyzátory třetích stran, jako [jsou StyleCop,](https://www.nuget.org/packages/StyleCop.Analyzers/) [Roslynator,](https://www.nuget.org/packages/Roslynator.Analyzers/) [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/)a [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="severity-levels-of-analyzers"></a>Úrovně závažnosti analyzátorů

Každý analyzátor má jednu z následujících úrovní závažnosti:

| Závažnost (Průzkumník řešení) | Závažnost (soubor EditorConfig) | Chování při sestavení | Chování editoru |
|-|-|-|
| Chyba | `error` | Porušení se zobrazují jako *chyby* v seznam chyb a ve výstupu sestavení příkazového řádku a způsobují selhání sestavení.| Poškozený kód je podtržen červenou vlnovkou a označený malým červeným polem na posuvníku. |
| Upozornění | `warning` | Porušení se zobrazí jako *Upozornění* v seznam chyb a ve výstupu sestavení příkazového řádku, ale nezpůsobí selhání sestavení. | Poškozený kód je podtržen zelenou vlnovkou a označený malým zeleným polem na posuvníku. |
| Informace | `suggestion` | Porušení se zobrazí jako *zprávy* v seznam chyb, a ne vůbec ve výstupu sestavení příkazového řádku. | Poškozený kód je podtržený šedou vlnovkou a označený malým šedým polem na posuvníku. |
| Skrytý | `silent` | Uživatel není viditelný. | Uživatel není viditelný. Diagnostika se oznamuje diagnostickému modulu IDE, ale. |
| Žádné | `none` | Zcela potlačeno. | Zcela potlačeno. |
| Výchozí | `default` | Odpovídá výchozí závažnosti pravidla. Chcete-li určit výchozí hodnotu pravidla, podívejte se do okno Vlastnosti. | Odpovídá výchozí závažnosti pravidla. |

Pokud je v analyzátoru zjištěna porušení pravidla, jsou uvedena v editoru kódu (jako *vlnovku* pod problematickým kódem) a v okně Seznam chyb.

![Porušení analyzátoru v Seznam chybm okně](../code-quality/media/code-analysis-error-list.png)

Narušení analyzátoru uvedená v seznamu chyb odpovídají [Nastavení úrovně závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Porušení analyzátoru se také zobrazují v editoru kódu jako podtržení podtržení kódem, který ho uráží. Následující obrázek znázorňuje tři porušení jedné chyby (červená podchytáka), jedno upozornění (zelený squiggle) a jeden návrh &mdash; (tři šedé tečky):

![V editoru kódu v aplikaci Visual Studio](media/diagnostics-severity-colors.png)

Mnoho pravidel analyzátoru nebo *diagnostika* obsahuje jednu nebo více přidružených oprav *kódu,* které můžete použít k nápravě porušení pravidla. Opravy kódu se zobrazují v nabídce ikon žárovky spolu s dalšími typy [rychlých akcí.](../ide/quick-actions.md) Informace o těchto opravách kódu najdete v tématu [Běžné rychlé akce.](../ide/quick-actions.md)

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Konfigurace úrovní závažnosti analyzátoru

Závažnost pravidel analyzátoru nebo diagnostiky můžete nakonfigurovat v souboru [EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) nebo v [nabídce žárovky](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu).

Analyzátory je také možné nakonfigurovat tak, aby při psaní kontrolovali kód v době sestavení a v reálném čase. Rozsah živé analýzy kódu můžete nakonfigurovat tak, aby se s spouštěním řešl jenom pro aktuální dokument, všechny otevřené dokumenty nebo celé řešení. Viz [Postupy: Konfigurace rozsahu živé analýzy kódu.](./configure-live-code-analysis-scope-managed-code.md)

> [!TIP]
> Chyby a upozornění v době sestavení z analyzátorů kódu se zobrazují pouze v případě, že jsou analyzátory nainstalované jako balíček NuGet. Integrované analyzátory (například IDE0067 a IDE0068) se během sestavování nikdy nespouštěly.

## <a name="nuget-package-versus-vsix-extension"></a>Porovnání balíčku NuGet a rozšíření VSIX

Analyzátory třetích stran je možné nainstalovat pro každý projekt prostřednictvím balíčku NuGet. Některé jsou také k dispozici jako Visual Studio, v takovém případě se vztahují na jakékoli řešení, které otevřete v Visual Studio. Mezi těmito dvěma metodami instalace analyzátorů existují některé klíčové [rozdíly v chování.](../code-quality/install-roslyn-analyzers.md)

### <a name="scope"></a>Obor

Pokud analyzátory instalujete jako Visual Studio, budou platit na úrovni řešení a na všechny instance Visual Studio. Pokud analyzátory nainstalujete jako balíček NuGet, což je upřednostňovaná metoda, vztahují se pouze na projekt, ve kterém byl nainstalován balíček NuGet. V týmových prostředích jsou analyzátory nainstalované jako balíčky NuGet v oboru pro *všechny vývojáře* , kteří na daném projektu pracují.

### <a name="build-errors"></a>Chyby sestavení

Aby byla pravidla vynutila při sestavování, včetně prostřednictvím příkazového řádku nebo jako součást sestavení průběžné integrace (CI), můžete vybrat jednu z následujících možností:

- Vytvořte projekt .NET 5,0, který obsahuje analyzátory ve výchozím nastavení v sadě .NET SDK. Analýza kódu je ve výchozím nastavení povolená pro projekty, které cílí na rozhraní .NET 5.0 nebo novější. Můžete povolit analýzu kódu pro projekty, které cílí na starší verze rozhraní .NET, nastavením vlastnosti [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) na hodnotu true.

- Nainstalujte analyzátory jako balíček NuGet. V sestavě sestavení se nezobrazují upozornění a chyby analyzátoru, pokud nainstalujete analyzátory jako rozšíření.

Následující obrázek ukazuje výstup sestavení příkazového řádku z sestavení projektu, který obsahuje porušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušením pravidla](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Závažnost pravidla

Nemůžete nakonfigurovat závažnost pravidel z analyzátorů, které se nainstalovaly jako rozšíření sady Visual Studio. Pokud chcete nakonfigurovat [závažnost pravidla](../code-quality/use-roslyn-analyzers.md#configure-severity-levels), nainstalujte analyzátory jako balíček NuGet.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Instalace analyzátorů kódu v aplikaci Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Použití analyzátorů kódu v aplikaci Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Viz také

- [Nejčastější dotazy k analyzátorům](analyzers-faq.yml)
- [Zápis vlastního analyzátoru kódu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Sada .NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)