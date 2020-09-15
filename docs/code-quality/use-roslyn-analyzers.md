---
title: Konfigurace analyzátoru
ms.date: 09/02/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6a950a005a4669e74722742b23527a9e85ab5f02
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560746"
---
# <a name="overview"></a>Přehled

Každé *diagnostice* nebo pravidlo Roslyn Analyzer má výchozí závažnost a stav potlačení, který lze přepsat a přizpůsobit pro váš projekt. Tento článek popisuje nastavení závažnosti analyzátoru a potlačení narušení analyzátoru.

## <a name="configure-severity-levels"></a>Konfigurace úrovní závažnosti

::: moniker range=">=vs-2019"

Počínaje verzí Visual Studio 2019 verze 16,3 můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*, v [souboru EditorConfig](#set-rule-severity-in-an-editorconfig-file), v [nabídce žárovky](#set-rule-severity-from-the-light-bulb-menu)a v seznamu chyb.

::: moniker-end

::: moniker range="vs-2017"

Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*. Závažnost pravidla můžete změnit [z Průzkumník řešení](#set-rule-severity-from-solution-explorer) nebo [v souboru sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

V následující tabulce jsou uvedeny různé možnosti závažnosti:

| Závažnost (Průzkumník řešení) | Závažnost (soubor EditorConfig) | Chování při sestavení | Chování editoru |
|-|-|-|
| Chyba | `error` | Porušení se zobrazují jako *chyby* v seznam chyb a ve výstupu sestavení příkazového řádku a způsobují selhání sestavení.| Poškozený kód je podtržen červenou vlnovkou a označený malým červeným polem na posuvníku. |
| Upozornění | `warning` | Porušení se zobrazí jako *Upozornění* v seznam chyb a ve výstupu sestavení příkazového řádku, ale nezpůsobí selhání sestavení. | Poškozený kód je podtržen zelenou vlnovkou a označený malým zeleným polem na posuvníku. |
| Informace | `suggestion` | Porušení se zobrazí jako *zprávy* v seznam chyb, a ne vůbec ve výstupu sestavení příkazového řádku. | Poškozený kód je podtržený šedou vlnovkou a označený malým šedým polem na posuvníku. |
| Skrytý | `silent` | Uživatel není viditelný. | Uživatel není viditelný. Diagnostika se oznamuje diagnostickému modulu IDE, ale. |
| Žádné | `none` | Zcela potlačeno. | Zcela potlačeno. |
| Výchozí | `default` | Odpovídá výchozí závažnosti pravidla. Chcete-li určit výchozí hodnotu pravidla, podívejte se do okno Vlastnosti. | Odpovídá výchozí závažnosti pravidla. |

Pokud je v analyzátoru zjištěna porušení pravidla, jsou uvedena v editoru kódu (jako *vlnovku* pod problematickým kódem) a v okně Seznam chyb.

Narušení analyzátoru uvedená v seznamu chyb odpovídají [Nastavení úrovně závažnosti](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) pravidla. Narušení analyzátoru se také zobrazí v editoru kódu jako vlnovky pod problematickým kódem. Následující obrázek ukazuje tři porušení &mdash; jedné chyby (červená vlnovka), jedno upozornění (zelená vlnovka) a jeden návrh (tři šedé tečky):

![Vlnovky v editoru kódu v aplikaci Visual Studio](media/diagnostics-severity-colors.png)

Následující snímek obrazovky ukazuje stejná tři porušení zásad, která se zobrazují v Seznam chyb:

![Došlo k chybě, varování a porušení informací v Seznam chyb](media/diagnostics-severities-in-error-list.png)

Mnoho pravidel analyzátoru nebo *diagnostiky*má jednu nebo více souvisejících *oprav kódu* , které můžete použít k opravě porušení pravidel. Opravy kódu se zobrazují v nabídce ikony žárovky spolu s dalšími typy [rychlých akcí](../ide/quick-actions.md). Informace o těchto opravách kódu najdete v tématu [běžné rychlé akce](../ide/quick-actions.md).

![Porušení analyzátoru a oprava kódu rychlé akce](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Závažnost "Hidden" versus závažnost "none"

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

- Položka závažnosti pro individuální pravidlo podle ID má přednost před položkou závažnosti pro kategorii.
- Položka závažnosti pro kategorii má přednost před položkou závažnosti pro všechna pravidla analyzátoru.

Vezměte v úvahu následující příklad EditorConfig, kde [CA1822](./ca1822.md) má kategorii Performance:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

V předchozím příkladu jsou všechny tři položky použitelné pro CA1822. Když ale použijete zadaná pravidla priority, první položka závažnosti na základě ID pravidla vychází z dalších položek. V tomto příkladu bude mít CA1822 efektivní závažnost "Error". Všechna zbývající pravidla s kategorií Performance budou mít závažnost "Warning". Všechna zbývající pravidla analyzátoru, která nemají kategorii výkon, budou mít závažnost "návrh".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Ruční konfigurace závažnosti pravidla v souboru EditorConfig

1. Pokud ještě nemáte soubor EditorConfig pro váš projekt, [přidejte ho](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Přidejte položku pro každé pravidlo, které chcete konfigurovat v odpovídající příponě souboru. Například pro nastavení závažnosti pro [CA1822](ca1822.md) pro `error` soubory v jazyce C# vypadá položka takto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Analyzátory ve stylu kódu IDE lze také nakonfigurovat v souboru EditorConfig pomocí jiné syntaxe, například `dotnet_style_qualification_for_field = false:suggestion` . Nicméně pokud nastavíte závažnost pomocí `dotnet_diagnostic` syntaxe, má přednost. Další informace najdete v tématu [jazykové konvence pro EditorConfig](../ide/editorconfig-language-conventions.md).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Nastavení závažnosti pravidla z nabídky žárovky

Visual Studio nabízí pohodlný způsob konfigurace závažnosti pravidla z nabídky návrhy [rychlých akcí](../ide/quick-actions.md) .

1. Jakmile dojde k porušení, najeďte myší nad vlnovkou porušení v editoru a otevřete nabídku žárovky. Nebo umístěte kurzor na řádek a stiskněte klávesu **CTRL** + **.** (tečka).

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

Z **Průzkumník řešení**můžete provádět většinu úprav diagnostiky analyzátoru. Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, pod uzlem **odkazy** nebo **závislosti** v **Průzkumník řešení**se zobrazí uzel **analyzátory** . Pokud rozbalíte **analyzátory**a pak rozbalíte jedno ze sestavení analyzátoru, uvidíte všechny diagnostiky v sestavení.

![Uzel analyzátorů v Průzkumník řešení](media/analyzers-expanded-in-solution-explorer.png)

V okně **vlastnosti** můžete zobrazit vlastnosti diagnostiky, včetně jeho popisu a výchozí závažnosti. Chcete-li zobrazit vlastnosti, klikněte pravým tlačítkem na pravidlo a vyberte **vlastnosti**, nebo vyberte pravidlo a stiskněte klávesu **ALT** + **ENTER**.

![Diagnostické vlastnosti v okno Vlastnosti](media/analyzer-diagnostic-properties.png)

Pokud chcete zobrazit online dokumentaci pro diagnostiku, klikněte pravým tlačítkem na diagnostiku a vyberte **Zobrazit nápovědu**.

Ikony vedle každé diagnostiky v **Průzkumník řešení** odpovídají ikonám, které vidíte v sadě pravidel při jejich otevírání v editoru:

- znak "x" v kruhu indikuje [závažnost](#configure-severity-levels) **chyby**
- znak "!" v trojúhelníku označuje [závažnost](#configure-severity-levels) **Upozornění**
- znak "i" v kruhu indikuje [závažnost](#configure-severity-levels) **informací**
- znak "i" v kruhu na pozadí s světlou barvou označuje [závažnost](#configure-severity-levels) **skrytého**
- Šipka dolů v kruhu indikuje, že je diagnostika potlačena.

![Ikony diagnostiky v Průzkumník řešení](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Převést existující soubor RuleSet na soubor EditorConfig

Počínaje verzí sady Visual Studio 2019 verze 16,5 jsou soubory RuleSet zastaraly namísto souboru EditorConfig pro konfiguraci analyzátoru pro spravovaný kód. Většina nástrojů sady Visual Studio pro konfiguraci závažnosti pravidla analyzátoru se aktualizovala tak, aby fungovala na souborech EditorConfig namísto souborů RuleSet. Soubory EditorConfig vám umožní nakonfigurovat obě možnosti pro závažnost pravidla analyzátoru i analyzátor, včetně možností stylu kódu IDE sady Visual Studio. Důrazně doporučujeme převést existující soubor RuleSet na soubor EditorConfig. Doporučuje se také uložit soubor EditorConfig v kořenovém adresáři úložiště nebo ve složce řešení. Pomocí kořenového adresáře vaší složky úložiště nebo řešení se ujistěte, že nastavení závažnosti z tohoto souboru se automaticky aplikuje na celé úložiště nebo řešení v uvedeném pořadí.

Existuje několik způsobů, jak převést existující soubor RuleSet na soubor EditorConfig:

- Z editoru RuleSet v aplikaci Visual Studio (vyžaduje Visual Studio 2019 16,5 nebo novější). Pokud váš projekt už používá určitý soubor RuleSet jako svůj `CodeAnalysisRuleSet` , můžete ho převést na ekvivalentní soubor EditorConfig z editoru RuleSet v rámci sady Visual Studio.

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

1. V Průzkumník řešení rozbalte položku **References**  >  **analyzátory** odkazů (nebo **Dependencies**  >  **analyzátory** závislostí pro projekty .NET Core).

2. Rozbalte sestavení, které obsahuje pravidlo, pro které chcete nastavit závažnost.

::: moniker range=">=vs-2019"
3. Klikněte pravým tlačítkem na pravidlo a vyberte **nastavit závažnost**. V místní nabídce vyberte jednu z možností závažnosti.

   Visual Studio přidá položku do souboru EditorConfig, aby nakonfigurovala pravidlo na požadovanou úroveň. Pokud váš projekt používá soubor RuleSet namísto souboru EditorConfig, je položka závažnost přidána do souboru ruleset.

   > [!TIP]
   > Pokud v projektu ještě nemáte soubor EditorConfig nebo RuleSet, Visual Studio vytvoří nový soubor EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Klikněte pravým tlačítkem na pravidlo a vyberte **nastavit závažnost sady pravidel**. V místní nabídce vyberte jednu z možností závažnosti.

   Závažnost pravidla se uloží do souboru aktivní sady pravidel.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Nastavte závažnost pravidla v souboru sady pravidel.

![Soubor sady pravidel v Průzkumník řešení](media/ruleset-in-solution-explorer.png)

1. Otevřete soubor aktivní sady pravidel jedním z následujících způsobů:

- V **Průzkumník řešení**dvakrát klikněte na soubor, klikněte pravým tlačítkem na uzel **referenční**  >  **analyzátory** a vyberte **Otevřít aktivní sadu pravidel**.
- Na stránce vlastností **Analýza kódu** projektu vyberte možnost **otevřít** .

  Pokud se jedná o první úpravu sady pravidel, sada Visual Studio vytvoří kopii výchozího souboru sady pravidel a pojmenuje ho * \<projectname> . ruleset*a přidá ho do projektu. Tato vlastní sada pravidel se také stal aktivní sadou pravidel pro váš projekt.

   > [!NOTE]
   > Projekty .NET Core a .NET Standard nepodporují příkazy nabídky pro sady pravidel v **Průzkumník řešení**, například **otevřete aktivní sadu pravidel**. Chcete-li určit nevýchozí sadu pravidel pro projekt .NET Core nebo .NET Standard, přidejte do souboru projektu ručně [vlastnost **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) . Pravidla můžete konfigurovat v rámci sady pravidel v uživatelském rozhraní editoru sad pravidel sady Visual Studio.

1. Přejděte k pravidlu tak, že rozbalíte jeho obsahující sestavení.

1. Ve sloupci **Akce** výběrem hodnoty otevřete rozevírací seznam a v seznamu zvolte požadovanou závažnost.

   ![Soubor sady pravidel je otevřen v editoru.](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Konfigurovat generovaný kód

Analyzátory jsou spouštěny ve všech zdrojových souborech v projektu a jejich porušení. Tato porušení nejsou ale užitečná u generovaných souborů kódu, jako jsou soubory kódu vygenerované návrhářem, dočasné zdrojové soubory vygenerované systémem sestavení atd. Uživatelé nemůžou ručně upravovat tyto soubory a/nebo se netýkají narušení oprav v těchto druzích souborů generovaných nástrojem.

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

Existuje několik způsobů, jak potlačit porušení pravidel:

::: moniker range=">=vs-2019"

- V **souboru EditorConfig**

  Nastavte závažnost na, například `none` `dotnet_diagnostic.CA1822.severity = none` .

- Z nabídky **analyzovat**

  Vyberte možnost **analyzovat**  >  **sestavení a potlačit aktivní problémy** na řádku nabídek, abyste potlačili všechna aktuální porušení. Někdy se označuje jako "monitorování standardních hodnot".

::: moniker-end

::: moniker range="vs-2017"

- Z nabídky **analyzovat**

  Vyberte možnost **analyzovat**  >  **Spustit analýzu kódu a potlačením aktivních problémů** na řádku nabídek potlačíte všechna aktuální porušení. Někdy se označuje jako "monitorování standardních hodnot".

::: moniker-end

- Z **Průzkumník řešení**

  Nastavte závažnost pravidla na **None (žádné**).

- Z **editoru sad pravidel**

  Zrušte zaškrtnutí políčka vedle jeho názvu nebo nastavte **akci** na **žádná**.

- Z **editoru kódu**

  Umístěte kurzor na řádek kódu s porušením a stisknutím klávesy **CTRL** + **(.)** otevřete nabídku **rychlé akce** . Vyberte možnost **potlačit CAXXXX**  >  **ve zdroji nebo v souboru potlačení**.

  ![Potlačit diagnostiku z nabídky rychlé akce](media/suppress-diagnostic-from-editor.png)

- Z **Seznam chyb**

  Vyberte pravidla, která chcete potlačit, a potom klikněte pravým tlačítkem myši a vyberte možnost **potlačit**  >  **ve zdroji nebo v souboru potlačení**.

  - Pokud potlačíte **ve zdroji**, otevře se dialogové okno **Náhled změn** , ve kterém se zobrazí náhled [#pragma upozornění](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) a direktiva Visual Basic [#Disable upozornění](/dotnet/visual-basic/language-reference/directives/directives) , která je přidána do zdrojového kódu.

    ![Náhled Přidání upozornění #pragma v souboru kódu](media/pragma-warning-preview.png)

  - Pokud vyberete možnost **v souboru potlačení**, otevře se dialogové okno **Náhled změn** a zobrazí náhled <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributu, který je přidán do globálního souboru potlačení.

    ![Náhled přidání atributu SuppressMessage do souboru potlačení](media/preview-changes-in-suppression-file.png)

  V dialogovém okně **Náhled změn** vyberte **použít**.

  > [!NOTE]
  > Pokud nevidíte možnost nabídky **potlačit** v **Průzkumník řešení**, porušení pravděpodobně přijde z buildu a ne za živou analýzu. **Seznam chyb** zobrazuje narušení diagnostiky nebo pravidla, a to od živých analýz kódu i sestavení. Vzhledem k tomu, že diagnostika sestavení může být zastaralá, například pokud jste upravili kód pro opravu porušení, ale ještě nebyla znovu sestavena, nemůžete tuto diagnostiku z **Seznam chyb**potlačit. Diagnostika z živých analýz nebo IntelliSense je vždy aktuální s aktuálními zdroji a lze ji potlačit z **Seznam chyb**. Pokud chcete z výběru vyloučit diagnostiku *sestavení* , přepněte filtr zdroje **Seznam chyb** z **Build + IntelliSense** na **pouze IntelliSense**. Pak vyberte diagnostiku, kterou chcete potlačit, a pokračujte podle postupu popsaného výše.
  >
  > ![Zdrojový filtr Seznam chyb v aplikaci Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Použití příkazového řádku

Při sestavování projektu na příkazovém řádku se porušení pravidla zobrazí ve výstupu sestavení, pokud jsou splněny následující podmínky:

- Analyzátory jsou nainstalovány jako balíček NuGet a nikoli jako rozšíření VSIX.

- V kódu projektu je porušeno jedno nebo více pravidel.

- [Závažnost](#configure-severity-levels) narušeného pravidla je nastavena na možnost **Upozornění**, v takovém případě porušení nezpůsobí selhání sestavení nebo **Chyba**. v takovém případě porušení způsobí selhání sestavení.

Podrobnosti výstupu sestavení neovlivňují, zda jsou zobrazena porušení pravidel. I při **tiché** podrobnostech se ve výstupu sestavení zobrazí porušení pravidel.

> [!TIP]
> Pokud jste zvyklí spouštět starší verzi analýzy z příkazového řádku, a to buď pomocí *FxCopCmd.exe* nebo prostřednictvím nástroje MSBuild s příznakem **RunCodeAnalysis** , zde je postup, jak to udělat pomocí analyzátorů kódu.

Chcete-li zobrazit narušení analyzátoru na příkazovém řádku při sestavování projektu pomocí nástroje MSBuild, spusťte příkaz podobný tomuto:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Následující obrázek ukazuje výstup sestavení příkazového řádku z sestavení projektu, který obsahuje porušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušením pravidla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Závislé projekty

Pokud v projektu .NET Core přidáte odkaz na projekt, který obsahuje analyzátory NuGet, tyto analyzátory jsou také automaticky přidány do závislého projektu. Chcete-li toto chování zakázat, například pokud je závislý projekt projekt testování částí, označte balíček NuGet jako soukromý v souboru *. csproj* nebo *. vbproj* odkazovaného projektu nastavením atributu **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v aplikaci Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Odeslat chybu analyzátoru kódu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Použití sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Potlačit upozornění analýzy kódu](../code-quality/in-source-suppression-overview.md)