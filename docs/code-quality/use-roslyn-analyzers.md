---
title: Závažnost pravidla analyzátoru a potlačení
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 81c1c200ba9ab0a50381192b34bad5e9b221fb29
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305668"
---
# <a name="use-code-analyzers"></a>Použití analyzátorů kódu

Analyzátory kódu .NET Compiler Platform ("Roslyn") analyzují C# kód nebo Visual Basic při psaní. Každé *diagnostice* nebo pravidlo má výchozí závažnost a stav potlačení, který může být pro váš projekt přepsán. Tento článek popisuje nastavení závažnosti pravidla, použití sad pravidel a potlačení porušení.

## <a name="analyzers-in-solution-explorer"></a>Analyzátory v Průzkumník řešení

Z **Průzkumník řešení**můžete provádět většinu úprav diagnostiky analyzátoru. Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, pod uzlem **odkazy** nebo **závislosti** v **Průzkumník řešení**se zobrazí uzel **analyzátory** . Pokud rozbalíte **analyzátory**a pak rozbalíte jedno ze sestavení analyzátoru, uvidíte všechny diagnostiky v sestavení.

![Uzel analyzátorů v Průzkumník řešení](media/analyzers-expanded-in-solution-explorer.png)

V okně **vlastnosti** můžete zobrazit vlastnosti diagnostiky, včetně jeho popisu a výchozí závažnosti. Chcete-li zobrazit vlastnosti, klikněte pravým tlačítkem na pravidlo a vyberte **vlastnosti**, nebo vyberte pravidlo a stiskněte klávesu **ALT**+**Zadejte**.

![Diagnostické vlastnosti v okno Vlastnosti](media/analyzer-diagnostic-properties.png)

Pokud chcete zobrazit online dokumentaci pro diagnostiku, klikněte pravým tlačítkem na diagnostiku a vyberte **Zobrazit nápovědu**.

Ikony vedle každé diagnostiky v **Průzkumník řešení** odpovídají ikonám, které vidíte v sadě pravidel při jejich otevírání v editoru:

- znak "x" v kruhu indikuje [závažnost](#rule-severity) **chyby**
- znak "!" v trojúhelníku označuje [závažnost](#rule-severity) **Upozornění**
- znak "i" v kruhu indikuje [závažnost](#rule-severity) **informací**
- znak "i" v kruhu na pozadí s světlou barvou označuje [závažnost](#rule-severity) **skrytého**
- Šipka dolů v kruhu indikuje, že je diagnostika potlačena.

![Ikony diagnostiky v Průzkumník řešení](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Závažnost pravidla

::: moniker range=">=vs-2019"

Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*. Počínaje verzí Visual Studio 2019 verze 16,3 můžete nakonfigurovat závažnost pravidla [v souboru EditorConfig](#set-rule-severity-in-an-editorconfig-file). Závažnost pravidla můžete také změnit [z Průzkumník řešení](#set-rule-severity-from-solution-explorer) nebo [v souboru sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Pokud [nainstalujete analyzátory](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, můžete nakonfigurovat závažnost pravidel analyzátoru nebo *diagnostiky*. Závažnost pravidla můžete změnit [z Průzkumník řešení](#set-rule-severity-from-solution-explorer) nebo [v souboru sady pravidel](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

V následující tabulce jsou uvedeny různé možnosti závažnosti:

| Závažnost (Průzkumník řešení) | Závažnost (soubor EditorConfig) | Chování při sestavení | Chování editoru |
|-|-|-|
| Chyba | `error` | Porušení se zobrazují jako *chyby* v seznam chyb a ve výstupu sestavení příkazového řádku a způsobují selhání sestavení.| Poškozený kód je podtržen červenou vlnovkou a označený malým červeným polem na posuvníku. |
| Upozornění | `warning` | Porušení se zobrazí jako *Upozornění* v seznam chyb a ve výstupu sestavení příkazového řádku, ale nezpůsobí selhání sestavení. | Poškozený kód je podtržen zelenou vlnovkou a označený malým zeleným polem na posuvníku. |
| Informace o | `suggestion` | Porušení se zobrazí jako *zprávy* v seznam chyb, a ne vůbec ve výstupu sestavení příkazového řádku. | Poškozený kód je podtržený šedou vlnovkou a označený malým šedým polem na posuvníku. |
| Hidden | `silent` | Uživatel není viditelný. | Uživatel není viditelný. Diagnostika se oznamuje diagnostickému modulu IDE, ale. |
| Žádné | `none` | Zcela potlačeno. | Zcela potlačeno. |
| Výchozí | `default` | Odpovídá výchozí závažnosti pravidla. Chcete-li určit výchozí hodnotu pravidla, podívejte se do okno Vlastnosti. | Odpovídá výchozí závažnosti pravidla. |

Následující snímek obrazovky editoru kódu ukazuje tři odlišná porušení s různými závažnostmi. Všimněte si barvy vlnovek a malého a barevného čtverce v posuvníku vpravo.

![Chyba, upozornění a porušení informací v editoru kódu](media/diagnostics-severity-colors.png)

Následující snímek obrazovky ukazuje stejná tři porušení zásad, která se zobrazují v Seznam chyb:

![Došlo k chybě, varování a porušení informací v Seznam chyb](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Nastavení závažnosti pravidla v souboru EditorConfig

(Visual Studio 2019 verze 16,3 a novější)

Obecná syntaxe pro určení závažnosti pravidla v souboru EditorConfig je následující:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Nastavení závažnosti pravidla v souboru EditorConfig má přednost před jakoukoli závažností, která je nastavená v sadě pravidel nebo v Průzkumník řešení. Můžete [ručně](#manually-configure-rule-severity) nakonfigurovat závažnost v souboru EditorConfig nebo [automaticky](#automatically-configure-rule-severity) prostřednictvím žárovky, která se zobrazí vedle porušení.

#### <a name="manually-configure-rule-severity"></a>Ruční konfigurace závažnosti pravidla

1. Pokud ještě nemáte soubor EditorConfig pro váš projekt, [přidejte ho](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Přidejte položku pro každé pravidlo, které chcete konfigurovat v odpovídající příponě souboru. Pokud třeba chcete nastavit závažnost pro [CA1822](ca1822.md) na `error` pro C# soubory, bude položka vypadat takto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Analyzátory ve stylu kódu IDE můžete také nakonfigurovat v souboru EditorConfig pomocí jiné syntaxe, například `dotnet_style_qualification_for_field = false:suggestion`. Pokud ale nastavíte závažnost pomocí syntaxe `dotnet_diagnostic`, má přednost. Další informace najdete v tématu [jazykové konvence pro EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Automaticky konfigurovat závažnost pravidla

Visual Studio nabízí pohodlný způsob konfigurace závažnosti pravidla z nabídky návrhy [rychlých akcí](../ide/quick-actions.md) .

1. Jakmile dojde k porušení, najeďte myší nad vlnovkou porušení v editoru a otevřete nabídku žárovky. Nebo umístěte kurzor na řádek a stiskněte **Ctrl**+ **.** (tečka).

2. V nabídce žárovky vyberte **Konfigurovat nebo potlačit problémy** > **Konfigurace \<rule ID > závažnost**.

   ![Konfigurace závažnosti pravidla z nabídky světlé žárovky v aplikaci Visual Studio](media/configure-rule-severity.png)

3. Tam vyberte jednu z možností závažnosti.

   ![Nakonfigurovat závažnost pravidla jako návrh](media/configure-rule-severity-suggestion.png)

   Visual Studio přidá položku do souboru EditorConfig, aby nakonfigurovala pravidlo na požadovanou úroveň, jak je uvedeno v poli Náhled.

   > [!TIP]
   > Pokud v projektu ještě nemáte soubor EditorConfig, Visual Studio ho vytvoří za vás.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Nastavit závažnost pravidla z Průzkumník řešení

1. V **Průzkumník řešení**rozbalte **odkazy** > **analyzátory** (nebo **závislosti** > **analyzátorů** pro projekty .NET Core).

1. Rozbalte sestavení, které obsahuje pravidlo, pro které chcete nastavit závažnost.

1. Klikněte pravým tlačítkem na pravidlo a vyberte **nastavit závažnost sady pravidel**. V rozevírací nabídce vyberte jednu z možností závažnosti.

   Závažnost pravidla se uloží do souboru aktivní sady pravidel.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Nastavte závažnost pravidla v souboru sady pravidel.

![Soubor sady pravidel v Průzkumník řešení](media/ruleset-in-solution-explorer.png)

1. Otevřete aktivní soubor sady pravidel tak, že na **Průzkumník řešení**něj dvakrát kliknete a vyberete **Otevřít aktivní sadu pravidel** v místní**nabídce uzlu** **odkazy** > , nebo výběrem možnosti **otevřít** v **kódu.** Stránka vlastností analýzy projektu

   Pokud se jedná o první úpravu sady pravidel, sada Visual Studio vytvoří kopii výchozího souboru sady pravidel a pojmenuje ji *\<projectname >. ruleset*a přidá je do projektu. Tato vlastní sada pravidel se také stal aktivní sadou pravidel pro váš projekt.

   > [!NOTE]
   > Projekty .NET Core a .NET Standard nepodporují příkazy nabídky pro sady pravidel v **Průzkumník řešení**, například **otevřete aktivní sadu pravidel**. Chcete-li určit nevýchozí sadu pravidel pro projekt .NET Core nebo .NET Standard, přidejte do souboru projektu ručně [vlastnost **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) . Pravidla můžete konfigurovat v rámci sady pravidel v uživatelském rozhraní editoru sad pravidel sady Visual Studio.

1. Přejděte k pravidlu tak, že rozbalíte jeho obsahující sestavení.

1. Ve sloupci **Akce** výběrem hodnoty otevřete rozevírací seznam a v seznamu vyberte požadovanou závažnost.

   ![Soubor sady pravidel je otevřen v editoru.](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Potlačit porušení

Existuje několik způsobů, jak potlačit porušení pravidel:

::: moniker range=">=vs-2019"

- V **souboru EditorConfig**

  Nastavte závažnost na `none`, například `dotnet_diagnostic.CA1822.severity = none`.

- Z nabídky **analyzovat**

  Vyberte možnost **analyzovat** > **sestavení a potlačení aktivních problémů** na řádku nabídek, aby se potlačila všechna aktuální porušení. Někdy se označuje jako "monitorování standardních hodnot".

::: moniker-end

::: moniker range="vs-2017"

- Z nabídky **analyzovat**

  Vyberte možnost **analyzovat** > **Spustit analýzu kódu a potlačit aktivní problémy** na řádku nabídek, aby se potlačila všechna aktuální porušení. Někdy se označuje jako "monitorování standardních hodnot".

::: moniker-end

- Z **Průzkumník řešení**

  Nastavte závažnost pravidla na **None (žádné**).

- Z **editoru sad pravidel**

  Zrušte zaškrtnutí políčka vedle jeho názvu nebo nastavte **akci** na **žádná**.

- Z **editoru kódu**

  Umístěte kurzor na řádek kódu s porušením a stisknutím **kombinace kláves Ctrl**+**tečka (.)** otevřete nabídku **rychlé akce** . Vyberte možnost **potlačit CAXXXX** > **ve zdroji/v souboru potlačení**.

  ![Potlačit diagnostiku z nabídky rychlé akce](media/suppress-diagnostic-from-editor.png)

- Z **Seznam chyb**

  Vyberte pravidla, která chcete potlačit, a potom klikněte pravým tlačítkem myši a vyberte možnost **potlačit** > **ve zdroji/v souboru potlačení**.

  - Pokud potlačíte **zdroj**, otevře se dialogové okno **Náhled změn** , ve kterém se zobrazí C# náhled [#pragma varování](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) nebo Visual Basic #Disable direktivu [Upozornění](/dotnet/visual-basic/language-reference/directives/directives) , která je přidána do zdrojového kódu.

    ![Náhled Přidání upozornění #pragma v souboru kódu](media/pragma-warning-preview.png)

  - Pokud vyberete možnost **v souboru potlačení**, otevře se dialogové okno **Náhled změn** , ve kterém se zobrazí náhled atributu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>, který je přidán do globálního souboru potlačení.

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

- [Závažnost](#rule-severity) narušeného pravidla je nastavena na možnost **Upozornění**, v takovém případě porušení nezpůsobí selhání sestavení nebo **Chyba**. v takovém případě porušení způsobí selhání sestavení.

Podrobnosti výstupu sestavení neovlivňují, zda jsou zobrazena porušení pravidel. I při **tiché** podrobnostech se ve výstupu sestavení zobrazí porušení pravidel.

> [!TIP]
> Pokud jste zvyklí spouštět starší verzi analýzy z příkazového řádku, a to buď pomocí *FxCopCmd. exe* , nebo pomocí nástroje MSBuild s příznakem **RunCodeAnalysis** , zde je postup, jak to udělat pomocí analyzátorů kódu.

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

## <a name="see-also"></a>Viz také:

- [Přehled analyzátorů kódu v aplikaci Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Odeslat chybu analyzátoru kódu](https://github.com/dotnet/roslyn-analyzers/issues)
- [Použití sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Potlačit upozornění analýzy kódu](../code-quality/in-source-suppression-overview.md)
