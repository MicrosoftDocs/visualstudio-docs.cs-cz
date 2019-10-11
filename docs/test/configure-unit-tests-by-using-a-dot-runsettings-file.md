---
title: Konfigurace testů jednotek pomocí souboru. runsettings
ms.date: 06/14/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4194a392eee1d5c9beaa0640f4006d1f01ebbace
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262312"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testů jednotek pomocí souboru *. runsettings*

Testy jednotek v aplikaci Visual Studio lze konfigurovat pomocí souboru *. runsettings* . Můžete například změnit verzi rozhraní .NET, na které jsou testy spuštěny, adresář pro výsledky testu nebo data, která jsou shromážděna během testovacího běhu.

Soubory parametrů běhu jsou nepovinné. Pokud nepotřebujete žádnou speciální konfiguraci, nepotřebujete soubor *. runsettings* . Běžné použití souboru *. runsettings* je přizpůsobení [analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Zadat soubor parametrů běhu

Soubory parametrů spuštění lze použít ke konfiguraci testů, které jsou spouštěny z [příkazového řádku](vstest-console-options.md), v integrovaném vývojovém prostředí (IDE) nebo v [pracovním postupu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) pomocí Azure test PLANS nebo Team Foundation Server (TFS).

### <a name="ide"></a>IDE – integrované vývojové prostředí

::: moniker range="vs-2017"

Chcete-li v integrovaném vývojovém prostředí zadat soubor parametrů spuštění, vyberte možnost **test** > **nastavení testu** > **Vyberte soubor nastavení testu**a pak vyberte soubor *. runsettings* .

![Výběr nabídky soubor nastavení testu v aplikaci Visual Studio 2017](media/select-test-settings-file.png)

Soubor se zobrazí v nabídce nastavení testu a můžete ho vybrat nebo zrušit jeho výběr. Když vyberete možnost **Analyzovat pokrytí kódu**, soubor parametrů běhu se použije vždy.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li v integrovaném vývojovém prostředí zadat soubor parametrů spuštění, vyberte možnost **Test** > **soubor nastavení**. Vyhledejte a vyberte soubor *. runsettings* .

![Výběr nabídky soubor nastavení testu v aplikaci Visual Studio 2019](media/vs-2019/select-settings-file.png)

Soubor se zobrazí v nabídce Test a můžete ho vybrat nebo zrušit jeho výběr. Když vyberete možnost **Analyzovat pokrytí kódu**, soubor parametrů běhu se použije vždy.

::: moniker-end

### <a name="command-line"></a>Příkazový řádek

Chcete-li spustit testy z příkazového řádku, použijte *VSTest. Console. exe*a zadejte soubor nastavení pomocí parametru **/Settings** .

1. Spusťte příkazový řádek pro vývojáře v sadě Visual Studio:

   ::: moniker range="vs-2017"

   V nabídce **Start** systému Windows vyberte možnost **Visual Studio 2017** > **Developer Command Prompt pro vs 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   V nabídce **Start** systému Windows vyberte možnost **Visual Studio 2019** > **Developer Command Prompt pro vs 2019**.

   ::: moniker-end

2. Zadejte příkaz podobný tomuto:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   nebo

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Další informace najdete v tématu [Možnosti příkazového řádku VSTest. Console. exe](vstest-console-options.md).

## <a name="customize-tests"></a>Přizpůsobení testů

K přizpůsobení testů pomocí souboru *. runsettings* použijte následující postup:

1. Přidejte soubor XML do řešení sady Visual Studio a uložte ho jako *test. runsettings*.

   > [!TIP]
   > Název souboru nezáleží na tom, pokud použijete příponu *. runsettings*.

2. Nahraďte obsah souboru souborem XML z následujícího příkladu a podle potřeby ho upravte.

::: moniker range="vs-2017"

3. V nabídce **test** zvolte možnost **nastavení testu** > **Vyberte soubor nastavení testu**. Přejděte k souboru *. runsettings* , který jste vytvořili, a pak vyberte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li vybrat soubor s parametry spuštění, zvolte možnost **Test** > **Vyberte soubor nastavení**. Přejděte k souboru *. runsettings* , který jste vytvořili, a pak vyberte **OK**.

::: moniker-end

   > [!TIP]
   > Ve vašem řešení můžete vytvořit více než jeden soubor *. runsettings* a podle potřeby vybrat ho jako aktivní soubor nastavení testu.

## <a name="example-runsettings-file"></a>Příklad souboru *. runsettings*

Následující kód XML ukazuje obsah typického souboru *. runsettings* . Každý prvek souboru je volitelný, protože má výchozí hodnotu.

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

## <a name="elements-of-a-runsettings-file"></a>Prvky souboru *. runsettings*

Níže uvedené části obsahují podrobnosti o prvcích souboru *. runsettings* .

### <a name="run-configuration"></a>Konfigurace spuštění

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

Element **RunConfiguration** může obsahovat následující prvky:

|Uzel|Výchozí|Hodnoty|
|-|-|-|
|**ResultsDirectory**||Adresář, ve kterém jsou umístěny výsledky testů.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` pro zdroje .NET Core `FrameworkUap10` pro zdroje založené na technologii UWP, `Framework45` pro .NET Framework 4,5 a vyšší, `Framework40` pro .NET Framework 4,0 a `Framework35` pro .NET Framework 3,5.<br /><br />Toto nastavení určuje verzi testovacího rozhraní jednotky, která se používá ke zjišťování a provádění testů. Může se lišit od verze platformy .NET, kterou jste zadali ve vlastnostech sestavení projektu testování částí.<br /><br />Vynecháte-li prvek `TargetFrameworkVersion` ze souboru *. runsettings* , platforma automaticky určí verzi rozhraní na základě sestavených binárních souborů.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Jedna nebo více cest k adresáři, kde se nachází TestAdapters|
|**MaxCpuCount**|1|Toto nastavení řídí stupeň paralelního provádění testů při spuštění testů jednotek pomocí dostupných jader v počítači. Spouštěcí modul testů začíná v každém dostupném jádru jako odlišný proces a poskytuje každému jádru kontejner s testy ke spuštění. Kontejner může být sestavením, knihovnou DLL nebo relevantním artefaktem. Kontejner testů je jednotka plánování. V každém kontejneru jsou testy spouštěny podle testovacího rozhraní. Pokud existuje mnoho kontejnerů, poté, jak procesy dokončí testy v kontejneru, získají další dostupný kontejner.<br /><br />MaxCpuCount může být:<br /><br />n, kde 1 < = n < = počet jader: spustí se až n procesů.<br /><br />n, kde n = jakákoli jiná hodnota: počet spuštěných procesů může být až na počet dostupných jader.|
|**TestSessionTimeout**||Umožňuje uživatelům ukončit relaci testu, když překročí zadaný časový limit. Nastavení časového limitu zajistí, že prostředky jsou dobře spotřebované a testovací relace jsou omezené na nastavený čas. Nastavení je k dispozici v **aplikaci Visual Studio 2017 verze 15,5** a novější.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptéry diagnostických dat (sběrače dat)

Prvek DataCollectors určuje nastavení adaptérů diagnostických dat. Adaptéry diagnostických dat shromažďují další informace o prostředí a testovaných aplikacích. Každý adaptér má výchozí nastavení a nastavení je nutné zadat pouze v případě, že nechcete použít výchozí hodnoty.

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

Kolektor dat pokrytí kódu vytvoří protokol uvádějící, které části kódu aplikace byly použity v testu. Další informace o přizpůsobení nastavení pro pokrytí kódu naleznete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Sběrač dat videa

Kolektor dat videa zachycuje záznam obrazovky při spuštění testů. Tento záznam je vhodný pro řešení potíží s testy uživatelského rozhraní. Sada video DataCollection je k dispozici v **aplikaci Visual Studio 2017 verze 15,5** a novější.

Chcete-li přizpůsobit jakýkoli jiný typ adaptérů diagnostických dat, použijte [soubor nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry testovacího běhu poskytují způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy v době běhu. Přístup k parametrům pomocí vlastnosti <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Chcete-li použít parametry testovacího běhu, přidejte do vaší třídy testu privátní pole <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> a veřejnou vlastnost <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>.

### <a name="mstest-run-settings"></a>MSTest nastavení spuštění

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

Tato nastavení jsou specifická pro testovací adaptér, který spouští testovací metody, které mají atribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.

|Konfiguraci|Výchozí|Hodnoty|
|-|-|-|
|**ForcedLegacyMode**|false|V aplikaci Visual Studio 2012 byl adaptér MSTest optimalizován, aby byl rychlejší a lépe škálovatelný. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu na **true** , pokud chcete použít starší testovací adaptér.<br /><br />Toto nastavení můžete použít například v případě, že máte zadaný soubor *App. config* pro testování částí.<br /><br />Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|
|**IgnoreTestImpact**|false|Funkce dopadu testu upřednostňuje při spuštění testů prostřednictvím adaptéru MSTest nebo nástroje Microsoft Test Manager testy, které jsou ovlivněny nedávnými změnami. Toto nastavení funkci deaktivuje. Další informace naleznete v tématu [které testy mají být spuštěny od předchozího sestavení](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Soubor nastavení testu, který se má použít s adaptérem MSTest, můžete zadat tady. Můžete také zadat soubor nastavení testu [z nabídky nastavení](#ide).<br /><br />Pokud zadáte tuto hodnotu, musíte také nastavit **položku forcedlegacymode** na **hodnotu true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po dokončení běhu testu je adaptér MSTest vypnut. Všechny procesy, které jsou spuštěny jako součást testu, jsou také ukončeny. Pokud chcete ponechat prováděcí modul testu aktivní, nastavte hodnotu na **true**. Pomocí tohoto nastavení můžete například zachovat, aby prohlížeč běžel mezi kódovanými testy uživatelského rozhraní.|
|**DeploymentEnabled**|true|Pokud nastavíte hodnotu **false**, položky nasazení, které jste určili v testovací metodě, se zkopírují do adresáře nasazení.|
|**CaptureTraceOutput**|true|Můžete zapisovat do trasování ladění z testovací metody pomocí <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Chcete-li zachovat adresář nasazení po spuštění testu, nastavte tuto hodnotu na **false**.|
|**MapInconclusiveToFailed**|false|Pokud je test dokončen s neprůkazovým stavem, je namapován na stav přeskočeno v **Průzkumníku testů**. Pokud chcete, aby se neprůkazné testy zobrazovaly jako neúspěšné, nastavte hodnotu na **true**.|
|**InProcMode**|false|Pokud chcete, aby testy běžely ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na **true**. Toto nastavení poskytuje malé zvýšení výkonu. Ale pokud se test ukončí s výjimkou, zbývající testy se nespustí.|
|**AssemblyResolution**|false|Při hledání a spouštění testů jednotek můžete zadat cesty k dalším sestavením. Například použijte tyto cesty pro sestavení závislostí, která nejsou ve stejném adresáři jako testovací sestavení. Chcete-li zadat cestu, použijte element **cesty k adresáři** . Cesty můžou zahrnovat proměnné prostředí.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Viz také:

- [Konfigurace testovacího běhu](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Úkol testu sady Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
