---
title: Konfigurace testů jednotek pomocí souboru .runsettings
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 935c1ebfb2efd888de5b336eafab4059fa6cd443
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903553"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testů jednotek s použitím *s příponou .runsettings* souboru

Testování částí v sadě Visual Studio můžete konfigurovat pomocí *s příponou .runsettings* souboru. Například můžete změnit verzi rozhraní .NET Framework, na kterém jsou testy spuštěny, adresář pro výsledky testů nebo data, která je shromážděn v rámci testovacího běhu.

Soubory parametrů běhu jsou volitelné. Pokud nevyžadují žádnou zvláštní konfiguraci, není nutné *s příponou .runsettings* souboru. Nejběžnější použití nástroje *s příponou .runsettings* soubor je pro přizpůsobení [analýza pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Zadejte soubor parametrů běhu

Soubory můžete použít ke konfiguraci testů, které jsou spouštěny z parametrů spuštění [příkazového řádku](vstest-console-options.md), v integrovaném vývojovém prostředí nebo v [sestavení pracovního postupu](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) pomocí Azure testovací plány nebo Team Foundation Server (TFS).

### <a name="specify-a-run-settings-file-in-the-ide"></a>Zadejte soubor parametrů spuštění v integrovaném vývojovém prostředí

Vyberte **testovací** > **nastavení testu** > **vybrat soubor nastavení testu** a pak vyberte *s příponou .runsettings*souboru. Soubor se zobrazí na **nastavení testu** nabídky kde můžete vybrat nebo výběr zrušte. Po výběru souboru parametrů běhu platí vždy, když vyberete **analyzovat pokrytí kódu**.

![Vyberte nabídky Soubor nastavení testu v sadě Visual Studio](media/select-test-settings-file.png)

### <a name="specify-a-run-settings-file-at-the-command-line"></a>Zadejte soubor parametrů běhu na příkazovém řádku

Ke spuštění testů z příkazového řádku, použijte *vstest.console.exe* a zadejte soubor s nastaveními pomocí **/Settings** parametru.

1. Spusťte příkazový řádek pro vývojáře v sadě Visual Studio:

   V Windows **Start** nabídce zvolte **Visual Studio 2017** > **Developer Command Prompt for VS 2017**.

2. Zadejte příkaz podobný:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

Další informace najdete v tématu [možnosti příkazového řádku VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Přizpůsobení testů

Přizpůsobení testů pomocí *s příponou .runsettings* souborů, postupujte podle těchto kroků:

1. Přidání souboru XML do řešení sady Visual Studio a uložte ho jako *test.runsettings*.

   > [!TIP]
   > Název souboru není důležité, za předpokladu, pomocí rozšíření *s příponou .runsettings*.

1. Nahraďte obsah souboru XML z příkladu, který následuje a podle potřeby upravte.

1. Na **testovací** nabídce zvolte **nastavení testu** > **vybrat soubor nastavení testu**. Přejděte *s příponou .runsettings* souboru, kterou jste vytvořili a pak vyberte **OK**.

   > [!TIP]
   > Můžete vytvořit více než jeden *s příponou .runsettings* souborů ve vašem řešení a vyberte jednu z nich jako aktivní testovací soubor nastavení podle potřeby.

## <a name="example-runsettings-file"></a>Příklad *s příponou .runsettings* souboru

Následující kód XML zobrazuje obsah typické *s příponou .runsettings* souboru. Každý prvek souboru je volitelný, protože má výchozí hodnotu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from menu Test > Test Settings > Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
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
        <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
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

## <a name="elements-of-a-runsettings-file"></a>Prvky *s příponou .runsettings* souboru

Následující části podrobně popisují prvky *s příponou .runsettings* souboru.

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

**RunConfiguration** element může obsahovat následující prvky:

|Uzel|Výchozí|Hodnoty|
|-|-|-|
|**ResultsDirectory**||Adresář, kde jsou umístěny výsledky testů.|
|**Parametr targetFrameworkVersion**|Framework40|Framework35, Framework40, Framework45<br /><br />Toto nastavení určuje verzi rozhraní testování částí pro zjištění a provedení testů. Může se lišit od verze platformy .NET, kterou jste zadali ve vlastnostech sestavení projektu testování částí.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Jednu nebo více cest k adresáři, kde se nachází TestAdapters|
|**MaxCpuCount**|1|Tato nastavení ovládacích prvků stupeň paralelní provádění testů při spuštění testů jednotky, pomocí dostupných jader v počítači. Prováděcí modul testu spouští jako samostatného procesu na každém z dostupných jader a poskytuje každé jádro kontejner s testy ke spuštění. Kontejner může být sestavení, knihovna DLL nebo relevantní artefakt. Jednotkou plánování je kontejnerem testu. V jednotlivých kontejnerech spuštění testů podle rozhraní pro testování. Pokud existuje spousta kontejnerů, pak jako zpracovává dokončení provádění testů v kontejneru, že získá k dalšímu dostupnému kontejneru.<br /><br />Může být MaxCpuCount:<br /><br />n, kde 1 < = n < = počet jader: až n procesů vydávaných<br /><br />n, kde n = libovolné jiné hodnoty: počet procesů spuštěných může být maximálně počet dostupných jader|
|**TestSessionTimeout**||Umožňuje ukončit relaci testování, když překročí daného časového limitu. Nastavení časového limitu zajistí, že se dobře spotřebovávají prostředky a relace testování jsou omezeny na nastavenou dobu. Toto nastavení je k dispozici v **Visual Studio 2017 verze 15.5** a novější.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptéry diagnostických dat (sběrače dat)

**DataCollectors** prvek určuje nastavení diagnostických dat adaptérů. Adaptéry diagnostických dat získání dalších informací o prostředí a testovanou aplikaci. Každý adaptér má výchozí nastavení a máte jenom k poskytování nastavení, pokud nechcete použít výchozí hodnoty.

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

#### <a name="video-data-collector"></a>Kolektor dat videa

Kolekce dat video zachycuje záznam obrazovky, pokud jsou testy spuštěny. Tento záznam je užitečné při řešení potíží s testy uživatelského rozhraní. Videa data collector je k dispozici v **Visual Studio 2017 verze 15.5** a novější.

Chcete-li přizpůsobit jakýkoli jiný typ adaptéry diagnostických dat, použijte [soubor nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
</TestRunParameters>
```

Parametry testovacího běhu poskytují způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy v době běhu. Přístup k parametrům pomocí <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> vlastnost:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Pokud chcete používat parametry testovacího běhu, přidejte privátní <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pole a veřejnou <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> vlastnost do vaší testovací třídy.

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

Tato nastavení jsou specifická pro testovací adaptér, který spouští testovací metody, které mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atribut.

|Konfigurace|Výchozí|Hodnoty|
|-|-|-|
|**ForcedLegacyMode**|false|V sadě Visual Studio 2012 se k němu rychlejší a lépe škálovatelný optimalizované adaptér MSTest. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu na **true** aby používala starší testovací adaptér.<br /><br />Například můžete použít toto nastavení, pokud máte *app.config* souboru určeného pro testování částí.<br /><br />Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|
|**IgnoreTestImpact**|false|Funkce dopadu testu upřednostňuje při spuštění testů prostřednictvím adaptéru MSTest nebo nástroje Microsoft Test Manager testy, které jsou ovlivněny nedávnými změnami. Toto nastavení funkci deaktivuje. Další informace najdete v tématu [které testy je třeba spustit od předchozího sestavení](https://msdn.microsoft.com/library/dd286589).|
|**Soubor_nastavení**||Můžete určit soubor nastavení testu pro použití s zde adaptér MSTest. Můžete také určit soubor nastavení testu tak, že vyberete **testování** > **nastavení testu** > **vybrat soubor nastavení testu**.<br /><br />Pokud chcete zadat tuto hodnotu, je nutné také nastavit **ForcedlegacyMode** k **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Po dokončení běhu testu je adaptér MSTest vypnut. Jakýkoli proces, který je spuštěn jako část testu je také ukončen. Pokud chcete zachovat prováděcí modul testování aktivní, nastavte hodnotu na **true**. Toto nastavení můžete například použít pro zachování chodu mezi programové testy uživatelského rozhraní prohlížeče.|
|**DeploymentEnabled**|true|Pokud nastavíte hodnotu na **false**, položky nasazení, které jste určili v testovací metodě nejsou zkopírovány do adresáře nasazení.|
|**CaptureTraceOutput**|true|Můžete zapisovat do trasování ladění z testovací metody pomocí <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Po testovacím běhu zachovat adresář nasazení, nastavte tuto hodnotu na **false**.|
|**MapInconclusiveToFailed**|false|Pokud test skončí v neprůkazném stavu, je mapován na stav přeskočeno v **Průzkumníka testů**. Pokud chcete neprůkazné testy zobrazený jako neúspěšný, nastavte hodnotu na **true**.|
|**InProcMode**|false|Pokud chcete testy spouštět ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na **true**. Toto nastavení poskytuje malé zvýšení výkonu. Pokud však test ukončen výjimkou, zbývající testy nejsou.|
|**AssemblyResolution**|false|Při hledání a spouštění testů jednotek, můžete určit cest na další sestavení. Například pomocí těchto cest pro závislosti sestavení, které nejsou ve stejném adresáři jako testovací sestavení. Chcete-li zadat cestu, použijte **cestu k adresáři** elementu. Cesty může obsahovat proměnné prostředí.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Viz také:

- [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)
- [Testovací úloha Visual Studia (testovací plány Azure)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
