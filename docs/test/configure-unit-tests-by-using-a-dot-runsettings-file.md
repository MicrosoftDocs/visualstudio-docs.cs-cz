---
title: Konfigurace testů jednotek pomocí souboru .runsettings
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 16ba88a11acd488ba70096e0b394a734e65011f5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549913"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testů jednotek pomocí souboru *.runsettings*

Testy částí v sadě Visual Studio lze konfigurovat pomocí souboru *.runsettings.* Můžete například změnit verzi rozhraní .NET, na které jsou testy spuštěny, adresář pro výsledky testů nebo data shromážděná během testovacího běhu.

Soubory nastavení spuštění jsou volitelné. Pokud nepotřebujete žádnou speciální konfiguraci, nepotřebujete soubor *.runsettings.* Soubor *.runsettings* běžně používá k přizpůsobení [analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Určení souboru nastavení spuštění

Soubory nastavení spuštění lze použít ke konfiguraci testů, které jsou spuštěny z [příkazového řádku](vstest-console-options.md), v ide nebo v [pracovním postupu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) pomocí Azure Test Plans nebo Team Foundation Server (TFS).

### <a name="ide"></a>IDE – integrované vývojové prostředí

::: moniker range="vs-2017"

Chcete-li v prostředí IDE určit soubor nastavení spuštění, vyberte **možnost Testovat** > **nastavení** > testu **vyberte soubor nastavení testu**a pak vyberte soubor *.runsettings.*

![Výběr nabídky souboru nastavení testu v Sadě Visual Studio 2017](media/select-test-settings-file.png)

Soubor se zobrazí v nabídce Nastavení testu a můžete jej vybrat nebo zrušit. Když je tato volba vybraná, soubor nastavení spuštění se použije vždy, když vyberete **možnost Analyzovat pokrytí kódu**.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 verze 16.3 a starší

Chcete-li v prostředí IDE určit soubor nastavení spuštění, vyberte **možnost Testovat** > **soubor nastavení výběru**. Vyhledejte soubor *.runsettings* a vyberte jej.

![Výběr nabídky souboru nastavení testu v Visual Studiu 2019](media/vs-2019/select-settings-file.png)

Soubor se zobrazí v nabídce Test a můžete jej vybrat nebo odznačit. Když je tato volba vybraná, soubor nastavení spuštění se použije vždy, když vyberete **možnost Analyzovat pokrytí kódu**.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 verze 16.4 a novější

Existují tři způsoby určení souboru nastavení spuštění ve Visual Studiu 2019 verze 16.4 a novějších:

- Přidejte vlastnost sestavení do projektu prostřednictvím souboru projektu nebo souboru Directory.Build.props. Soubor nastavení spuštění projektu je určen vlastností **RunSettingsFilePath**.

    - Nastavení spuštění na úrovni projektu je aktuálně podporováno v projektech Jazyka C#, VB, C++ a F#.
    - Soubor zadaný pro projekt přepíše jakýkoli jiný soubor nastavení spuštění zadaný v řešení.
    - [Tyto vlastnosti MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) lze určit cestu k souboru runsettings. 

    Příklad zadání souboru *.runsettings* pro projekt:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Umístěte soubor nastavení spuštění s názvem ".runsettings" do kořenového adresáře řešení.

  Pokud je povolena automatická detekce souborů nastavení spuštění, nastavení v tomto souboru se použijí ve všech testech spustit. Automatické zjišťování souborů runsettings můžete zapnout ze dvou míst:
  
    - **Možnosti** > > nástroje **Test** > **Auto Detect runsettings Files** **Options**

      ![Možnost automatického zjišťování souboru runsettings v Sadě Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Testovat** > **konfigurovat automatické** > rozpoznání souborů **runsettings**
    
      ![Automatické rozpoznání nabídky souborů RunSettings v sadě Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

- V rozhraní IDE vyberte **možnost Testovat** > **konfigurovat nastavení** > spuštění **vyberte soubor nastavení celého spuštění řešení**a pak vyberte soubor *.runsettings.*

   ![V yberte v souboru Sady Visual Studio 2019 v nabídce souboru runsettings pro celé testovací řešení.](media/vs-2019/select-solution-settings-file.png)
      
   - Tento soubor přepíše soubor ".runsettings" v kořenovém adresáři řešení, pokud existuje, a je použit ve všech testech spustit.  
   - Tento výběr souborů přetrvává pouze místně. 

::: moniker-end

### <a name="command-line"></a>Příkazový řádek

Chcete-li spustit testy z příkazového řádku, použijte *vstest.console.exe*a zadejte soubor nastavení pomocí parametru **/Settings.**

1. Spusťte příkazový řádek pro vývojáře v sadě Visual Studio:

   ::: moniker range="vs-2017"

   V nabídce **Start** systému Windows zvolte **Visual Studio 2017** > **Developer Command Prompt for VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   V nabídce **Start** systému Windows zvolte **Visual Studio 2019** > **Developer Command Prompt for VS 2019**.

   ::: moniker-end

2. Zadejte příkaz podobný:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   – nebo –

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Další informace naleznete v tématu [Možnosti příkazového řádku VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Přizpůsobení testů

Chcete-li testy přizpůsobit pomocí souboru *.runsettings,* postupujte takto:

1. Přidejte soubor XML do řešení sady Visual Studio a uložte jej jako *test.runsettings*.

   > [!TIP]
   > Na názvu souboru nezáleží, pokud použijete příponu *Runsettings*.

2. Nahraďte obsah souboru xml z následujícího příkladu a podle potřeby jej přizpůsobte.

::: moniker range="vs-2017"

3. V nabídce **Test** zvolte **Nastavení testu** > **Vybrat soubor nastavení testu**. Přejděte k vytvořenému souboru *.runsettings* a vyberte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li vybrat soubor nastavení spuštění, zvolte **Testovat** > **soubor nastavení výběru**. Přejděte k vytvořenému souboru *.runsettings* a vyberte **OK**.

::: moniker-end

   > [!TIP]
   > V řešení můžete vytvořit více než jeden soubor *.runsettings* a podle potřeby vybrat jeden jako aktivní soubor nastavení testu.

## <a name="example-runsettings-file"></a>Příklad souboru *.runsettings*

Následující jazyk XML zobrazuje obsah typického souboru *.runsettings.* Každý prvek souboru je volitelný, protože má výchozí hodnotu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Prvky souboru *.runsettings*

Následující oddíly podrobně popisují prvky souboru *.runsettings.*

### <a name="run-configuration"></a>Spustit konfiguraci

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

Prvek **RunConfiguration** může obsahovat následující prvky:

|Node|Výchozí|Hodnoty|
|-|-|-|
|**Funkce Výsledky**||Adresář, kde jsou umístěny výsledky testů.|
|**Cílová verze Framework**|Framework40|`FrameworkCore10`pro základní zdroje `FrameworkUap10` .NET, pro zdroje `Framework45` založené na UPW, pro `Framework40` rozhraní .NET Framework 4.5 a vyšší, pro rozhraní .NET Framework 4.0 a `Framework35` pro rozhraní .NET Framework 3.5.<br /><br />Toto nastavení určuje verzi rozhraní testování částí, která slouží ke zjišťování a provádění testů. Může se lišit od verze platformy .NET, kterou jste zadali ve vlastnostech sestavení projektu testování částí.<br /><br />Pokud vyneche `TargetFrameworkVersion` prvek ze souboru *.runsettings,* platforma automaticky určí verzi architektury na základě vytvořených binárních souborů.|
|**Targetplatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false (nepravda)|false, true|
|**TestAdaptersPaths**||Jedna nebo více cest do adresáře, kde jsou umístěny testadapters|
|**MaxCpuCount**|1|Toto nastavení řídí stupeň paralelního provádění testů při spuštění testů částí pomocí dostupných jader v počítači. Modul provádění testu spustí jako odlišný proces na každé dostupné jádro a dává každé jádro kontejner s testy ke spuštění. Kontejner může být sestavení, DLL nebo relevantní artefakt. Testovací kontejner je plánovací jednotka. V každém kontejneru testy jsou spuštěny podle testovacího rámce. Pokud existuje mnoho kontejnerů, pak jako procesy dokončení provádění testů v kontejneru, jsou uvedeny další kontejner k dispozici.<br /><br />MaxCpuCount může být:<br /><br />n, kde 1 <= n <= počet jader: jsou spuštěny až n procesy<br /><br />n, kde n = jakákoli jiná hodnota: počet zahájených procesů může být až do počtu dostupných jader. Například nastavte n = 0, aby platforma automaticky rozhodla optimální počet procesů, které mají být spuštěny na základě prostředí.|
|**TestSessionTimeout**||Umožňuje uživatelům ukončit testovací relaci, pokud překročí daný časový limit. Nastavení časového opovce zajišťuje, že prostředky jsou dobře spotřebovány a testovací relace jsou omezeny na nastavený čas. Nastavení je k dispozici ve **Visual Studiu 2017 verze 15.5** a novější.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptéry diagnostických dat (sběrače dat)

Element **DataCollectors** určuje nastavení adaptérů diagnostických dat. Adaptéry diagnostických dat shromažďují další informace o prostředí a testovné aplikaci. Každý adaptér má výchozí nastavení a nastavení je třeba zadat pouze v případě, že nechcete používat výchozí hodnoty.

#### <a name="code-coverage-adapter"></a>Adaptér pokrytí kódu

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Kolektor dat pokrytí kódu vytvoří protokol uvádějící, které části kódu aplikace byly použity v testu. Další informace o přizpůsobení nastavení pokrytí kódu naleznete v [tématu Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Sběr dat videa

Kolektor dat videa zachytí záznam obrazovky při spuštění testů. Tento záznam je užitečný pro řešení potíží s testy ui. Kolekcí dat videa je k dispozici ve **Visual Studiu 2017 verze 15.5** a novější.

Chcete-li přizpůsobit jakýkoli jiný typ adaptérů diagnostických dat, použijte [soubor nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>Parametry testrun

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry spuštění testu poskytují způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy za běhu. Přístup k parametrům <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> pomocí vlastnosti:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Chcete-li použít parametry spuštění <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> testu, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> přidejte do testovací třídy soukromé pole a veřejnou vlastnost.

### <a name="mstest-run-settings"></a>Nastavení spuštění mstestu

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Tato nastavení jsou specifická pro testovací adaptér, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> který spouští testovací metody, které mají atribut.

|Konfigurace|Výchozí|Hodnoty|
|-|-|-|
|**ForcedLegacyMode**|false (nepravda)|V sadě Visual Studio 2012 byl adaptér MSTest optimalizován tak, aby byl rychlejší a škálovatelnější. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu na **true** pro použití staršího testovacího adaptéru.<br /><br />Toto nastavení můžete například použít, pokud máte pro testování částí zadaný soubor *app.config.*<br /><br />Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|
|**IgnoreTestImpact**|false (nepravda)|Funkce dopadu testu upřednostňuje při spuštění testů prostřednictvím adaptéru MSTest nebo nástroje Microsoft Test Manager testy, které jsou ovlivněny nedávnými změnami. Toto nastavení funkci deaktivuje. Další informace naleznete v [tématu Které testy by měly být spuštěny od předchozího sestavení](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Zde můžete zadat soubor nastavení testu, který se má použít s adaptérem MSTest. Soubor nastavení testu můžete také zadat [v nabídce nastavení](#ide).<br /><br />Pokud zadáte tuto hodnotu, musíte také nastavit **ForcedlegacyMode** na **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false (nepravda)|Po dokončení běhu testu je adaptér MSTest vypnut. Každý proces, který je spuštěn jako součást testu je také zabit. Pokud chcete zachovat zachycovač testu naživu, nastavte hodnotu na **hodnotu true**. Toto nastavení můžete například použít k zachování spuštěného prohlížeče mezi kódovými testy ui.|
|**DeploymentEnabled**|true|Pokud nastavíte hodnotu **na hodnotu false**, položky nasazení, které jste zadali v testovací metodě, nebudou zkopírovány do adresáře nasazení.|
|**CaptureTraceOutput**|true|Můžete zapisovat do ladění trasování <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>z testovací metody pomocí .|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Chcete-li zachovat adresář nasazení po spuštění testu, nastavte tuto hodnotu na **hodnotu false**.|
|**MapInconclusiveToFailed**|false (nepravda)|Pokud test dokončí s neprůkazným stavem, je mapován na stav přeskočené v **Průzkumníku testů**. Pokud chcete, aby se neprůkazné testy zobrazovali jako neúspěšné, nastavte hodnotu na **hodnotu true**.|
|**InProcMode**|false (nepravda)|Pokud chcete, aby byly testy spuštěny ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na **hodnotu true**. Toto nastavení poskytuje malé zvýšení výkonu. Ale pokud test ukončí s výjimkou, zbývající testy nespustí.|
|**Řešení sestavení**|false (nepravda)|Při hledání a spouštění testů částí můžete určit cesty k dalším sestavením. Tyto cesty můžete například použít pro sestavení závislostí, která nejsou ve stejném adresáři jako testovací sestavení. Chcete-li určit cestu, použijte prvek **Cesta k adresáři.** Cesty mohou zahrnovat proměnné prostředí.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Viz také

- [Konfigurace testovacího běhu](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Úloha testování visual studia (plány testů Azure)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

