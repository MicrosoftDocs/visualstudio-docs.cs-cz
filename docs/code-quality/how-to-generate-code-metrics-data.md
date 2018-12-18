---
title: Generovat metriky kódu z rozhraní IDE nebo příkazového řádku
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3f8d6f2df0b0d9ec6e3f9d8ead7fd1e08929f8e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966528"
---
# <a name="how-to-generate-code-metrics-data"></a>Postupy: vygenerování dat metrik kódu

Můžete generování výsledků metrik kódu pro jeden nebo více projektů nebo celého řešení. Metriky kódu jsou k dispozici interaktivní vývojového prostředí (IDE) sady Visual Studio a pro C# a projekty Visual Basic, na příkazovém řádku.

Kromě toho můžete nainstalovat [balíček NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) , který obsahuje čtyři metriky kódu [analyzátor](roslyn-analyzers-overview.md) pravidla: CA1501, CA1502, CA1505 a CA1506. Tato pravidla jsou ve výchozím nastavení zakázané, ale můžete povolit jim **Průzkumníku řešení** nebo [sada pravidel, která](using-rule-sets-to-group-code-analysis-rules.md) souboru.

## <a name="visual-studio-ide-code-metrics"></a>Visual Studio IDE metriky kódu

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generování výsledků metrik kódu pro celé řešení

Výsledky metrik kódu pro celé řešení lze vytvořit v některém z následujících způsobů:

- Na panelu nabídek zvolte **analyzovat** > **vypočítat metriky kódu** > **pro řešení**.

- V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a klikněte na tlačítko **vypočítat metriky kódu**.

- V **výsledků metrik kódu** okna, vyberte **vypočítat metriky kódu pro řešení** tlačítko.

Výsledky jsou generovány a **výsledků metrik kódu** se zobrazí okno. Chcete-li zobrazit detaily výsledků, rozbalte stromovou strukturu v **hierarchie** sloupce.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generování výsledků metrik kódu pro jeden nebo více projektů

1. V **Průzkumníka řešení**, vyberte jeden nebo více projektů.

1. Na panelu nabídek zvolte **analyzovat** > **vypočítat metriky kódu** > **pro vybrané projekty**.

Výsledky jsou generovány a **výsledků metrik kódu** se zobrazí okno. Chcete-li zobrazit detaily výsledků, rozbalte stromovou strukturu v **hierarchie**.

## <a name="command-line-code-metrics"></a>Metriky kódu příkazového řádku

Můžete vygenerování dat metrik kódu z příkazového řádku pro C# a projekty Visual Basic pro aplikace rozhraní .NET Framework, .NET Core a .NET Standard. Nástroje příkazového řádku kódu metriky se nazývá *Metrics.exe*.

Získat *Metrics.exe* spustitelný soubor, je nutné [generovat sami](#generate-the-executable). V blízké budoucnosti [publikované verze *Metrics.exe* bude k dispozici](https://github.com/dotnet/roslyn-analyzers/issues/1756) aby nemuseli vytvářet sami.

### <a name="generate-the-executable"></a>Generovat spustitelný soubor

Ke generování spustitelný soubor *Metrics.exe*, postupujte podle těchto kroků:

1. Klonování [dotnet /-analyzátory roslyn](https://github.com/dotnet/roslyn-analyzers) úložiště.
2. Otevřete příkazový řádek pro vývojáře pro sadu Visual Studio jako správce.
3. Z kořenové složky **analyzátory roslyn** úložiště, spusťte následující příkaz: `Restore.cmd`
4. Změňte adresář na *src\Tools*.
5. Spusťte následující příkaz k sestavení **Metrics.csproj** projektu:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Spustitelný soubor s názvem *Metrics.exe* generován *binární soubory* adresáře v kořenovém adresáři úložiště.

   > [!TIP]
   > K vytvoření *Metrics.exe* v [režim starší verze](#legacy-mode), spusťte následující příkaz:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Použití

Ke spuštění *Metrics.exe*, zadat projekt nebo řešení a výstup XML souboru jako argumenty. Příklad:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Výstup

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Nástroj rozdíly

Předchozí verze sady Visual Studio, včetně sady Visual Studio 2015, zahrnout metriky nástroj příkazového řádku kódu volá *Metrics.exe*. Tuto předchozí verzi nástroje nebylo binární analýzy, to znamená, analýzy založené na sestavení. Nový nástroj analyzuje zdrojový kód místo. Protože nová *Metrics.exe* je zdrojem založený na kódu, výsledky se liší na co je vygenerována v předchozích verzích nástroje *Metrics.exe* a integrovaného vývojového prostředí Visual Studio 2017.

Nové *Metrics.exe* nástroje můžete vypočítat metriky i v případě výskytu chyby zdrojového kódu, tak dlouho, dokud je možné načíst řešení a projektu.

#### <a name="metric-value-differences"></a>Rozdíly hodnota metriky

`LinesOfCode` Metrika je více přesným a spolehlivým na novém *Metrics.exe*. Je nezávislý na případné rozdíly codegen a nezmění, pokud se změní sadu nástrojů nebo modulu runtime. Nové *Metrics.exe* počítá skutečné řádky kódu, včetně prázdné řádky a komentáře.

Jiné metriky, jako `CyclomaticComplexity` a `MaintainabilityIndex` stejné vzorce použít jako předchozí verze *Metrics.exe*, ale nové *Metrics.exe* spočítá `IOperations` (logické zdroje pokyny) namísto instrukce (IL intermediate language). Čísla budou mírně lišit od předchozích verzí *Metrics.exe* a z výsledků metrik kódu IDE sady Visual Studio 2017.

### <a name="legacy-mode"></a>Režim starší verze

Můžete také sestavit *Metrics.exe* v *režim starší verze*. Režim starší verze nástroje generuje hodnoty metrik, které jsou blíž ke jaké starší verze generovaných nástrojem. Kromě toho v režimu starší verze *Metrics.exe* generuje metriky kódu pro stejnou sadu metoda typy, které jsou předchozí verze generovaných nástrojem metriky kódu pro. Například pro pole a vlastnosti inicializátory negeneroval dat metrik kódu. Starší režim je užitečný pro zpětnou kompatibilitu nebo pokud máte brány vrácení se změnami kódu na základě metrik kódu čísla. Příkaz k vytvoření *Metrics.exe* v režimu starší verze je:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Další informace najdete v tématu [povolit generování metriky kódu v režimu starší verze](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Viz také:

- [Použijte okno výsledků metrik kódu](../code-quality/working-with-code-metrics-data.md)
- [Hodnoty metrik kódu](../code-quality/code-metrics-values.md)