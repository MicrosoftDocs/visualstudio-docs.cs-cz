---
title: Závažnost a potlačení pravidel analyzátoru
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431407"
---
# <a name="use-code-analyzers"></a>Použití analyzátorů kódu

Analyzátory kódu platformy kompilátoru .NET ("Roslyn") analyzují kód jazyka C# nebo Visual Basic při psaní. Každá *diagnostika* nebo pravidlo má výchozí stav závažnosti a potlačení, který lze přepsat pro váš projekt. Tento článek popisuje nastavení závažnosti pravidel, použití sady pravidel a potlačení porušení.

## <a name="analyzers-in-solution-explorer"></a>Analyzátory v Průzkumníku řešení

Většinu vlastního nastavení diagnostiky analyzátoru můžete provést z **Průzkumníka řešení**. Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, uzel **analyzátorů** se zobrazí pod uzlemi **Reference** **nebo Závislosti** v **Průzkumníku řešení**. Pokud rozbalíte **analyzátory**a potom rozbalíte jednu ze sestav analyzátoru, zobrazí se v sestavení všechny diagnostiky.

![Uzel analyzátorů v Průzkumníku řešení](media/analyzers-expanded-in-solution-explorer.png)

Vlastnosti diagnostiky, včetně jejího popisu a výchozí závažnosti, můžete zobrazit v okně **Vlastnosti.** Chcete-li vlastnosti zobrazit, klepněte pravým tlačítkem myši na pravidlo a vyberte příkaz **Vlastnosti**nebo vyberte pravidlo a stiskněte **klávesu Alt**+**Enter**.

![Diagnostické vlastnosti v okně Vlastnosti](media/analyzer-diagnostic-properties.png)

Chcete-li zobrazit online dokumentaci k diagnostice, klepněte pravým tlačítkem myši na diagnostiku a vyberte příkaz **Zobrazit nápovědu**.

Ikony vedle každé diagnostiky v **Průzkumníku řešení** odpovídají ikonám, které se zobrazí v sadě pravidel při otevření v editoru:

- "x" v kruhu označuje [závažnost](#rule-severity) **chyby**
- "!" v trojúhelníku označuje [závažnost](#rule-severity) **varování**
- "i" v kruhu označuje [závažnost](#rule-severity) **Info**
- "i" v kruhu na světlém pozadí označuje [závažnost](#rule-severity) **skrytého**
- šipka směřující dolů v kruhu označuje, že diagnostika je potlačena

![Ikony diagnostiky v Průzkumníku řešení](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Závažnost pravidla

::: moniker range=">=vs-2019"

Můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*, pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet. Počínaje visual studio 2019 verze 16.3, můžete nakonfigurovat závažnost pravidla [v souboru EditorConfig](#set-rule-severity-in-an-editorconfig-file). Závažnost pravidla můžete také změnit [z Průzkumníka řešení](#set-rule-severity-from-solution-explorer) nebo [v souboru sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*, pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet. Závažnost pravidla můžete změnit [z Průzkumníka řešení](#set-rule-severity-from-solution-explorer) nebo v [souboru sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

V následující tabulce jsou uvedeny různé možnosti závažnosti:

| Závažnost (Průzkumník řešení) | Závažnost (soubor EditorConfig) | Chování v době sestavení | Chování editoru |
|-|-|-|
| Chyba | `error` | Porušení se zobrazí jako *chyby* v seznamu chyb a ve výstupu sestavení příkazového řádku a způsobit sestavení nezdaří.| Problematický kód je podtržen červenou vlnovkou a označen malým červeným rámečkem ve posuvníku. |
| Upozornění | `warning` | Porušení se zobrazí jako *upozornění* v seznamu chyb a ve výstupu sestavení příkazového řádku, ale nezpůsobí selhání sestavení. | Problematický kód je podtržen zeleným vlnovkou a označen malým zeleným rámečkem ve posuvníku. |
| Informace | `suggestion` | Porušení se zobrazí jako *zprávy* v seznamu chyb a vůbec ve výstupu sestavení příkazového řádku. | Problematický kód je podtržen šedou vlnovkou a označen malým šedým rámečkem ve posuvníku. |
| Skrytý | `silent` | Neviditelné pro uživatele. | Neviditelné pro uživatele. Diagnostika je však hlášena diagnostickému modulu IDE. |
| Žádný | `none` | Úplně potlačeno. | Úplně potlačeno. |
| Výchozí | `default` | Odpovídá výchozí závažnosti pravidla. Chcete-li zjistit, jaká je výchozí hodnota pravidla, podívejte se do okna Vlastnosti. | Odpovídá výchozí závažnosti pravidla. |

Následující snímek obrazovky editoru kódu ukazuje tři různá porušení s různými závažnostmi. Všimněte si barvy vlnovky a malého barevného čtverce ve posuvníku vpravo.

![Chyba, upozornění a narušení informací v editoru kódu](media/diagnostics-severity-colors.png)

Následující snímek obrazovky ukazuje stejné tři porušení, která se zobrazují v seznamu chyb:

![Chyba, upozornění a porušení informací v seznamu chyb](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Nastavení závažnosti pravidla v souboru EditorConfig

(Visual Studio 2019 verze 16.3 a novější)

Závažnost upozornění kompilátoru nebo pravidel analyzátoru můžete nastavit v souboru EditorConfig pomocí následující syntaxe:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Nastavení závažnosti pravidla v souboru EditorConfig má přednost před jakoukoli závažností nastavenou v sadě pravidel nebo v Průzkumníku řešení. Závažnost můžete [nakonfigurovat ručně](#manually-configure-rule-severity) v souboru EditorConfig nebo [automaticky](#automatically-configure-rule-severity) prostřednictvím žárovky, která se zobrazí vedle porušení.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Nastavení závažnosti pravidel více pravidel analyzátoru najednou v souboru EditorConfig

(Visual Studio 2019 verze 16.5 a novější)

Závažnost můžete nastavit pro určitou kategorii pravidel analyzátoru nebo pro všechna pravidla analyzátoru pomocí jedné položky v souboru EditorConfig.

- Nastavte závažnost pravidla pro kategorii pravidel analyzátoru:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Nastavte závažnost pravidla pro všechna pravidla analyzátoru:

`dotnet_analyzer_diagnostic.severity = <severity>`

Pokud máte více položek, které se vztahují na konkrétní ID pravidla, je pořadí priorit pro výběr příslušné položky:

- Položka závažnosti pro jednotlivé pravidlo podle ID má přednost před položkou závažnosti pro kategorii.
- Položka závažnosti pro kategorii má přednost před položkou závažnosti pro všechna pravidla analyzátoru.

Vezměme si následující EditorConfig příklad, kde [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) má kategorii "Výkon":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

V předchozím příkladu jsou všechny tři položky použitelné pro CA1822. Při použití zadaných pravidel priority však první položka závažnosti založené na ID pravidla vyhrává v následujících položkách. V tomto příkladu ca1822 bude mít efektivní závažnost "chyba". Všechna zbývající pravidla s kategorií "Výkon" budou mít závažnost "upozornění". Všechna zbývající pravidla analyzátoru, která nemají kategorii "Výkon", budou mít "návrh" závažnosti.

#### <a name="manually-configure-rule-severity"></a>Ruční konfigurace závažnosti pravidla

1. Pokud ještě nemáte soubor EditorConfig pro váš projekt, [přidejte jeden](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Přidejte položku pro každé pravidlo, které chcete nakonfigurovat pod odpovídající příponou souboru. Chcete-li například nastavit závažnost pro [CA1822](ca1822.md) na `error` soubory C#, položka vypadá takto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Pro analyzátory ve stylu kódu IDE je můžete také nakonfigurovat v souboru `dotnet_style_qualification_for_field = false:suggestion`EditorConfig pomocí jiné syntaxe, například . Pokud však nastavíte závažnost `dotnet_diagnostic` pomocí syntaxe, bude mít přednost. Další informace naleznete [v tématu Language conventions for EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Převedení existujícího souboru sady pravidel na soubor EditorConfig

Počínaje Visual Studio 2019 verze 16.5, soubory sady pravidel jsou zastaralé ve prospěch souboru EditorConfig pro konfiguraci analyzátoru pro spravovaný kód. Většina nástrojů sady Visual Studio pro konfiguraci závažnosti pravidel analyzátoru byla aktualizována tak, aby fungovala na souborech EditorConfig namísto souborů sady pravidel. EditorConfig soubory umožňují konfigurovat rozdělení pravidel analyzátoru a možnosti analyzátoru, včetně možností stylu stylu ide aplikace Visual Studio. Důrazně doporučujeme převést existující soubor sady pravidel na soubor EditorConfig. Doporučujeme také uložit soubor EditorConfig v kořenovém adresáři ukládání do pou nebo do složky řešení. Pomocí kořenového adresáře složky pro repo nebo řešení se ujistěte, že nastavení závažnosti z tohoto souboru jsou automaticky použita na celé repo nebo řešení.

Existuje několik způsobů, jak převést existující soubor sady pravidel na soubor EditorConfig:

- Z editoru sad pravidel v sadě Visual Studio (vyžaduje Visual Studio 2019 16.5 nebo novější). Pokud projekt již používá jako soubor `CodeAnalysisRuleSet`konkrétní sady pravidel konkrétní soubor pravidel , můžete jej převést na ekvivalentní soubor EditorConfig z Editoru sady pravidel v sadě Visual Studio.

    1. Poklepejte na soubor sady pravidel v Průzkumníku řešení.

       Soubor sady pravidel by se měl otevřít v Editoru sad pravidel. V horní části editoru sad pravidel byste měli vidět **informační panel,** na který lze kliknout.

       ![Převést sadu pravidel na soubor EditorConfig v Editoru sad pravidel](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Klikněte na** odkaz na informační panel.

       To by mělo otevřít dialogové okno **Uložit jako,** které umožňuje vybrat adresář, ve kterém chcete vygenerovat soubor EditorConfig.

    3. **Klepnutím na** tlačítko **Uložit** vygenerujete soubor EditorConfig.

       Vygenerovaný EditorConfig by se měl otevřít v editoru. Navíc MSBuild vlastnost `CodeAnalysisRuleSet` získá aktualizovánv souboru projektu tak, aby již odkazuje na původní soubor sady pravidel.

- Z příkazového řádku:

    1. Nainstalujte balíček NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Spouštět `RulesetToEditorconfigConverter.exe` z nainstalovaného balíčku, s cestami k souboru sady pravidel a EditorConfig soubor jako argumenty příkazového řádku.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Zde je ukázkový soubor sady pravidel, který chcete převést:

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

Zde je převeden EditorConfig soubor:

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

#### <a name="automatically-configure-rule-severity"></a>Automatická konfigurace závažnosti pravidla

##### <a name="configure-from-light-bulb-menu"></a>Konfigurace z nabídky žárovky

Visual Studio poskytuje pohodlný způsob konfigurace závažnosti pravidla z nabídky rychlé [akce](../ide/quick-actions.md) žárovky.

1. Po porušení dojde, najeďte na porušení klikyháky v editoru a otevřete nabídku žárovky. Nebo položte kurzor na řádek a stiskněte **klávesu Ctrl**+**.** (tečka).

2. V nabídce Žárovka vyberte **Konfigurovat nebo potlačit problémy** > **Konfigurovat \<ID pravidla> závažnosti**.

   ![Konfigurace závažnosti pravidla z nabídky žárovky v sadě Visual Studio](media/configure-rule-severity.png)

3. Odtud vyberte jednu z možností závažnosti.

   ![Konfigurace závažnosti pravidla jako návrhu](media/configure-rule-severity-suggestion.png)

   Visual Studio přidá položku do souboru EditorConfig a nakonfiguruje pravidlo na požadovanou úroveň, jak je znázorněno v poli náhledu.

   > [!TIP]
   > Pokud ještě nemáte editorconfig soubor v projektu, Visual Studio vytvoří jeden pro vás.

##### <a name="configure-from-error-list"></a>Konfigurovat ze seznamu chyb

Visual Studio také poskytuje pohodlný způsob konfigurace závažnosti pravidla z kontextové nabídky seznamu chyb.

1. Po porušení dojde, klikněte pravým tlačítkem myši na diagnostickou položku v seznamu chyb.

2. V místní nabídce vyberte **Nastavit závažnost**.

   ![Konfigurace závažnosti pravidla ze seznamu chyb v sadě Visual Studio](media/configure-rule-severity-error-list.png)

3. Odtud vyberte jednu z možností závažnosti.

   Visual Studio přidá položku do souboru EditorConfig a nakonfiguruje pravidlo na požadovanou úroveň.

   > [!TIP]
   > Pokud ještě nemáte editorconfig soubor v projektu, Visual Studio vytvoří jeden pro vás.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Nastavení závažnosti pravidla z Průzkumníka řešení

1. V Průzkumníku řešení **rozbalte reference** > **analyzátory** (nebo**analyzátory** **závislostí** > pro projekty .NET Core).

2. Rozbalte sestavení obsahující pravidlo, pro které chcete nastavit závažnost.

::: moniker range=">=vs-2019"
3. Klepněte pravým tlačítkem myši na pravidlo a vyberte **nastavit závažnost**. V místní nabídce vyberte jednu z možností závažnosti.

   Visual Studio přidá položku do souboru EditorConfig a nakonfiguruje pravidlo na požadovanou úroveň. Pokud projekt používá soubor sady pravidel namísto souboru EditorConfig, položka závažnosti se přidá do souboru sady pravidel.

   > [!TIP]
   > Pokud ještě nemáte soubor EditorConfig nebo soubor pravidel v projektu, Visual Studio vytvoří nový editorconfig soubor pro vás.
::: moniker-end

::: moniker range="vs-2017"
3. Klepněte pravým tlačítkem myši na pravidlo a vyberte **nastavit závažnost sady pravidel**. V místní nabídce vyberte jednu z možností závažnosti.

   Závažnost pravidla je uložena v aktivním souboru sady pravidel.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Nastavení závažnosti pravidla v souboru sady pravidel

![Soubor sady pravidel v Průzkumníku řešení](media/ruleset-in-solution-explorer.png)

1. Otevřete aktivní soubor sady pravidel poklepáním v **Průzkumníku řešení**, vyberte **otevřít aktivní sadu pravidel** v nabídce po kliknutí pravým tlačítkem myši na uzlu Reference**analyzátory** **References** > nebo výběrem **možnosti Otevřít** na stránce **vlastností Analýza kódu** pro projekt.

   Pokud upravujete sadu pravidel poprvé, visual studio vytvoří kopii výchozího souboru sady pravidel, pojmenuje * \<název projektu>.ruleset*a přidá ji do projektu. Tato vlastní sada pravidel se také stane aktivní sadou pravidel pro váš projekt.

   > [!NOTE]
   > Projekty .NET Core a .NET Standard nepodporují příkazy nabídky pro sady pravidel v **Průzkumníku řešení**, například **Otevřít aktivní sadu pravidel**. Chcete-li zadat nevýchozí sadu pravidel pro projekt .NET Core nebo .NET Standard, ručně [přidejte vlastnost **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) do souboru projektu. Pravidla v rámci sady pravidel v editoru sady pravidel sady visual ateliu stále můžete nakonfigurovat.

1. Přejděte k pravidlu rozšířením jeho obsahující ho sestavení.

1. Ve sloupci **Akce** vyberte hodnotu, kterou chcete otevřít rozevíracím seznamu, a vyberte požadovanou závažnost ze seznamu.

   ![Soubor sady pravidel otevřený v editoru](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Potlačit porušení

Porušení pravidel lze potlačit několika způsoby:

::: moniker range=">=vs-2019"

- V **souboru EditorConfig**

  Nastavte závažnost na `none`, například `dotnet_diagnostic.CA1822.severity = none`.

- Z nabídky **Analyzovat**

  Vyberte **Analyzovat** > **sestavení a potlačit aktivní problémy** na řádku nabídek, abyste potlačili všechna aktuální porušení. To se někdy označuje jako "baselining".

::: moniker-end

::: moniker range="vs-2017"

- Z nabídky **Analyzovat**

  Vyberte **Analyzovat** > **spustit analýzu kódu a potlačit aktivní problémy** na řádku nabídek, abyste potlačili všechna aktuální porušení. To se někdy označuje jako "baselining".

::: moniker-end

- Z **Průzkumníka řešení**

  Nastavte závažnost pravidla na **žádné**.

- Z **editoru sady pravidel**

  Odškrtnete políčko vedle jeho názvu nebo nastavte **akci** na **žádnou**.

- Z **editoru kódu**

  Umístěte kurzor do řádku kódu s porušením a stisknutím **klávesy Ctrl**+**Period (.)** otevřete nabídku **Rychlé akce.** Vyberte **příkaz Potlačit caxxxx** > **ve zdroji/v souboru potlačení**.

  ![Potlačit diagnostiku z nabídky rychlých akcí](media/suppress-diagnostic-from-editor.png)

- Ze **seznamu chyb**

  Vyberte pravidla, která chcete potlačit, a potom klepněte pravým tlačítkem myši a vyberte **příkaz Potlačit** > **ve zdroji/v souboru potlačení**.

  - Pokud potlačíte **ve zdroji**, otevře se dialogové okno **Změny náhledu** a zobrazí náhled [příkazu c# #pragma upozornění](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) nebo směrnice upozornění [#Disable](/dotnet/visual-basic/language-reference/directives/directives) jazyka Visual Basic, která je přidána do zdrojového kódu.

    ![Náhled přidání upozornění #pragma v souboru kódu](media/pragma-warning-preview.png)

  - Pokud vyberete **V souboru potlačení**, otevře se <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> dialogové okno Náhled **změn** a zobrazí se náhled atributu, který je přidán do souboru globálních potlačení.

    ![Náhled přidání atributu SuppressMessage do souboru potlačení](media/preview-changes-in-suppression-file.png)

  V dialogovém **okně Náhled změn** vyberte **Použít**.

  > [!NOTE]
  > Pokud v **Průzkumníku řešení**nevidíte možnost **Potlačit** nabídku , porušení pravděpodobně pochází z sestavení a ne z živé analýzy. **Seznam chyb** zobrazuje diagnostiku nebo porušení pravidel z analýzy živého kódu i sestavení. Vzhledem k tomu, že diagnostika sestavení může být zastaralá, například pokud jste upravili kód k opravě porušení, ale nejste znovu sestaveni, nelze tuto diagnostiku potlačit ze **seznamu chyb**. Diagnostika z živé analýzy nebo technologie IntelliSense je vždy aktuální s aktuálními zdroji a může být z **seznamu chyb**potlačena . Chcete-li z výběru vyloučit diagnostiku *sestavení,* přepněte zdrojový filtr **Seznamu chyb** z **položky Build + IntelliSense** na **pouze položku IntelliSense**. Potom vyberte diagnostiku, kterou chcete potlačit, a postupujte podle výše popsaného postupu.
  >
  > ![Zdrojový filtr Seznamu chyb v sadě Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Využití příkazového řádku

Při vytváření projektu na příkazovém řádku se porušení pravidel zobrazí ve výstupu sestavení, pokud jsou splněny následující podmínky:

- Analyzátory jsou nainstalovány jako balíček NuGet a ne jako rozšíření VSIX.

- V kódu projektu je porušeno jedno nebo více pravidel.

- [Závažnost](#rule-severity) porušeného pravidla je nastavena buď na **upozornění**, v takovém případě porušení nezpůsobí selhání sestavení nebo **chybu**, v takovém případě porušení způsobit selhání sestavení.

Podrobnost výstupu sestavení nemá vliv na to, zda jsou zobrazena porušení pravidel. I při **tiché** podrobnosti porušení pravidel se objeví ve výstupu sestavení.

> [!TIP]
> Pokud jste zvyklí na spuštění starší analýzy z příkazového řádku, buď s *FxCopCmd.exe* nebo prostřednictvím msbuild s **RunCodeAnalysis** příznak, zde je návod, jak to udělat s analyzátory kódu.

Chcete-li zobrazit porušení analyzátoru na příkazovém řádku při vytváření projektu pomocí msbuild, spusťte příkaz, jako je tento:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Následující obrázek znázorňuje výstup sestavení příkazového řádku z vytváření projektu, který obsahuje porušení pravidel analyzátoru:

![Výstup MSBuild s porušením pravidel](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Závislé projekty

V projektu .NET Core pokud přidáte odkaz na projekt, který má analyzátory NuGet, tyto analyzátory jsou automaticky přidány do závislého projektu příliš. Chcete-li zakázat toto chování, například pokud závislý projekt je projekt testování částí, označte balíček NuGet jako soukromý v souboru *.csproj* nebo *.vbproj* odkazovaného projektu nastavením atributu **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v sadě Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Odeslat chybu analyzátoru kódu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Použití sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Potlačit upozornění na analýzu kódu](../code-quality/in-source-suppression-overview.md)
