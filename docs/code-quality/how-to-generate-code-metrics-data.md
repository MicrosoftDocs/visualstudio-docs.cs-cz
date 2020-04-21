---
title: Generovat metriky kódu z ide nebo příkazového řádku
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649326"
---
# <a name="how-to-generate-code-metrics-data"></a>Postup: Generování dat metrik kódu

Data metrik kódu můžete generovat třemi způsoby:

- Instalací [analyzátorů FxCop](#fxcop-analyzers-code-metrics-rules) a povolením čtyř pravidel metrik kódu (udržovatelnosti), která obsahuje.

- Výběrem příkazu [ **nabídky Analyzovat** > vypočítat metriky kódu](#calculate-code-metrics-menu-command) v sadě Visual Studio.

- Z [příkazového řádku](#command-line-code-metrics) pro projekty jazyka C# a Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Pravidla metrik kódu analyzátorů FxCop

[Balíček FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) obsahuje několik pravidel [analyzátoru metrik](roslyn-analyzers-overview.md) kódu:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Tato pravidla jsou ve výchozím nastavení zakázána, ale můžete je povolit z [**Průzkumníka řešení**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) nebo v souboru [sady pravidel.](using-rule-sets-to-group-code-analysis-rules.md) Chcete-li například povolit pravidlo CA1502 jako upozornění, soubor .ruleset bude obsahovat následující položku:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfigurace

Můžete nakonfigurovat prahové hodnoty, při kterých pravidla metrikkódu v spuštění balíčku analyzátory FxCop.

1. Vytvořte textový soubor. Jako příklad jej můžete pojmenovat *CodeMetricsConfig.txt*.

2. Přidejte požadované prahové hodnoty do textového souboru v následujícím formátu:

   ```txt
   CA1502: 10
   ```

   V tomto příkladu je pravidlo [CA1502](ca1502.md) nakonfigurováno tak, aby se sníbylo, když je cyklomatická složitost metody větší než 10.

3. V okně **Vlastnosti** sady Visual Studio nebo v souboru projektu označte akci sestavení konfiguračního souboru jako [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Příklad:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Příkaz Nabídky Vypočítat metriky kódu

Generovat metriky kódu pro jeden nebo všechny otevřené projekty v ide pomocí **nabídky Analyzovat** > **vypočítat metriky kódu.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generovat výsledky metrik kódu pro celé řešení

Můžete generovat výsledky metrik kódu pro celé řešení libovolným z následujících způsobů:

- Na řádku nabídek zvolte **Analyzovat** > **výpočet metrik** > kódu**pro řešení**.

- V **Průzkumníku řešení**klikněte pravým tlačítkem myši na řešení a pak zvolte **Vypočítat metriky kódu**.

- V okně **Výsledky metrik kódu** zvolte tlačítko **Vypočítat metriky kódu pro řešení.**

Výsledky jsou generovány a zobrazí se okno **Výsledky metrikkódu.** Chcete-li zobrazit podrobnosti výsledků, rozbalte strom ve sloupci **Hierarchie.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generovat výsledky metrik kódu pro jeden nebo více projektů

1. V **Průzkumníku řešení**vyberte jeden nebo více projektů.

1. Na řádku nabídek zvolte **Analyzovat** > **výpočet metrik** > kódu**pro vybrané projekty**.

Výsledky jsou generovány a zobrazí se okno **Výsledky metrikkódu.** Chcete-li zobrazit podrobnosti výsledků, rozbalte strom v **hierarchii**.

::: moniker range="vs-2017"

> [!NOTE]
> Příkaz **Vypočítat metriky kódu** nefunguje pro projekty .NET Core a .NET Standard. Chcete-li vypočítat metriky kódu pro projekt .NET Core nebo .NET Standard, můžete:
>
> - Místo toho výpočet metrik kódu z [příkazového řádku](#command-line-code-metrics)
>
> - Upgrade na [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Metriky kódu příkazového řádku

Můžete generovat data metrik kódu z příkazového řádku pro projekty Jazyka C# a Visual Basic pro aplikace .NET Framework, .NET Core a .NET Standard. Chcete-li spustit metriky kódu z příkazového řádku, nainstalujte [balíček Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) nebo vytvořte spustitelný soubor [Metrics.exe](#metricsexe) sami.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Balíček Microsoft.CodeAnalysis.Metrics NuGet

Nejjednodušší způsob, jak generovat data metrik kódu z příkazového řádku, je instalace balíčku [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet. Po instalaci balíčku spusťte `msbuild /t:Metrics` z adresáře, který obsahuje soubor projektu. Příklad:

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

Název výstupního souboru můžete přepsat `/p:MetricsOutputFile=<filename>`zadáním . Data metrik kódu [staršího stylu](#previous-versions) můžete také `/p:LEGACY_CODE_METRICS_MODE=true`získat zadáním . Příklad:

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

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Pokud nechcete nainstalovat balíček NuGet, můžete vygenerovat a použít *metrics.exe* spustitelný přímo. Chcete-li generovat spustitelný soubor *Metrics.exe:*

1. Klon [dotnet / roslyn-analyzátory](https://github.com/dotnet/roslyn-analyzers) repo.
2. Otevřete příkazový řádek pro vývojáře pro Visual Studio jako správce.
3. Z kořenového adresáře **repo analyzátorů roslyn** proveďte následující příkaz:`Restore.cmd`
4. Změnit adresář na *src\Tools*.
5. K vytvoření projektu **Metrics.csproj** proveďte následující příkaz:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Spustitelný soubor s názvem *Metrics.exe* je generován v adresáři *artifacts\bin* pod kořenovým adresářem úložiště.

#### <a name="metricsexe-usage"></a>Využití souboru Metrics.exe

Chcete-li spustit *soubor Metrics.exe*, zařazujete jako argumenty projekt nebo řešení a výstupní soubor XML. Příklad:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Starší režim

Můžete se rozhodnout vytvořit *Soubor Metrics.exe* ve *starším režimu*. Starší verze nástroje generuje hodnoty metriky, které jsou blíže k tomu, co [starší verze nástroje generované](#previous-versions). Navíc ve starším režimu *Nástroj Ín.* Například negeneruje data metrik kódu pro inicializátory polí a vlastností. Starší režim je užitečný pro zpětnou kompatibilitu nebo pokud máte brány vrácení kódu na základě čísel metrik kódu. Příkaz k sestavení *souboru Metrics.exe* ve starším režimu je:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Další informace naleznete v [tématu Enable generating code metrics in legacy mode](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Předchozí verze

::: moniker range=">=vs-2019"
Visual Studio 2015 součástí nástroje metrikkódu příkazového řádku, který se také nazýval *Metrics.exe*. Tato předchozí verze nástroje provedla binární analýzu, tedy analýzu založenou na sestavení. Novější verze nástroje *Metrics.exe* místo toho analyzuje zdrojový kód. Vzhledem k tomu, že novější *nástroj Metrics.exe* je založen na zdrojovém kódu, mohou se výsledky metrik kódu příkazového řádku lišit od výsledků generovaných ide sady Visual Studio a předchozími verzemi nástroje *Metrics.exe*. Počínaje Visual Studio 2019, Visual Studio IDE analyzuje zdrojový kód, jako je nástroj příkazového řádku a výsledky by měly být stejné.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 součástí nástroje metrikkódu příkazového řádku, který se také nazýval *Metrics.exe*. Tato předchozí verze nástroje provedla binární analýzu, tedy analýzu založenou na sestavení. Nový nástroj *Metrics.exe* místo toho analyzuje zdrojový kód. Vzhledem k tomu, že nový nástroj *Metrics.exe* je založen na zdrojovém kódu, výsledky metrik kódu příkazového řádku se liší od výsledků generovaných ide sady Visual Studio a předchozími verzemi nástroje *Metrics.exe*.
::: moniker-end

Nový nástroj metriky kódu příkazového řádku vypočítá metriky i za přítomnosti chyb zdrojového kódu, pokud lze načíst řešení a projekt.

#### <a name="metric-value-differences"></a>Rozdíly v hodnotě metriky

::: moniker range=">=vs-2019"
Počínaje Visual Studio 2019 verze 16.4 a Microsoft.CodeAnalysis.Metics `SourceLines` (2.9.5) a `ExecutableLines` nahradit předchozí `LinesOfCode` metriku. Popis nových metrik najdete v tématu [Hodnoty metrik kódu](../code-quality/code-metrics-values.md). Metrika `LinesOfCode` je k dispozici ve starším režimu.
::: moniker-end
::: moniker range="vs-2017"
Metrika `LinesOfCode` je přesnější a spolehlivější v novém nástroji metrik kódu příkazového řádku. Je nezávislý na všech rozdílech kódů a nemění se při změně sady nástrojů nebo za běhu. Nový nástroj počítá skutečné řádky kódu, včetně prázdných řádků a komentářů.
::: moniker-end

Jiné metriky, `CyclomaticComplexity` `MaintainabilityIndex` jako jsou a používat stejné vzorce jako předchozí verze *Metrics.exe* `IOperations` , ale nový nástroj počítá počet (logické zdrojové pokyny) namísto zprostředkující jazyk (IL) pokyny. Čísla se budou mírně lišit od čísel generovaných ide sady Visual Studio a předchozími verzemi programu *Metrics.exe*.

## <a name="see-also"></a>Viz také

- [Použití okna Výsledky metrik kódu](../code-quality/working-with-code-metrics-data.md)
- [Hodnoty metrik kódu](../code-quality/code-metrics-values.md)
