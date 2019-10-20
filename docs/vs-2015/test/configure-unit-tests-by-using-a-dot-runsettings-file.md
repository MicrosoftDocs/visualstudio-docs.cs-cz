---
title: Konfigurace testů jednotek pomocí souboru. runsettings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9779dd685ad662cd0761dc85be58d0dbb3ccf0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660659"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testování částí s použitím souboru .runsettings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednotek v aplikaci Visual Studio lze konfigurovat pomocí souboru *. runsettings. (Název souboru nezáleží na tom, že použijete rozšíření. runsettings. ') Můžete například změnit .NET Framework, na které budou testy spuštěny, adresář, kde jsou doručeny výsledky testů, a data shromážděná během testovacího běhu.

 Pokud nechcete provádět žádné zvláštní konfigurace, nepotřebujete soubor *. runsettings. Nejčastěji se využívá k přizpůsobení [pokrytí kódu](../test/customizing-code-coverage-analysis.md).

> [!NOTE]
> **. runsettings a. testsettings**
>
> Existují dva typy souborů pro konfiguraci testů. *. runsettings se používá pro testování částí. A \*. testsettings pro [testy testovacího prostředí](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), webový výkon a zátěžové testy a pro přizpůsobení některých typů adaptérů diagnostických dat, jako jsou IntelliTrace a adaptéry protokolu událostí.
>
> V předchozích edicích sady Visual Studio až 2010 byly testy jednotek také přizpůsobené pomocí souborů *. testsettings. Pořád to můžete udělat, ale testy budou pomalejší než při použití ekvivalentních konfigurací v souboru \*. runsettings.

## <a name="customizing-tests-with-a-runsettings-file"></a>Přizpůsobení testů pomocí souboru .runsettings

1. Přidejte soubor XML do řešení sady Visual Studio a přejmenujte ho na test. runsettings. (Název souboru nezáleží, ale přípona musí být. runsettings.)

2. Nahraďte obsah souboru [příkladem](#example).

    Upravte jej podle svých potřeb.

3. V nabídce **test** zvolte možnost **nastavení testu**, **Vybrat soubor s nastavením testu**.

   Ve vašem řešení můžete vytvořit více souborů \*. runsettings a povolit je nebo zakázat v různých časech pomocí nabídky **nastavení testu** .

   ![Povolení souboru parametrů běhu](../test/media/runsettings-1.png "RunSettings-1")

## <a name="example"></a>Zkopírujte tento příklad souboru. runsettings
 Tady je typický soubor *. runsettings. Každý prvek souboru je volitelný, protože každá hodnota má výchozí nastavení.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- [x86] | x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
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

 Soubor. runsettings slouží také ke konfiguraci [pokrytí kódu](../test/customizing-code-coverage-analysis.md).

 Zbývající část tohoto tématu popisuje obsah souboru.

## <a name="edit-your-runsettings-file"></a>Úprava souboru .runsettings
 Soubor .runsettings obsahuje následující prvky.

### <a name="test-run-configuration"></a>Konfigurace testovacího běhu

|Uzel|Výchozí|Hodnoty|
|----------|-------------|------------|
|`ResultsDirectory`||Adresář, kde budou umístěny výsledky testů.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Toto určuje, která verze rozhraní pro testování částí slouží k zjištění a provedení testů. Může se lišit od verze platformy .NET, kterou jste zadali ve vlastnostech sestavení projektu testování částí.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|false|false, true|
|`TestAdaptersPaths`||Jedna nebo více cest k adresáři, kde se nachází TestAdapters|
|`MaxCpuCount`|první|Tato kontrola určuje stupeň paralelního provádění testů při spuštění testů jednotek pomocí dostupných jader v počítači.  Spouštěcí modul testů se spouští jako samostatný proces na každém dostupném jádru a poskytuje každému jádru kontejner s testy ke spuštění, jako je sestavení, knihovna DLL nebo relevantní artefakt.  Kontejner testů je jednotka plánování.  V každém kontejneru jsou testy spouštěny podle testovacího rozhraní.  Pokud existuje mnoho kontejnerů, poté, jak procesy dokončí testy v kontejneru, získají další dostupný kontejner.<br /><br /> MaxCpuCount může být:<br /><br /> n, kde 1 < = n < = počet jader: spustí se až n procesů.<br /><br /> n, kde n = jakákoli jiná hodnota: počet spuštěných procesů bude až do dostupných jader v počítači až do počtu, který je k dispozici.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptéry diagnostických dat (sběrače dat)
 Element `DataCollectors` určuje nastavení adaptérů diagnostických dat. Adaptéry diagnostických dat slouží k získání dalších informací o testovaném prostředí a aplikaci. Každý adaptér má výchozí nastavení a nastavení je nutné zadat, pouze pokud nechcete použít výchozí hodnoty.

#### <a name="code-coverage-adapter"></a>Adaptér pokrytí kódu
 Kolektor dat pokrytí kódu vytvoří protokol uvádějící, které části kódu aplikace byly použity v testu. Další informace o přizpůsobení nastavení pro pokrytí kódu naleznete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

#### <a name="other-diagnostic-data-adapters"></a>Další adaptéry diagnostických dat
 Adaptér pokrytí kódu je aktuálně jediný adaptér, který lze přizpůsobit pomocí souboru parametrů běhu.

 Chcete-li přizpůsobit jakýkoli jiný typ adaptéru diagnostických dat, musíte použít soubor s nastavením testu. Další informace naleznete v tématu [Určení nastavení testu pro testy sady Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).

#### <a name="testrunparameters"></a>TestRunParameters
 TestRunParameters poskytuje způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy za běhu.

### <a name="mstest-run-settings"></a>Parametry běhu adaptéru MSTest
 Tato nastavení jsou specifická pro testovací adaptér, který spouští testovací metody, které mají atribut `[TestMethod]`.

|Konfigurace|Výchozí|Hodnoty|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|V sadě Visual Studio 2012 byl optimalizován adaptér MSTest tak, aby byl rychlejší a lépe škálovatelný. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu `true`, aby používala starší testovací adaptér.<br /><br /> Toto nastavení můžete například použít, pokud máte pro testování částí určen soubor app.config.<br /><br /> Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|
|IgnoreTestImpact|false|Funkce dopadu testu upřednostňuje při spuštění testů prostřednictvím adaptéru MSTest nebo nástroje Microsoft Test Manager testy, které jsou ovlivněny nedávnými změnami. Toto nastavení funkci deaktivuje. Další informace naleznete v tématu [Postupy: shromáždění dat pro kontrolu, které testy mají být spuštěny po změně kódu](https://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Zde můžete určit soubor s nastavením testu, který chcete použít v adaptéru MSTest. Můžete také zadat soubor nastavení testu pomocí nabídky **test**, **nastavení testu**, **Vybrat soubor s nastavením testu**.<br /><br /> Pokud zadáte tuto hodnotu, musíte také nastavit **položku forcedlegacymode** na **hodnotu true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|Po dokončení běhu testu je adaptér MSTest vypnut. Jakýkoli proces, který je spuštěn jako část testu, bude v tuto chvíli také ukončen. Pokud chcete zachovat prováděcí modul testování v provozu, přepněte tuto konfiguraci na hodnotu true.<br /><br /> Toto nastavení můžete například použít pro zachování chodu prohlížeče mezi programovými testy uživatelského rozhraní.|
|DeploymentEnabled|true|Pokud nastavíte hodnotu false, nezkopírují se položky nasazení, které jste určili v testovací metodě, do adresáře nasazení.|
|CaptureTraceOutput|true|Pomocí příkazu Trace.WriteLine můžete zapisovat do trasování ladění z testovací metody. Pomocí této konfigurace můžete vypnout tato trasování ladění.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Nastavením této hodnoty na false můžete po testovacím běhu zachovat adresář nasazení.|
|MapInconclusiveToFailed|false|Pokud se test vrátí v neprůkazném stavu, je obvykle v aplikaci Průzkumník testů mapován na stav Vynecháno. Pokud chcete, aby se neprůkazné testy zobrazovaly ve stavu Selhalo, je třeba použít tuto konfiguraci.|
|InProcMode|false|Pokud chcete testy spouštět ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na true. Toto nastavení poskytuje malé zvýšení výkonu. Pokud je však test ukončen výjimkou, nebudou ostatní testy pokračovat.|
|AssemblyResolution|false|Při hledání a spouštění testů jednotek můžete zadat cesty k dalším sestavením.  Například použijte tyto cesty pro sestavení závislostí, která se nenacházejí ve stejném adresáři jako testovací sestavení.  Chcete-li zadat cestu, použijte element cesta k adresáři.  Cesty můžou obsahovat proměnné prostředí.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Viz také
 [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md) [Určení nastavení testu pro testy sady Visual Studio](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
