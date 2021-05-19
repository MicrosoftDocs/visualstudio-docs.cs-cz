---
title: Konfigurace analyzátoru
ms.date: 05/10/2021
description: Zjistěte, jak přizpůsobit pravidla analyzátoru Roslyn. Podívejte se, jak upravit závažnost analyzátoru, potlačit porušení a určit soubory jako vygenerovaný kód.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973379"
---
# <a name="overview"></a>Přehled

Každá diagnostika nebo *pravidlo* analyzátoru Roslyn má výchozí závažnost a stav potlačení, které je možné přepsat a přizpůsobit pro váš projekt. Tento článek popisuje nastavení závažnosti analyzátoru a potlačení porušení analyzátoru.

## <a name="configure-severity-levels"></a>Konfigurace úrovní závažnosti

::: moniker range=">=vs-2019"

Od verze Visual Studio 2019 verze 16.3 můžete v souboru [EditorConfig,](#set-rule-severity-in-an-editorconfig-file)v nabídce žárovky a v [](#set-rule-severity-from-the-light-bulb-menu)seznamu chyb nakonfigurovat závažnost pravidel analyzátoru nebo diagnostiku. 

::: moniker-end

::: moniker range="vs-2017"

Pokud instalujete analyzátory jako balíček NuGet, [](../code-quality/install-roslyn-analyzers.md) můžete nakonfigurovat závažnost pravidel analyzátoru neboli diagnostiky. Závažnost pravidla můžete změnit z Průzkumník řešení [nebo](#set-rule-severity-from-solution-explorer) v souboru [sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

Následující tabulka uvádí různé možnosti závažnosti:

| Závažnost (Průzkumník řešení) | Závažnost (soubor EditorConfig) | Chování při sestavení | Chování editoru |
|-|-|-|
| Chyba | `error` | Porušení se zobrazují *jako chyby* v Seznam chyb a ve výstupu sestavení příkazového řádku a způsobují selhání sestavení.| Urážející kód je podtržený červenou podtržení podtrženou podtržení a označeno malým červeným polem v posuvníku. |
| Upozornění | `warning` | Porušení se *zobrazují jako upozornění* v Seznam chyb a ve výstupu sestavení příkazového řádku, ale nezpůsobují selhání sestavení. | Urážející kód je podtržený zelenou podtrženou podtržení a označeno malým zeleným polem v posuvníku. |
| Informace | `suggestion` | Porušení se *zobrazují jako* zprávy v Seznam chyb, a ne vůbec ve výstupu sestavení příkazového řádku. | Urážející kód je podtržený šedým podtržením a označený malým šedým polem v posuvníku. |
| Skrytý | `silent` | Uživatel je nezviditelněn. | Uživatel je nezviditelněn. Diagnostika se ale hlásí diagnostického modulu integrovaného vývojového prostředí(IDE). |
| Žádná | `none` | Zcela potlačeno. | Zcela potlačeno. |
| Výchozí | `default` | Odpovídá výchozí závažnosti pravidla. Pokud chcete zjistit, jaká je výchozí hodnota pravidla, podívejte se do okno Vlastnosti. | Odpovídá výchozí závažnosti pravidla. |

Pokud analyzátor našeří pravidla, nahlásil se v editoru kódu (jako podtržení podtržení kódem, který je urážející) *a* v okně Seznam chyb kódu.

Porušení analyzátoru hlášená v seznamu chyb odpovídají [nastavení úrovně závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Porušení analyzátoru se také zobrazují v editoru kódu jako podtržení podtržení kódem, který ho uráží. Následující obrázek znázorňuje tři porušení jedné chyby (červená podchytáka), jedno upozornění (zelený squiggle) a jeden návrh &mdash; (tři šedé tečky):

![V editoru kódu v aplikaci Visual Studio](media/diagnostics-severity-colors.png)

Následující snímek obrazovky ukazuje stejná tři porušení, jako se zobrazují v Seznam chyb:

![Porušení chyby, upozornění a informací v Seznam chyb](media/diagnostics-severities-in-error-list.png)

Mnoho pravidel analyzátoru nebo *diagnostika* má jednu nebo více přidružených oprav *kódu,* které můžete použít k nápravě porušení pravidla. Opravy kódu se zobrazují v nabídce ikon žárovky spolu s dalšími typy [rychlých akcí.](../ide/quick-actions.md) Informace o těchto opravách kódu najdete v tématu [Běžné rychlé akce.](../ide/quick-actions.md)

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Závažnost "Skrytá" versus závažnost "Žádná"

`Hidden` pravidla závažnosti, která jsou ve výchozím nastavení povolená, se liší od pravidel zákazu nebo `None` závažnosti několika způsoby.

- Pokud byla pro pravidlo závažnosti zaregistrována nějaká oprava kódu `Hidden` , je tato oprava nabízena jako akce refaktoringu kódu žárovky v aplikaci Visual Studio, a to i v případě, že skrytá Diagnostika není viditelná pro uživatele. Nejedná se o případ zakázaných `None` pravidel závažnosti.
- `Hidden` pravidla závažnosti je možné hromadně nakonfigurovat pomocí položek, které [Nastaví závažnost pravidla pro více pravidel analyzátoru najednou v souboru EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` pravidla závažnosti nejde nakonfigurovat tímto způsobem. Místo toho je třeba je nakonfigurovat pomocí záznamů, které [Nastaví závažnost pravidla v souboru EditorConfig pro každé ID pravidla](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Nastavení závažnosti pravidla v souboru EditorConfig

(Visual Studio 2019 verze 16,3 a novější)

Můžete nastavit závažnost pro upozornění kompilátoru nebo pravidla analyzátoru v souboru EditorConfig pomocí následující syntaxe:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Nastavení závažnosti pravidla v souboru EditorConfig má přednost před jakoukoli závažností, která je nastavená v sadě pravidel nebo v Průzkumník řešení. Můžete [ručně](#manually-configure-rule-severity-in-an-editorconfig-file) nakonfigurovat závažnost v souboru EditorConfig nebo [automaticky](#set-rule-severity-from-the-light-bulb-menu) prostřednictvím žárovky, která se zobrazí vedle porušení.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Nastavení závažnosti pravidel pro více pravidel analyzátoru najednou v souboru EditorConfig

(Visual Studio 2019 verze 16,5 a novější)

Můžete nastavit závažnost pro specifickou kategorii pravidel analyzátoru nebo pro všechna pravidla analyzátoru s jednou položkou v souboru EditorConfig.

- Nastavte závažnost pravidla pro kategorii pravidel analyzátoru:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Nastavte závažnost pravidla pro všechna pravidla analyzátoru:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Položky, které se mají nakonfigurovat víc pravidel analyzátoru najednou, se použijí jenom na pravidla, která jsou *ve výchozím nastavení povolená*. Pravidla analyzátoru, která jsou ve výchozím nastavení označena jako zakázaná v balíčku analyzátoru, musí být povolená prostřednictvím explicitních `dotnet_diagnostic.<rule ID>.severity = <severity>` záznamů.

Pokud máte více položek, které se vztahují na ID konkrétního pravidla, je následující pořadí priorit výběru příslušné položky:

- Položka závažnosti pro jednotlivá pravidla podle ID má přednost před záznamem závažnosti pro kategorii.
- Položka závažnosti pro kategorii má přednost před záznamem závažnosti pro všechna pravidla analyzátoru.

Představte si následující příklad EditorConfig, [kde CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) má kategorii Výkon:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

V předchozím příkladu platí všechny tři položky pro CA1822. Při použití zadaných pravidel priority ale první položka závažnosti založená na ID pravidla vyhrává nad následujícími položkami. V tomto příkladu bude mít CA1822 efektivní závažnost "chyba". Všechna zbývající pravidla s kategorií Výkon budou mít závažnost "upozornění". Všechna zbývající pravidla analyzátoru, která nemají kategorii Výkon, budou mít závažnost "návrh".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Ruční konfigurace závažnosti pravidla v souboru EditorConfig

1. Pokud ještě pro svůj projekt nemáte soubor EditorConfig, [přidejte ho](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Přidejte položku pro každé pravidlo, které chcete nakonfigurovat, pod odpovídající příponu souboru. Pokud chcete například nastavit závažnost [ca1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) na pro `error` soubory jazyka C#, bude položka vypadat takto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Pro analyzátory ve stylu kódu IDE je můžete také nakonfigurovat v souboru EditorConfig pomocí jiné syntaxe, například `dotnet_style_qualification_for_field = false:suggestion` . Pokud ale nastavíte závažnost pomocí `dotnet_diagnostic` syntaxe, bude mít přednost. Další informace najdete v tématu [Jazykové konvence pro EditorConfig.](/dotnet/fundamentals/code-analysis/style-rules/language-rules)

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Nastavení závažnosti pravidla z nabídky žárovky

Visual Studio nabízí pohodlný způsob konfigurace závažnosti pravidla z nabídky žárovky [Rychlé](../ide/quick-actions.md) akce.

1. Když dojde k porušení zásad, najeďte v editoru myší na squiggle porušení a otevřete nabídku žárovky. Nebo umístěte kurzor na řádek a stiskněte **Ctrl** + **.** (období).

2. V nabídce žárovky vyberte **Konfigurovat nebo potlačit problémy** > **konfigurace \<rule ID> závažnosti**.

   ![Konfigurace závažnosti pravidla z nabídky světlé žárovky v aplikaci Visual Studio](media/configure-rule-severity.png)

3. Odtud vyberte jednu z možností závažnosti.

   ![Nakonfigurovat závažnost pravidla jako návrh](media/configure-rule-severity-suggestion.png)

   Visual Studio přidá položku do souboru EditorConfig, aby nakonfigurovala pravidlo na požadovanou úroveň, jak je uvedeno v poli Náhled.

   > [!TIP]
   > Pokud v projektu ještě nemáte soubor EditorConfig, Visual Studio ho vytvoří za vás.

### <a name="set-rule-severity-from-the-error-list-window"></a>Nastavení závažnosti pravidla z okna Seznam chyb

Visual Studio také nabízí pohodlný způsob konfigurace závažnosti pravidla z kontextové nabídky seznamu chyb.

1. Po porušení klikněte pravým tlačítkem myši na položku diagnostiky v seznamu chyb.

2. V místní nabídce vyberte **nastavit závažnost**.

   ![Konfigurace závažnosti pravidla ze seznamu chyb v aplikaci Visual Studio](media/configure-rule-severity-error-list.png)

3. Odtud vyberte jednu z možností závažnosti.

   Visual Studio přidá položku do souboru EditorConfig, aby nakonfigurovala pravidlo na požadovanou úroveň.

   > [!TIP]
   > Pokud v projektu ještě nemáte soubor EditorConfig, Visual Studio ho vytvoří za vás.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Nastavit závažnost pravidla z Průzkumník řešení

Z **Průzkumník řešení** můžete provádět většinu úprav diagnostiky analyzátoru. Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, pod uzlem **odkazy** nebo **závislosti** v **Průzkumník řešení** se zobrazí uzel **analyzátory** . Pokud rozbalíte **analyzátory** a pak rozbalíte jedno ze sestavení analyzátoru, uvidíte všechny diagnostiky v sestavení.

![Uzel analyzátorů v Průzkumník řešení](media/analyzers-expanded-in-solution-explorer.png)

V okně **vlastnosti** můžete zobrazit vlastnosti diagnostiky, včetně jeho popisu a výchozí závažnosti. Pokud chcete zobrazit vlastnosti, klikněte pravým tlačítkem na pravidlo a vyberte **Vlastnosti**, nebo vyberte pravidlo a stiskněte **Klávesu Alt** + **Enter.**

![Diagnostické vlastnosti v okno Vlastnosti](media/analyzer-diagnostic-properties.png)

Pokud chcete zobrazit online dokumentaci pro diagnostiku, klikněte pravým tlačítkem na diagnostiku a vyberte **Zobrazit nápovědu.**

Ikony vedle každé diagnostiky v **Průzkumník řešení** odpovídají ikonám, které vidíte v sadě pravidel při otevření v editoru:

- Symbol "x" v kruhu označuje [závažnost](#configure-severity-levels) **chyby.**
- Symbol "!" v trojúhelníku označuje [závažnost upozornění.](#configure-severity-levels) 
- Písmeno "i" v kruhu označuje [závažnost](#configure-severity-levels) **informací.**
- Písmeno "i" v kruhu na světle barevném pozadí označuje [závažnost](#configure-severity-levels) **Skryté.**
- šipka dolů v kruhu indikuje, že diagnostika je potlačena.

![Ikony diagnostiky v Průzkumník řešení](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Převod existujícího souboru ruleset na soubor EditorConfig

Od verze Visual Studio 2019 verze 16.5 jsou soubory sady pravidel zastaralé ve prospěch souboru EditorConfig pro konfiguraci analyzátoru pro spravovaný kód. Většina nástrojů Visual Studio nástroje pro konfiguraci závažnosti pravidla analyzátoru byla aktualizována tak, aby fungovala se soubory EditorConfig místo souborů sady pravidel. Soubory EditorConfig umožňují konfigurovat závažnost pravidla analyzátoru i možnosti analyzátoru, včetně Visual Studio možností stylu kódu IDE. Důrazně doporučujeme převést existující soubor sady pravidel na soubor EditorConfig. Doporučujeme také uložit soubor EditorConfig v kořenovém adresáři vašeho repo nebo ve složce řešení. Pomocí kořenového adresáře vašeho adresáře nebo složky řešení se ujistěte, že se nastavení závažnosti z tohoto souboru automaticky aplikují na celé repo nebo řešení.

Existující soubor sady pravidel můžete převést na soubor EditorConfig několika způsoby:

- Z Editoru sady pravidel v Visual Studio (vyžaduje Visual Studio 2019 16.5 nebo novější). Pokud váš projekt už používá určitý soubor RuleSet jako svůj `CodeAnalysisRuleSet` , můžete ho převést na ekvivalentní soubor EditorConfig z editoru RuleSet v rámci sady Visual Studio.

    1. Dvakrát klikněte na soubor RuleSet v Průzkumník řešení.

       Soubor RuleSet by měl být otevřen v editoru RuleSet. V horní části editoru RuleSet by se měl zobrazit **informační panel** umožňující kliknutí.

       ![Převod RuleSet na soubor EditorConfig v editoru RuleSet](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Vyberte odkaz na **informační panel** .

       Mělo by se otevřít dialogové okno **Uložit jako** , ve kterém můžete vybrat adresář, ve kterém chcete vytvořit soubor EditorConfig.

    3. Vyberte tlačítko **Uložit** pro vygenerování souboru EditorConfig.

       Vygenerovaný EditorConfig by měl být otevřen v editoru. Kromě toho se vlastnost MSBuild `CodeAnalysisRuleSet` aktualizuje v souboru projektu tak, že už neodkazuje na původní soubor RuleSet.

- Z příkazového řádku:

    1. Nainstalujte balíček NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Provede se `RulesetToEditorconfigConverter.exe` z nainstalovaného balíčku s cestami k souboru ruleset a souborem EditorConfig jako argumenty příkazového řádku.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Tady je příklad souboru ruleset, který se má převést:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Zde je převedený soubor EditorConfig:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Nastavit závažnost pravidla z Průzkumník řešení

1. V Průzkumník řešení rozbalte položku   >  **analyzátory** odkazů (nebo   >  **analyzátory** závislostí pro projekty .NET Core).

2. Rozbalte sestavení, které obsahuje pravidlo, pro které chcete nastavit závažnost.

::: moniker range=">=vs-2019"
3. Klikněte pravým tlačítkem na pravidlo a vyberte **nastavit závažnost**. V místní nabídce vyberte jednu z možností závažnosti.

   Visual Studio přidá položku do souboru EditorConfig, aby nakonfigurovala pravidlo na požadovanou úroveň. Pokud váš projekt používá soubor sady pravidel místo souboru EditorConfig, položka závažnosti se přidá do souboru sady pravidel.

   > [!TIP]
   > Pokud v projektu ještě nemáte soubor EditorConfig nebo soubor sady pravidel, Visual Studio vytvoří nový soubor EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Klikněte pravým tlačítkem na pravidlo a vyberte **Nastavit závažnost sady pravidel.** V místní nabídce zvolte jednu z možností závažnosti.

   Závažnost pravidla se uloží do aktivního souboru sady pravidel.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Nastavení závažnosti pravidla v souboru sady pravidel

![Soubor sady pravidel v Průzkumník řešení](media/ruleset-in-solution-explorer.png)

1. Otevřete aktivní soubor sady pravidel jedním z následujících způsobů:

- V **Průzkumník řešení** na soubor poklikejte, klikněte pravým tlačítkem na **uzel Analyzátory** odkazů a vyberte Otevřít sadu  >   **aktivních pravidel.**
- Na **Code Analysis** vlastností projektu vyberte **Otevřít.**

  Pokud sadu pravidel upravujete poprvé, vytvoří Visual Studio výchozí soubor sady pravidel, nazý se *\<projectname> .ruleset* a přidá ji do projektu. Tato vlastní sada pravidel se také stane aktivním souborem pravidel pro váš projekt.

   > [!NOTE]
   > Projekty .NET Core a .NET Standard nepodporují příkazy nabídky pro sady pravidel v **Průzkumník řešení**, například **Otevřít aktivní sadu pravidel.** Pokud chcete zadat jiné než výchozí sady pravidel pro projekt .NET Core nebo .NET Standard, přidejte do souboru projektu ručně vlastnost [ **CodeAnalysisRuleSet.**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) Pravidla v sadě pravidel můžete nakonfigurovat i v uživatelském rozhraní editoru Visual Studio sady pravidel.

1. Přejděte k pravidlu tak, že rozbalíte jeho obsahující sestavení.

1. Ve **sloupci** Akce vyberte hodnotu, která se má otevřít, rozevírací seznam a zvolte požadovanou závažnost ze seznamu.

   ![Soubor sady pravidel otevřený v editoru](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Konfigurace vygenerovaného kódu

Analyzátory běží na všech zdrojových souborech v projektu a hlásí na nich porušení. Tato porušení nejsou ale užitečná u generovaných souborů kódu, jako jsou soubory kódu vygenerované návrhářem, dočasné zdrojové soubory vygenerované systémem sestavení atd. Uživatelé nemůžou ručně upravovat tyto soubory a/nebo se netýkají narušení oprav v těchto druzích souborů generovaných nástrojem.

Ve výchozím nastavení ovladač analyzátoru, který provádí analyzátory, zpracovává soubory s určitým názvem, příponou souboru nebo automaticky generovaným hlavičkou souboru jako soubory generovaného kódu. Například název souboru končícího `.designer.cs` nebo `.generated.cs` se považuje za generovaný kód. Tyto heuristiky ale nemusí být schopné identifikovat všechny vlastní soubory generovaného kódu ve zdrojovém kódu uživatele.

Od sady Visual Studio 2019 16,5 mohou koncoví uživatelé konfigurovat konkrétní soubory nebo složky, které mají být zpracovány jako vygenerovaný kód v [souboru EditorConfig](https://editorconfig.org/). Chcete-li přidat takovou konfiguraci, postupujte podle následujících kroků:

1. Pokud ještě nemáte soubor EditorConfig pro váš projekt, [přidejte ho](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Přidejte `generated_code = true | false` položku pro konkrétní soubory a složky. Například pro považovat všechny soubory, jejichž název končí `.MyGenerated.cs` jako generovaný kód, bude položka následující:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Potlačit porušení

Porušení pravidel můžete potlačit pomocí různých metod. Další informace naleznete v tématu [potlačení narušení analýzy kódu](../code-quality/in-source-suppression-overview.md).

## <a name="command-line-usage"></a>Použití příkazového řádku

Při sestavování projektu na příkazovém řádku se porušení pravidla zobrazí ve výstupu sestavení, pokud jsou splněny následující podmínky:

- Analyzátory jsou nainstalovány se sadou .NET SDK nebo jako balíček NuGet, nikoli jako rozšíření VSIX.

  Pro analyzátory nainstalované pomocí .NET SDK možná budete muset [Povolit analyzátory](../code-quality/install-net-analyzers.md). Pro styly kódu můžete také [vynutili styly kódu při sestavení](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) nastavením vlastnosti MSBuild.

- V kódu projektu je porušeno jedno nebo více pravidel.

- [Závažnost](#configure-severity-levels) narušeného pravidla je nastavena na možnost **Upozornění**, v takovém případě porušení nezpůsobí selhání sestavení nebo **Chyba**. v takovém případě porušení způsobí selhání sestavení.

Podrobnosti výstupu sestavení neovlivňují, zda jsou zobrazena porušení pravidel. I s **tichou** podrobností se ve výstupu sestavení zobrazí porušení pravidel.

> [!TIP]
> Pokud jste zvyklí spouštět starší verze analýzy z příkazového  řádku,FxCopCmd.exenebo prostřednictvím nástroje msbuild s příznakem **RunCodeAnalysis,** tady je postup použití analyzátorů kódu.

Pokud chcete při sestavování projektu pomocí nástroje msbuild zobrazit porušení analyzátoru na příkazovém řádku, spusťte příkaz, jako je tento:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Následující obrázek ukazuje výstup sestavení příkazového řádku ze sestavení projektu, který obsahuje porušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušením pravidel](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Závislé projekty

Pokud v projektu .NET Core přidáte odkaz na projekt, který obsahuje analyzátory NuGet, tyto analyzátory se automaticky přidávají také do závislého projektu. Pokud chcete toto chování zakázat, například pokud je závislý projekt projektem testování částí, označte balíček NuGet v *souboru .csproj* nebo *.vbproj* odkazovaného projektu nastavením atributu **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Odeslání chyby analyzátoru kódu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Použití sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Potlačení upozornění analýzy kódu](../code-quality/in-source-suppression-overview.md)
- [Možnosti konfigurace pro analýzu kódu (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
