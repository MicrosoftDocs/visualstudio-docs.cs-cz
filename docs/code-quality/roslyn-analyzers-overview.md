---
title: Analýza kódu pomocí analyzátorů Roslyn
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d3fa48a7f571680cb9d26257fe4aa288aba15dbc
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352200"
---
# <a name="overview-of-source-code-analysis"></a>Přehled analýzy zdrojového kódu

Analyzátory .NET Compiler Platform (Roslyn) kontrolují kód v jazyce C# nebo Visual Basic ve stylu, kvalitě, udržovatelnosti, návrhu a dalších problémech. Tato kontrola nebo analýza se provádí během návrhu ve všech otevřených souborech.

Analyzátory lze rozdělit do následujících skupin:

- Analyzátory [stylu kódu](/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019&preserve-view=true#convention-categories) jsou součástí sady Visual Studio. ID diagnostiky nebo kód pro tyto analyzátory mají formát IDExxxx, například IDE0067. Předvolby můžete nakonfigurovat na [stránce Možnosti textového editoru](../ide/code-styles-and-code-cleanup.md) nebo v [souboru EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Počínaje rozhraním .NET 5,0 jsou analyzátory stylu kódu součástí sady .NET SDK a je možné je striktně vyhovět jako upozornění nebo chyby sestavení. Další informace najdete [tady](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Analyzátory [kvality kódu](code-analysis-warnings-for-managed-code-by-checkid.md) jsou nyní součástí sady .NET 5 SDK a jsou ve výchozím nastavení povoleny. ID diagnostiky nebo kód pro tyto analyzátory mají formát CAxxxx, například CA1822. Další informace najdete v tématu [Přehled analýzy kvality kódu .NET](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Analyzátory třetích stran je možné nainstalovat jako balíček NuGet nebo rozšíření sady Visual Studio. Analyzátory třetích stran, jako jsou [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzer](https://www.nuget.org/packages/xunit.analyzers/)a [sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

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

Narušení analyzátoru uvedená v seznamu chyb odpovídají [Nastavení úrovně závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Narušení analyzátoru se také zobrazí v editoru kódu jako vlnovky pod problematickým kódem. Následující obrázek ukazuje tři porušení &mdash; jedné chyby (červená vlnovka), jedno upozornění (zelená vlnovka) a jeden návrh (tři šedé tečky):

![Vlnovky v editoru kódu v aplikaci Visual Studio](media/diagnostics-severity-colors.png)

Mnoho pravidel analyzátoru nebo *diagnostiky*má jednu nebo více souvisejících *oprav kódu* , které můžete použít k opravě porušení pravidel. Opravy kódu se zobrazují v nabídce ikony žárovky spolu s dalšími typy [rychlých akcí](../ide/quick-actions.md). Informace o těchto opravách kódu najdete v tématu [běžné rychlé akce](../ide/quick-actions.md).

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Konfigurace úrovní závažnosti analyzátoru

Závažnost pravidel analyzátoru nebo *diagnostiky*můžete nakonfigurovat v [souboru EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) nebo v [nabídce](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)žárovky.

Analyzátory je také možné nakonfigurovat tak, aby zkontrolovaly kód v době sestavení a při psaní v reálném čase. Můžete nakonfigurovat rozsah živé analýzy kódu, který se má provést jenom pro aktuální dokument, všechny otevřené dokumenty nebo celé řešení. Viz [How to: Configure a Scope for Live Code Analysis](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Chyby při sestavování a varování z analyzátorů kódu se zobrazují pouze v případě, že analyzátory jsou nainstalovány jako balíček NuGet. Předdefinované analyzátory (například IDE0067 a IDE0068) nikdy neběží během sestavování.

## <a name="nuget-package-versus-vsix-extension"></a>Balíček NuGet versus rozšíření VSIX

Analyzátory třetích stran je možné instalovat v jednotlivých projektech pomocí balíčku NuGet. Některé jsou také k dispozici jako rozšíření sady Visual Studio. v takovém případě se vztahují na jakékoli řešení, které jste otevřeli v aplikaci Visual Studio. Existují některé rozdíly v chování při [instalaci analyzátorů](../code-quality/install-roslyn-analyzers.md)mezi těmito dvěma způsoby.

### <a name="scope"></a>Obor

Pokud nainstalujete analyzátory jako rozšíření sady Visual Studio, budou použity na úrovni řešení a na všechny instance aplikace Visual Studio. Pokud nainstalujete analyzátory jako balíček NuGet, což je upřednostňovaná metoda, vztahují se pouze na projekt, ve kterém byl balíček NuGet nainstalován. V týmových prostředích jsou analyzátory nainstalované jako balíčky NuGet v oboru pro *všechny vývojáře* , kteří na daném projektu pracují.

### <a name="build-errors"></a>Chyby sestavení

Aby byla pravidla vynutila při sestavování, včetně prostřednictvím příkazového řádku nebo jako součást sestavení průběžné integrace (CI), můžete vybrat jednu z následujících možností:

- Vytvořte projekt .NET 5,0, který obsahuje analyzátory ve výchozím nastavení v sadě .NET SDK. Analýza kódu je ve výchozím nastavení povolená pro projekty, které cílí na rozhraní .NET 5.0 nebo novější. Můžete povolit analýzu kódu pro projekty, které cílí na starší verze rozhraní .NET, nastavením vlastnosti [EnableNETAnalyzers](https://docs.microsoft.com/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) na hodnotu true.

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

- [Nejčastější dotazy k analyzátorům](analyzers-faq.md)
- [Zápis vlastního analyzátoru kódu](../extensibility/getting-started-with-roslyn-analyzers.md)
- [Sada .NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
