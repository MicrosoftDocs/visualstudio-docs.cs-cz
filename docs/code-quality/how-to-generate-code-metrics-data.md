---
title: Generování metrik kódu z integrovaného vývojového prostředí (IDE) nebo příkazového řádku
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 55f9904c95be45c7f293355340c814faafb5de2b
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568845"
---
# <a name="how-to-generate-code-metrics-data"></a>Postupy: generování dat metrik kódu

Data metriky kódu můžete generovat třemi způsoby:

- Instalací [analyzátorů FxCop](#fxcop-analyzers-code-metrics-rules) a povolením čtyř pravidel metriky kódu (udržovatelnosti), která obsahuje.

- Kliknutím na příkaz v nabídce [ **analyzovat** > **Vypočítat metriky kódu** ](#calculate-code-metrics-menu-command) v sadě Visual Studio.

- Z [příkazového řádku](#command-line-code-metrics) pro C# a Visual Basic projekty.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Pravidla metrik kódu analyzátorů FxCop

[Balíček NuGet FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) zahrnuje několik pravidel [analyzátoru](roslyn-analyzers-overview.md) metrik kódu:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506.md)

Tato pravidla jsou ve výchozím nastavení zakázaná, ale můžete je povolit z [**Průzkumník řešení**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) nebo v souboru [sady pravidel](using-rule-sets-to-group-code-analysis-rules.md) . Například pokud chcete, aby se pravidlo CA1502 jako upozornění, váš soubor. ruleset by obsahoval následující položku:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfigurace

Můžete nakonfigurovat prahové hodnoty, při kterých se pravidla metrik kódu v balíčku FxCop analyzers aktivují.

1. Vytvořte textový soubor. Jako příklad můžete pojmenovat *CodeMetricsConfig. txt*.

2. Přidejte požadované prahové hodnoty do textového souboru v následujícím formátu:

   ```txt
   CA1502: 10
   ```

   V tomto příkladu je [CA1502](ca1502.md) pravidla nastavená tak, aby se aktivovalo, když je cyklomatickáá složitost větší než 10.

3. V okně **vlastnosti** aplikace Visual Studio nebo v souboru projektu označte akci sestavení konfiguračního souboru jako [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Příklad:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Příkaz nabídky pro výpočet metriky kódu

Vygenerujte metriky kódu pro jeden nebo všechny otevřené projekty v integrovaném vývojovém prostředí pomocí nabídky **analyzovat** > **Vypočítat metriky kódu** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generování výsledků metrik kódu pro celé řešení

Můžete generovat Výsledky metrik kódu pro celé řešení některým z následujících způsobů:

- Z panelu nabídek vyberte možnost **analyzovat** > **Vypočítat metriky kódu** > **pro řešení**.

- V **Průzkumník řešení**klikněte pravým tlačítkem na řešení a pak zvolte **Vypočítat metriky kódu**.

- V okně **výsledků metrik kódu** klikněte na tlačítko **Vypočítat metriky kódu pro řešení** .

Výsledky jsou generovány a zobrazí se okno **Výsledky metrik kódu** . Chcete-li zobrazit podrobnosti výsledků, rozbalte strom ve sloupci **hierarchie** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generování výsledků metrik kódu pro jeden nebo více projektů

1. V **Průzkumník řešení**vyberte jeden nebo více projektů.

1. Z panelu nabídek vyberte možnost **analyzovat** > **Vypočítat metriky kódu** > **pro vybrané projekty**.

Výsledky jsou generovány a zobrazí se okno **Výsledky metrik kódu** . Chcete-li zobrazit podrobnosti výsledků, rozbalte stromovou strukturu v **hierarchii**.

::: moniker range="vs-2017"

> [!NOTE]
> Příkaz **Vypočítat metriky kódu** nefunguje pro projekty .NET Core a .NET Standard. Chcete-li vypočítat metriky kódu pro projekt .NET Core nebo .NET Standard, můžete:
>
> - Místo toho vypočítat metriky kódu z [příkazového řádku](#command-line-code-metrics)
>
> - Upgrade na [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metriky kódu příkazového řádku

Data metriky kódu můžete vygenerovat z příkazového řádku pro C# a Visual Basic projekty pro .NET Framework, .NET Core a .NET Standard aplikace. Chcete-li spustit metriky kódu z příkazového řádku, nainstalujte [balíček NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) nebo sestavte spustitelný soubor [metriky. exe](#metricsexe) sami.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Balíček NuGet Microsoft. CodeAnalysis. Metrics

Nejjednodušší způsob, jak generovat data metrik kódu z příkazového řádku, je instalace balíčku NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . Po instalaci balíčku spusťte `msbuild /t:Metrics` z adresáře, který obsahuje soubor projektu. Příklad:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Název výstupního souboru můžete přepsat zadáním `/p:MetricsOutputFile=<filename>`. Data metriky kódu [starší verze](#previous-versions) můžete získat také zadáním `/p:LEGACY_CODE_METRICS_MODE=true`. Příklad:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Výstup metrik kódu

Generovaný výstup XML má následující formát:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metriky. exe

Pokud balíček NuGet nechcete instalovat, můžete ho vygenerovat a použít přímo pomocí souboru *Metrics. exe* . Vygenerujte spustitelný soubor *. exe s metrikami* :

1. Naklonujte úložiště [dotnet/Roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) .
2. Otevřete Developer Command Prompt pro Visual Studio jako správce.
3. Z kořenového adresáře úložiště **Roslyn-Analyzer** spusťte následující příkaz: `Restore.cmd`
4. Změňte adresář na *src\Tools*.
5. Spuštěním následujícího příkazu Sestavte projekt **metriky. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Spustitelný soubor s názvem *metrika. exe* je vygenerován v adresáři *artifacts\bin* pod kořenem úložiště.

#### <a name="metricsexe-usage"></a>Metriky. exe využití

Chcete-li spustit *metriky. exe*, zadejte jako argumenty projekt nebo řešení a výstupní soubor XML. Příklad:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Starší režim

*Metriky. exe* si můžete sestavit v *režimu starší verze*. Verze v režimu starší verze nástroje generuje hodnoty metrik, které jsou bližší pro to, jaké [starší verze nástroje vygenerovala](#previous-versions). Kromě toho v režimu starší verze *metrika. exe* generuje metriky kódu pro stejnou sadu typů metod, pro kterou předchozí verze nástroje vygenerovala metriky kódu. Například negeneruje data metriky kódu pro Inicializátory polí a vlastností. Režim starší verze je vhodný pro zpětnou kompatibilitu nebo v případě, že máte v závislosti na číslech metriky kódu brány pro vrácení se změnami. Příkaz pro sestavení *metrik. exe* v režimu starší verze je:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Další informace najdete v tématu [Povolení generování metrik kódu v režimu starší verze](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Předchozí verze

Visual Studio 2015 zahrnovalo nástroj příkazového řádku pro metriky kódu, který se také nazývá *metrika. exe*. Tato předchozí verze nástroje obsahovala binární analýzu, tedy analýzu založenou na sestavení. Nový nástroj *metriky. exe* analyzuje místo toho zdrojový kód. Vzhledem k tomu, že nový nástroj *metriky. exe* je založen na zdrojovém kódu, jsou výsledky metrik kódu příkazového řádku odlišné od hodnot generovaných IDE sady Visual Studio a předchozími verzemi *metrik. exe*.

Nástroj metriky kódu nového příkazového řádku počítá metriky i v přítomnosti chyb zdrojového kódu, pokud je možné řešení a projekt načíst.

#### <a name="metric-value-differences"></a>Rozdíly v hodnotách metriky

Metrika `LinesOfCode` je přesnější a spolehlivá v novém nástroji příkazového řádku pro metriky kódu. Nezávisí na žádných rozdílech CODEGEN a nemění se, když se změní sada nástrojů nebo modul runtime. Nový nástroj počítá skutečné řádky kódu, včetně prázdných řádků a komentářů.

Jiné metriky, jako je například `CyclomaticComplexity` a `MaintainabilityIndex`, používají stejné vzorce jako předchozí verze *metrik. exe*, ale nový nástroj počítá počet `IOperations` (instrukcí logických zdrojů) místo instrukcí zprostředkujícího jazyka (IL). Čísla budou mírně odlišná na ta, která jsou vygenerována v integrovaném vývojovém prostředí sady Visual Studio a v předchozích verzích *metrik. exe*.

## <a name="see-also"></a>Viz také:

- [Použití okna výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md)
- [Hodnoty metrik kódu](../code-quality/code-metrics-values.md)
