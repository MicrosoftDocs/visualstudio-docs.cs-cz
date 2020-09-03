---
title: Konfigurace testů jednotek pomocí souboru. runsettings
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f638d60b7bd4416bb7a19cc960cac1159c755ab3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972293"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testů jednotek pomocí souboru *. runsettings*

Testy jednotek v aplikaci Visual Studio lze konfigurovat pomocí souboru *. runsettings* . Můžete například změnit verzi rozhraní .NET, na které jsou testy spuštěny, adresář pro výsledky testu nebo data, která jsou shromážděna během testovacího běhu. Běžné použití souboru *. runsettings* je přizpůsobení [analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

Soubory parametrů spuštění lze použít ke konfiguraci testů, které jsou spouštěny z [příkazového řádku](vstest-console-options.md), z rozhraní IDE nebo v [pracovním postupu sestavení](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) pomocí Azure test PLANS nebo Team Foundation Server (TFS).

Soubory parametrů běhu jsou nepovinné. Pokud nepotřebujete žádnou speciální konfiguraci, nepotřebujete soubor *. runsettings* .

## <a name="create-a-run-settings-file-and-customize-it"></a>Vytvoření souboru parametrů běhu a jeho přizpůsobení

1. Přidejte do svého řešení soubor s parametry spuštění. V **Průzkumník řešení**v místní nabídce řešení zvolte možnost **Přidat**  >  **novou položku**a vyberte **soubor XML**. Uložte soubor s názvem, například *test. runsettings*.

   > [!TIP]
   > Název souboru nezáleží na tom, pokud použijete příponu *. runsettings*.

2. Přidejte obsah z [příkladu soubor *. runsettings](#example-runsettings-file)a pak ho Přizpůsobte podle svých potřeb, jak je popsáno v následujících částech.

3. Zadejte soubor *. runsettings, který chcete použít, pomocí jedné z následujících metod:

   - [Integrované vývojové prostředí sady Visual Studio](#specify-a-run-settings-file-in-the-ide)
   - [Příkazový řádek](#specify-a-run-settings-file-from-the-command-line)
   - [Sestavujte pracovní postup](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) pomocí Azure Test Plans nebo Team Foundation Server (TFS).

4. Spusťte testy jednotek a použijte vlastní nastavení spuštění.

::: moniker range="vs-2017"

Pokud chcete vlastní nastavení vypnout a zapnout v integrovaném vývojovém prostředí, zrušte výběr nebo vyberte soubor v nabídce nastavení **testu testu** > **Test Settings** .

![Nabídka nastavení testu se souborem vlastního nastavení v aplikaci Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete vlastní nastavení vypnout a zapnout v integrovaném vývojovém prostředí, zrušte výběr nebo vyberte soubor v nabídce **test** .

::: moniker-end

> [!TIP]
> Ve vašem řešení můžete vytvořit více než jeden soubor *. runsettings* a podle potřeby vybrat ho jako aktivní soubor nastavení testu.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Zadejte soubor parametrů běhu v integrovaném vývojovém prostředí (IDE)

Dostupné metody závisí na vaší verzi sady Visual Studio.

::: moniker range="vs-2017"
Chcete-li zadat soubor parametrů běhu v rozhraní IDE, vyberte možnost **test** > **Nastavení** testu > **Vybrat soubor nastavení testu**a pak vyberte soubor *. runsettings* .

![Výběr nabídky soubor nastavení testu v aplikaci Visual Studio 2017](media/select-test-settings-file.png)

Soubor se zobrazí v nabídce nastavení testu a můžete ho vybrat nebo zrušit jeho výběr. Když vyberete možnost **Analyzovat pokrytí kódu**, soubor parametrů běhu se použije vždy.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 verze 16,4 a novější

Existují tři způsoby určení souboru parametrů běhu v aplikaci Visual Studio 2019 verze 16,4 a novější.

- [Automatické rozpoznávání parametrů spuštění](#autodetect-the-run-settings-file)
- [Ruční nastavení parametrů spuštění](#manually-select-the-run-settings-file)
- [Nastavení vlastnosti buildu](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Automaticky rozpoznat soubor parametrů běhu

Pokud chcete automaticky detekovat soubor s parametry spuštění, umístěte ho do kořenového adresáře vašeho řešení.

Pokud je povoleno automatické zjišťování souborů parametrů běhu, nastavení v tomto souboru se aplikují ve všech testech běhu. Automatickou detekci souborů runsettings můžete zapnout pomocí dvou metod:
  
- Výběr **nástrojů** > **Možnosti** > **test** > **Automatické rozpoznávání souborů runsettings**

   ![Možnost automaticky rozpoznat soubor runsettings v aplikaci Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
- Vyberte **test** > **Konfigurace parametrů spuštění** > **automaticky rozpoznat soubory runsettings** .
    
   ![Nabídka souboru automatické detekce runsettings v aplikaci Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Ručně vybrat soubor parametrů běhu

V integrovaném vývojovém prostředí vyberte **test** > **Konfigurovat nastavení spuštění** > **Vyberte runsettings soubor řešení**a pak vyberte soubor *. runsettings* .

   - Tento soubor přepíše soubor *. runsettings* v kořenovém adresáři řešení, pokud je k dispozici a je použit pro všechny testy, které jsou spuštěny.  
   - Tento výběr souboru se zachovává jenom místně.

![V aplikaci Visual Studio 2019 vyberte nabídku souboru runsettings pro všechny testovací řešení.](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Nastavení vlastnosti buildu

Přidejte do projektu vlastnost sestavení v souboru projektu nebo v souboru. Build. props. Soubor parametrů běhu pro projekt je určen vlastností **RunSettingsFilePath**.

- V projektech C#, VB, C++ a F # se aktuálně podporují nastavení běhu na úrovni projektu.
- Soubor zadaný pro projekt přepíše jakékoli jiné soubory parametrů spuštění, které jsou zadány v řešení.
- [Tyto vlastnosti nástroje MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) lze použít k určení cesty k souboru runsettings. 

Příklad zadání souboru *. runsettings* pro projekt:
    
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 verze 16,3 a starší

Chcete-li zadat soubor parametrů běhu v rozhraní IDE, vyberte možnost **test**  >  **Vybrat soubor nastavení**. Vyhledejte a vyberte soubor *. runsettings* .

![Výběr nabídky soubor nastavení testu v aplikaci Visual Studio 2019](media/vs-2019/select-settings-file.png)

Soubor se zobrazí v nabídce Test a můžete ho vybrat nebo zrušit jeho výběr. Když vyberete možnost **Analyzovat pokrytí kódu**, soubor parametrů běhu se použije vždy.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Zadání souboru parametrů spuštění z příkazového řádku

Chcete-li spustit testy z příkazového řádku, použijte *vstest.console.exe*a zadejte soubor nastavení pomocí parametru **/Settings** .

1. Otevřete [Developer Command Prompt](/dotnet/framework/tools/developer-command-prompt-for-vs) pro Visual Studio.

2. Zadejte příkaz podobný tomuto:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   nebo

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Další informace najdete v tématu [VSTest.Console.exe možnosti příkazového řádku](vstest-console-options.md).

## <a name="the-runsettings-file"></a>Soubor *. runsettings

Soubor *. runsettings je soubor XML, který obsahuje různé prvky konfigurace v rámci elementu **runsettings** . Níže uvedené části obsahují podrobnosti o různých prvcích. Úplnou ukázku najdete v tématu [příklad souboru *. runsettings](#example-runsettings-file).

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Každá z elementů konfigurace je volitelná, protože má výchozí hodnotu.

## <a name="runconfiguration-element"></a>Element RunConfiguration

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

|Node|Výchozí|Hodnoty|
|-|-|-|
|**MaxCpuCount**|1|Toto nastavení řídí stupeň paralelního provádění testů při spuštění testů jednotek pomocí dostupných jader v počítači. Spouštěcí modul testů začíná v každém dostupném jádru jako odlišný proces a poskytuje každému jádru kontejner s testy ke spuštění. Kontejner může být sestavením, knihovnou DLL nebo relevantním artefaktem. Kontejner testů je jednotka plánování. V každém kontejneru jsou testy spouštěny podle testovacího rozhraní. Pokud existuje mnoho kontejnerů, poté, jak procesy dokončí testy v kontejneru, získají další dostupný kontejner.<br /><br />MaxCpuCount může být:<br /><br />n, kde 1 <= n <= počet jader: spustí se až n procesů.<br /><br />n, kde n = jakákoli jiná hodnota: počet spuštěných procesů může být až na počet dostupných jader. Nastavte například n = 0, aby platforma automaticky rozhodla optimální počet procesů, které se mají spustit na základě prostředí.|
|**ResultsDirectory**||Adresář, ve kterém jsou umístěny výsledky testů. Cesta je relativní vzhledem k adresáři, který obsahuje soubor. runsettings.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` pro zdroje .NET Core pro `FrameworkUap10` zdroje založené na technologii UWP, pro `Framework45` .NET Framework 4,5 a vyšší, `Framework40` pro .NET Framework 4,0 a `Framework35` pro .NET Framework 3,5.<br /><br />Toto nastavení určuje verzi testovacího rozhraní jednotky, která se používá ke zjišťování a provádění testů. Může se lišit od verze platformy .NET, kterou jste zadali ve vlastnostech sestavení projektu testování částí.<br /><br />Vynecháte `TargetFrameworkVersion` -li prvek ze souboru *. runsettings* , platforma automaticky určí verzi rozhraní na základě sestavených binárních souborů.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false (nepravda)|false, true|
|**TestAdaptersPaths**||Jedna nebo více cest k adresáři, kde se nachází TestAdapters|
|**TestSessionTimeout**||Umožňuje uživatelům ukončit relaci testu, když překročí zadaný časový limit. Nastavení časového limitu zajistí, že prostředky jsou dobře spotřebované a testovací relace jsou omezené na nastavený čas. Nastavení je k dispozici v **aplikaci Visual Studio 2017 verze 15,5** a novější.|
|**DotnetHostPath**||Zadejte vlastní cestu k hostiteli dotnet, který se používá ke spuštění testhost. To je užitečné, když vytváříte vlastní dotnet, například při sestavování úložiště dotnet/runtime. Zadání této možnosti přeskočí hledání testhost.exe a bude vždy používat testhost.dll. 

## <a name="datacollectors-element-diagnostic-data-adapters"></a>DataCollectors – element (adaptéry diagnostických dat)

Prvek **DataCollectors** DataCollectors určuje nastavení adaptérů diagnostických dat. Adaptéry diagnostických dat shromažďují další informace o prostředí a testovaných aplikacích. Každý adaptér má výchozí nastavení a nastavení je nutné zadat pouze v případě, že nechcete použít výchozí hodnoty.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Kolekce dat CodeCoverage

Kolektor dat pokrytí kódu vytvoří protokol uvádějící, které části kódu aplikace byly použity v testu. Podrobné informace o přizpůsobení nastavení pro pokrytí kódu naleznete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
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
  </CodeCoverage>
</Configuration>
```

### <a name="videorecorder-data-collector"></a>Kolekce dat VideoRecorder

Kolektor dat videa zachycuje záznam obrazovky při spuštění testů. Tento záznam je vhodný pro řešení potíží s testy uživatelského rozhraní. Sada video DataCollection je k dispozici v **aplikaci Visual Studio 2017 verze 15,5** a novější. Příklad konfigurace tohoto shromažďování dat naleznete v [souboru example *. runsettings](#example-runsettings-file).

Chcete-li přizpůsobit jakýkoli jiný typ adaptérů diagnostických dat, použijte [soubor nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Kolekce dat viny

Tato možnost vám může přispět k izolaci problematického testu, který způsobí selhání hostitele testu. Spuštění kolektoru vytvoří výstupní soubor (*Sequence.xml*) v *TestResults*, který zachycuje pořadí provádění testu před selháním. 

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Parametry testovacího běhu poskytují způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy v době běhu. Přístup k parametrům pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> vlastnosti MSTest (nebo nunit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)):

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Chcete-li použít parametry testovacího běhu, přidejte veřejnou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> vlastnost do vaší testovací třídy.

## <a name="loggerrunsettings-element"></a>Element LoggerRunSettings

`LoggerRunSettings`Oddíl definuje jeden nebo více protokolovacích nástrojů, které se mají použít pro testovací běh. Nejběžnější protokolovací nástroje jsou konzola, Visual Studio Výsledky testů soubor (TRX) a HTML.

```xml
<LoggerRunSettings>
    <Loggers>        
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>Element MSTest

Tato nastavení jsou specifická pro testovací adaptér, který spouští testovací metody, které mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut.

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

|Konfigurace|Výchozí|Hodnoty|
|-|-|-|
|**ForcedLegacyMode**|false (nepravda)|V aplikaci Visual Studio 2012 byl adaptér MSTest optimalizován, aby byl rychlejší a lépe škálovatelný. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu na **true** , pokud chcete použít starší testovací adaptér.<br /><br />Toto nastavení můžete použít například v případě, že je pro testování částí zadán soubor *app.config* .<br /><br />Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|
|**IgnoreTestImpact**|false (nepravda)|Funkce dopadu testu určuje prioritu testů, které jsou ovlivněny nedávnými změnami při spuštění v MSTest nebo z Microsoft Test Manager (zastaralé v aplikaci Visual Studio 2017). Toto nastavení funkci deaktivuje. Další informace naleznete v tématu [které testy mají být spuštěny od předchozího sestavení](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Soubor nastavení testu, který se má použít s adaptérem MSTest, můžete zadat tady. Můžete také zadat soubor nastavení testu [z nabídky nastavení](#specify-a-run-settings-file-in-the-ide).<br /><br />Pokud zadáte tuto hodnotu, musíte také nastavit **položku forcedlegacymode** na **hodnotu true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false (nepravda)|Po dokončení běhu testu je adaptér MSTest vypnut. Všechny procesy, které jsou spuštěny jako součást testu, jsou také ukončeny. Pokud chcete ponechat prováděcí modul testu aktivní, nastavte hodnotu na **true**. Pomocí tohoto nastavení můžete například zachovat, aby prohlížeč běžel mezi kódovanými testy uživatelského rozhraní.|
|**DeploymentEnabled**|true|Pokud nastavíte hodnotu **false**, položky nasazení, které jste určili v testovací metodě, se zkopírují do adresáře nasazení.|
|**CaptureTraceOutput**|true|Můžete zapisovat do trasování ladění z testovací metody pomocí <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> .|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Chcete-li zachovat adresář nasazení po spuštění testu, nastavte tuto hodnotu na **false**.|
|**MapInconclusiveToFailed**|false (nepravda)|Pokud je test dokončen s neprůkazovým stavem, je namapován na stav přeskočeno v **Průzkumníku testů**. Pokud chcete, aby se neprůkazné testy zobrazovaly jako neúspěšné, nastavte hodnotu na **true**.|
|**InProcMode**|false (nepravda)|Pokud chcete, aby testy běžely ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na **true**. Toto nastavení poskytuje malé zvýšení výkonu. Ale pokud se test ukončí s výjimkou, zbývající testy se nespustí.|
|**AssemblyResolution**|false (nepravda)|Při hledání a spouštění testů jednotek můžete zadat cesty k dalším sestavením. Například použijte tyto cesty pro sestavení závislostí, která nejsou ve stejném adresáři jako testovací sestavení. Chcete-li zadat cestu, použijte element **cesty k adresáři** . Cesty můžou zahrnovat proměnné prostředí.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Příklad souboru *. runsettings*

Následující kód XML ukazuje obsah typického souboru *. runsettings* . Zkopírujte tento kód a upravte jej tak, aby vyhovoval vašim potřebám.

Každý prvek souboru je volitelný, protože má výchozí hodnotu.

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

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>
  
  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>      
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

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

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Zadat proměnné prostředí v souboru *. runsettings*

Proměnné prostředí lze nastavit v souboru *. runsettings* , který může přímo komunikovat s testovacím hostitelem. Zadání proměnných prostředí v souboru *. runsettings* je nezbytné pro podporu projektů netriviální, které vyžadují nastavení proměnných prostředí, jako je *DOTNET_ROOT*. Tyto proměnné jsou nastaveny při vytváření procesu testovacího hostitele a jsou k dispozici na hostiteli.

### <a name="example"></a>Příklad

Následující kód je ukázkový soubor *. runsettings* , který předává proměnné prostředí:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

Uzel **RunConfiguration** by měl obsahovat uzel **EnvironmentVariables** . Proměnnou prostředí lze zadat jako název prvku a jeho hodnotu.

> [!NOTE]
> Vzhledem k tomu, že tyto proměnné prostředí by měly být vždy nastaveny při spuštění testovacího hostitele, testy by měly vždy běžet v samostatném procesu. V tomto případě se příznak */inisolation.* nastaví, když jsou proměnné prostředí, aby se testovací hostitel vždycky vyvolal.

## <a name="see-also"></a>Viz také

- [Konfigurace testovacího běhu](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Úkol testu sady Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

