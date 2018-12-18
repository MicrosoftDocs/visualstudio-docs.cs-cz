---
title: Použití a konfiguraci analyzátory Roslyn
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 47dc7d38a2ae9b842891d2e36aebd9b009297cbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817038"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Konfigurovat a používat pravidla analyzátoru Roslyn

Pravidla analyzátoru .NET compiler Platform ("Roslyn"), nebo *diagnostiky*, analýza kódu C# nebo Visual Basic během psaní. Každý diagnostiky má výchozí závažnost a potlačení stavu, ve kterém můžete přepsat pro váš projekt. Tento článek se týká nastavení závažnost pravidla, použití sad pravidel a potlačení porušení.

## <a name="analyzers-in-solution-explorer"></a>Analyzátory v Průzkumníku řešení

Můžete provést mnoho přizpůsobení analyzátor Diagnostika z **Průzkumníka řešení**. Pokud jste [instalace analyzátorů](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet, **analyzátory** uzel se zobrazí v části **odkazy** nebo **závislosti** uzel v  **Průzkumník řešení**. Pokud rozbalíte **analyzátory**a potom rozbalte některou sestavení analyzátoru, zobrazí se všechny diagnostiky v sestavení.

![Analyzátory uzlu v Průzkumníkovi řešení](media/analyzers-expanded-in-solution-explorer.png)

Můžete zobrazit vlastnosti diagnostiky, včetně jeho popis a výchozí závažnost, **vlastnosti** okno. Chcete-li zobrazit vlastnosti, klikněte pravým tlačítkem na pravidlo a vyberte **vlastnosti**, nebo vyberte pravidlo a potom stiskněte klávesu **Alt**+**Enter**.

![Diagnostické vlastnosti v okně Vlastnosti](media/analyzer-diagnostic-properties.png)

Chcete-li najdete v online dokumentaci pro diagnostiku, klikněte pravým tlačítkem na diagnostiky a vyberte **zobrazit nápovědu**.

Ikony vedle každého Diagnostika v rámci **Průzkumníka řešení** odpovídají ikony se zobrazí v pravidle nastavit po otevření v editoru:

- Označuje, "i" v kruhu [závažnost](#rule-severity) z **informace**
- "!" v trojúhelníku označuje [závažnost](#rule-severity) z **upozornění**
- Označuje, "x" v kruhu [závažnost](#rule-severity) z **chyba**
- Označuje, "i" v kruhu na pozadí světlé [závažnost](#rule-severity) z **skryté**
- na šipku dolů v kruhu Určuje, že je potlačeno diagnostiky

![Diagnostika ikony v Průzkumníku řešení](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Sady pravidel

A [sada pravidel, která](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) je soubor XML, který ukládá stav závažnosti a potlačení pro jednotlivé diagnostiky. Použití sad pravidel do jednoho projektu a projekt může obsahovat více sad pravidel. Chcete-li zobrazit aktivní sadu v editoru pravidel, klikněte pravým tlačítkem na **analyzátory** uzel v **Průzkumníka řešení** a vyberte **otevřít aktivní sadu pravidel**. Pokud je to poprvé při přístupu k pravidla nastavena, soubor s názvem  *\<projectname > Analýza* se přidá do projektu a zobrazí se v **Průzkumníka řešení**.

> [!NOTE]
> Sady pravidel patří analýza statického kódu (binární) a pravidla analyzátoru Roslyn.

Můžete změnit aktivní sadu pravidel pro projekt na **analýzy kódu** karta Vlastnosti projektu. Vyberte pravidlo, nastavte **spustit tuto sadu pravidel** rozevíracího seznamu. Můžete také otevřít sadu z pravidel **analýzy kódu** stránku vlastností tak, že vyberete **otevřete**.

## <a name="rule-severity"></a>Závažnost pravidla

Můžete nakonfigurovat závažnost pravidla analyzátoru nebo *diagnostiky*, pokud jste [instalace analyzátorů](../code-quality/install-roslyn-analyzers.md) jako balíček NuGet. Následující tabulka uvádí možnosti závažnosti pro diagnostiku:

|Závažnost|Chování sestavení|Chování editoru|
|-|-|-|
|Chyba|Narušení se zobrazují jako *chyby* v **seznam chyb** a do příkazového řádku výstup sestavení a sestavení selže.|Poškozený kód je podtržený s červenou vlnovkou a označené jako malé červeným rámečkem posuvníku.|
|Upozornění|Narušení se zobrazují jako *upozornění* v **seznam chyb** do příkazového řádku výstup sestavení, ale nezpůsobí sestavení selhala.|Poškozený kód je podtržený s zelenou vlnovkou a označené pomocí malé zeleného pole do oblasti posuvníku.|
|Informace o|Narušení se zobrazují jako *zprávy* v **seznam chyb**a vůbec ne ve výstupu sestavení z příkazového řádku.|Poškozený kód je podtržený s šedá vlnovkou a označené pomocí malé šedé pole do oblasti posuvníku.|
|Hidden|Non viditelné pro uživatele.|Non viditelné pro uživatele. Diagnostiky se hlásí k modulu diagnostiky integrovaného vývojového prostředí, ale.|
|Žádné|Zcela potlačit.|Zcela potlačit.|

Kromě toho můžete "obnovit" závažnost pravidla nastavením na **výchozí**. Každý diagnostiky má výchozí závažnost, která si můžete prohlédnout ve **vlastnosti** okna.

Následující snímek obrazovky ukazuje tři různé diagnostické narušení v editoru kódu, s třemi jinou závažností. Všimněte si, že barvu podtržení, stejně jako malé pole do oblasti posuvníku na pravé straně.

![Chyba, upozornění a informace o narušení v editoru kódu](media/diagnostics-severity-colors.png)

Následující snímek obrazovky ukazuje stejný tři porušení zásad, jak se objeví v **seznam chyb**:

![Chyba, upozornění a informace o narušení v seznamu chyb](media/diagnostics-severities-in-error-list.png)

Můžete změnit závažnost pravidla z **Průzkumníka řešení**, nebo v rámci  *\<projectname > Analýza* soubor, který je přidán do řešení, když změníte závažnost pravidla v  **Průzkumník řešení**.

![Soubor sady pravidel v Průzkumníku řešení](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Chcete-li nastavit závažnost pravidla z Průzkumníka řešení

1. V **Průzkumníka řešení**, rozbalte **odkazy** > **analyzátory** (**závislosti**  >  **Analyzátory** pro projekty .NET Core).

1. Rozbalte položku, která obsahuje pravidlo, které chcete nastavit závažnost pro sestavení.

1. Klikněte pravým tlačítkem na pravidlo a vyberte **nastavit závažnost pravidla nastavit**. V rozevírací nabídce vyberte jednu z možností závažnosti.

   Závažnost pravidla je uložen v souboru sady pravidel aktivní.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Chcete-li nastavit pravidlo závažnost v pravidle nastavit soubor

1. Otevřete soubor pravidlo nastaví poklepáním v **Průzkumníku řešení**, kde vyberou **otevřít aktivní sadu pravidel** v nabídce klikněte pravým tlačítkem **analyzátory** uzlu, nebo výběrem **Otevřít** na **analýzy kódu** stránku vlastností pro projekt.

1. Vyhledejte pravidlo tak, že rozbalíte její obsahující sestavení.

1. V **akce** sloupce, vyberte hodnotu, otevřete rozevírací seznam a vyberte požadovaný závažnost ze seznamu.

   ![Soubor sady pravidel, které jsou otevřeny v editoru](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Potlačit porušení

Potlačit porušení pravidel několika způsoby:

- Chcete-li potlačit všechna aktuální porušení pravidel, vyberte **analyzovat** > **spustit analýzu kódu a potlačit aktivních problémů** na řádku nabídek. To se někdy označuje jako "monitorování standardních hodnot".

- Potlačit diagnostiku z **Průzkumníka řešení**, nastavte jeho závažnosti na **žádný**.

- Chcete-li potlačit diagnostiku z editoru sad pravidel, zrušte zaškrtnutí políčka vedle jeho názvu nebo nastavte **akce** k **žádný**.

- Potlačit diagnostiku z editoru kódu, umístěte kurzor na řádek kódu s porušení a stiskněte klávesu **Ctrl**+**.** Chcete-li otevřít **rychlé akce** nabídky. Vyberte **potlačit CAxxxx** > **ve zdroji** nebo **potlačit CAxxxx** > **v souboru potlačení**.

   ![Potlačit diagnostiku z nabídky rychlé akce](media/suppress-diagnostic-from-editor.png)

- Potlačit diagnostiku z **seznam chyb**, naleznete v tématu [potlačit porušení ze seznamu chyb](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Potlačit porušení ze seznamu chyb

Můžete potlačit diagnostiku pro jeden nebo více z **seznam chyb** výběrem ty, které chcete potlačit, a klikněte pravým tlačítkem myši a vyberete **potlačit** > **v zdroje**  nebo **potlačit** > **v souboru potlačení**.

- Pokud vyberete **zdroje v**, **náhled změn** dialogové okno se otevře a zobrazí náhled jazyka C# [varování #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) nebo Visual Basic [#Disable upozornění](/dotnet/visual-basic/language-reference/directives/directives) – direktiva, která je přidána ke zdrojovému kódu.

   ![Přidání upozornění #pragma v souboru kódu ve verzi Preview](media/pragma-warning-preview.png)

- Pokud vyberete **v souboru potlačení**, **náhled změn** dialogové okno se otevře a zobrazí náhled <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atribut, který se přidá do soubor globálního potlačení.

   ![Přidání atributu SuppressMessage do souboru potlačení ve verzi Preview](media/preview-changes-in-suppression-file.png)

V **náhled změn** dialogového okna, vyberte **použít**.

**Seznam chyb** zobrazí diagnostiky nebo pravidlo porušení z obou živá analýza kódu a sestavení. Protože Diagnostika sestavení může být zastaralá, například pokud jste upravili kódu, chcete-li vyřešit porušení zásad, ale nebyly znovu sestavit, nelze potlačit tato Diagnostika z **seznam chyb**. Ale diagnostika živé analýze nebo technologie IntelliSense, jsou vždy aktuální s aktuálním zdroji a lze potlačit z **seznam chyb**. Zakázána možnost potlačení v nabídce klepněte pravým tlačítkem nebo kontextu, je pravděpodobné, protože má jednu nebo více sestavení diagnostiky ve výběru. Vyloučit diagnostiky sestavení z vašeho výběru, přepínat **seznam chyb** zdrojový filtr ze sloupce **sestavení + IntelliSense** k **pouze technologie Intellisense**. Vyberte diagnostiky, které chcete potlačit a pokračovat, jak je popsáno výše.

![Filtr zdroje seznam chyb v sadě Visual Studio](media/error-list-filter.png)

> [!NOTE]
> V projektu .NET Core Pokud přidáte odkaz na projekt, který má NuGet analyzátory těchto Analyzátory se automaticky přidají do závislý projekt příliš. Chcete-li zakázat toto chování, například pokud závislý projekt je projekt testování částí, označte balíček NuGet jako v privátní *.csproj* nebo *.vbproj* souboru odkazovaného projektu:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="command-line-usage"></a>Použití příkazového řádku

Při sestavování projektu na příkazovém řádku se porušení pravidel se zobrazí ve výstupu sestavení. Pokud jsou splněny následující podmínky:

- Analyzátory jsou nainstalovány jako balíček Nuget a ne jako rozšíření VSIX.

- Jeden nebo více pravidel se poruší, v projektu kódu.

- [Závažnost](#rule-severity) porušená pravidla je nastaven na hodnotu **upozornění**, v takovém případě narušení nezpůsobí, aby sestavení selhalo, nebo **chyba**, v takovém případě narušení způsobit, že sestavení selže.

Podrobnost výstupu sestavení nemá vliv, zda jsou zobrazeny porušení pravidel. I přes **quiet** podrobností, porušení pravidel se zobrazí ve výstupu sestavení.

> [!TIP]
> Pokud jste zvyklí na spuštění z příkazového řádku, buď pomocí statické analýzy kódu *FxCopCmd.exe* nebo prostřednictvím msbuild s parametrem / **RunCodeAnalysis** příznak, tady je postup, který s analyzátory Roslyn.

Analyzátor narušení zobrazíte na příkazovém řádku při vytváření projektu pomocí nástroje msbuild, spusťte příkaz takto:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

Následující obrázek ukazuje sestavení z příkazového řádku výstup z operace sestavení projektu, který obsahuje porušení pravidla analyzátoru:

![Výstup nástroje MSBuild s porušení pravidla](media/command-line-build-analyzers.png)

## <a name="see-also"></a>Viz také:

- [Přehled analyzátory Roslyn v sadě Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Odeslání chyby analyzátoru Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Použití sad pravidel](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Potlačení upozornění analýzy kódu](../code-quality/in-source-suppression-overview.md)