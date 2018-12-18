---
title: Konfigurace testů jednotek s použitím souboru .runsettings | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: gewarren
manager: douge
ms.openlocfilehash: 806c19b7132a4541ff97c253700a5e5e980ef556
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817974"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurace testů jednotek s použitím souboru .runsettings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testování částí v sadě Visual Studio můžete konfigurovat pomocí souboru *.runsettings. (Název souboru není důležité, pokud použijete rozšíření "s příponou .runsettings.") Můžete například změnit rozhraní .NET Framework, na kterém se spustí testy, adresář, kde jsou doručeny výsledky testů, a spusťte data shromážděná během testu.  
  
 Pokud nechcete provést žádnou zvláštní konfiguraci, není nutné *.runsettings souboru. Nejčastěji se vyskytujících slouží k přizpůsobení [pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
> [!NOTE]
>  **.runsettings a .testsettings**  
>   
>  Existují dva typy souboru pro konfigurace testů. *.runsettings se používají pro testování částí. A \*.testsettings pro [laboratorních prostředí testů](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), testování výkonnosti webů a zátěžové testy a pro přizpůsobení některých typů adaptérů diagnostických dat, jako jsou adaptéry Intellitrace a protokolu událostí.  
>   
>  V předchozích verzích sady Visual Studio až 2010, jednotky testů byly také přizpůsobit pomocí *.testsettings souborů. Můžete dál tak učinit, ale testy poběží pomaleji než při použití ekvivalentní konfiguraci v \*soubor s příponou .runsettings.  
  
## <a name="customizing-tests-with-a-runsettings-file"></a>Přizpůsobení testů pomocí souboru .runsettings  
  
1. Přidání souboru XML do řešení sady Visual Studio a přejmenujte jej na test.runsettings. (Název souboru není důležité, ale rozšíření musí být s příponou .runsettings.)  
  
2. Nahraďte obsah souboru [příklad](#example).  
  
    Upravte jej podle svých potřeb.  
  
3. Na **testovací** nabídce zvolte **nastavení testu**, **vybrat soubor nastavení testu**.  
  
   Můžete vytvořit více než jeden \*s příponou .runsettings souborů ve vašem řešení a povolit nebo zakázat v různých časech pomocí **nastavení testu** nabídky.  
  
   ![Povolení souboru parametrů běhu](../test/media/runsettings-1.png "RunSettings-1")  
  
##  <a name="example"></a> Zkopírování tohoto ukázkového souboru .runsettings  
 Zde je typický *.runsettings soubor. Každý prvek souboru je volitelný, protože každá hodnota má výchozí nastavení.  
  
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
  
 Soubor s příponou .runsettings slouží také ke konfiguraci [pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
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
|`TestAdaptersPaths`||Jeden nebo více cest k adresáři, kde se nachází TestAdapters|  
|`MaxCpuCount`|1|Tento ovládací prvky stupeň paralelní provádění testů při spuštění jednotky testů, pomocí dostupných jader v počítači.  Prováděcí modul testu spouští jako samostatného procesu na každém z dostupných jader a poskytuje každé jádro kontejner s testy ke spuštění, jako jsou sestavení, knihovna DLL nebo relevantní artefakt.  Jednotkou plánování je kontejnerem testu.  V jednotlivých kontejnerech spuštění testů podle rozhraní pro testování.  Pokud existuje spousta kontejnerů, pak jako zpracovává dokončení provádění testů v kontejneru, jsou uvedeny k dalšímu dostupnému kontejneru.<br /><br /> Může být MaxCpuCount:<br /><br /> n, kde 1 < = n < = počet jader: až n procesů se spustí<br /><br /> n, kde n = libovolné jiné hodnoty: počet procesů spuštěných bude až až dostupných jader v počítači|  
  
### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptéry diagnostických dat (sběrače dat)  
 `DataCollectors` Prvek určuje nastavení diagnostických dat adaptérů. Adaptéry diagnostických dat slouží k získání dalších informací o testovaném prostředí a aplikaci. Každý adaptér má výchozí nastavení a nastavení je nutné zadat, pouze pokud nechcete použít výchozí hodnoty.  
  
#### <a name="code-coverage-adapter"></a>Adaptér pokrytí kódu  
 Kolektor dat pokrytí kódu vytvoří protokol uvádějící, které části kódu aplikace byly použity v testu. Další informace o přizpůsobení nastavení pro pokrytí kódu naleznete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
#### <a name="other-diagnostic-data-adapters"></a>Další adaptéry diagnostických dat  
 Adaptér pokrytí kódu je aktuálně jediný adaptér, který lze přizpůsobit pomocí souboru parametrů běhu.  
  
 Chcete-li přizpůsobit jakýkoli jiný typ adaptéru diagnostických dat, musíte použít soubor s nastavením testu. Další informace najdete v tématu [zadání nastavení testu pro testy Visual Studia](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).  
  
#### <a name="testrunparameters"></a>TestRunParameters  
 TestRunParameters poskytuje způsob, jak definovat proměnné a hodnoty, které jsou k dispozici pro testy v době běhu.  
  
### <a name="mstest-run-settings"></a>Parametry běhu adaptéru MSTest  
 Tato nastavení jsou specifická pro testovací adaptér, který spouští testovací metody, které mají `[TestMethod]` atribut.  
  
|Konfigurace|Výchozí|Hodnoty|  
|-------------------|-------------|------------|  
|ForcedLegacyMode|false|V sadě Visual Studio 2012 byl optimalizován adaptér MSTest tak, aby byl rychlejší a lépe škálovatelný. Některé rysy chování sady, jako například pořadí, ve kterém jsou testy spuštěny, nemusí být přesně stejné jako v předchozích edicích sady Visual Studio. Nastavte tuto hodnotu `true` aby používala starší testovací adaptér.<br /><br /> Toto nastavení můžete například použít, pokud máte pro testování částí určen soubor app.config.<br /><br /> Doporučujeme zvážit refaktoring testů, aby bylo možné použít novější adaptér.|  
|IgnoreTestImpact|false|Funkce dopadu testu upřednostňuje při spuštění testů prostřednictvím adaptéru MSTest nebo nástroje Microsoft Test Manager testy, které jsou ovlivněny nedávnými změnami. Toto nastavení funkci deaktivuje. Další informace najdete v tématu [postupy: shromáždění dat k zkontrolovat, které testy mají být spuštěny po změně kódu](http://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|  
|SettingsFile||Zde můžete určit soubor s nastavením testu, který chcete použít v adaptéru MSTest. Můžete také určit soubor nastavení testu pomocí nabídky **testování**, **nastavení testu**, **vybrat soubor nastavení testu**.<br /><br /> Pokud chcete zadat tuto hodnotu, je nutné také nastavit **ForcedlegacyMode** k **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|  
|KeepExecutorAliveAfterLegacyRun|false|Po dokončení běhu testu je adaptér MSTest vypnut. Jakýkoli proces, který je spuštěn jako část testu, bude v tuto chvíli také ukončen. Pokud chcete zachovat prováděcí modul testování v provozu, přepněte tuto konfiguraci na hodnotu true.<br /><br /> Toto nastavení můžete například použít pro zachování chodu prohlížeče mezi programovými testy uživatelského rozhraní.|  
|DeploymentEnabled|true|Pokud nastavíte hodnotu false, nezkopírují se položky nasazení, které jste určili v testovací metodě, do adresáře nasazení.|  
|CaptureTraceOutput|true|Pomocí příkazu Trace.WriteLine můžete zapisovat do trasování ladění z testovací metody. Pomocí této konfigurace můžete vypnout tato trasování ladění.|  
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Nastavením této hodnoty na false můžete po testovacím běhu zachovat adresář nasazení.|  
|MapInconclusiveToFailed|false|Pokud se test vrátí v neprůkazném stavu, je obvykle v aplikaci Průzkumník testů mapován na stav Vynecháno. Pokud chcete, aby se neprůkazné testy zobrazovaly ve stavu Selhalo, je třeba použít tuto konfiguraci.|  
|InProcMode|false|Pokud chcete testy spouštět ve stejném procesu jako adaptér MSTest, nastavte tuto hodnotu na true. Toto nastavení poskytuje malé zvýšení výkonu. Pokud je však test ukončen výjimkou, nebudou ostatní testy pokračovat.|  
|AssemblyResolution|false|Při hledání a spouštění testů jednotek, můžete určit cest na další sestavení.  Například pomocí těchto cest pro závislosti sestavení, která není se nacházejí ve stejném adresáři jako testovací sestavení.  Pokud chcete zadat cestu, použijte prvek "Cesta k adresáři".  Cesty mohou obsahovat proměnné prostředí.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md)   
 [Zadání nastavení testu pro testy Visual Studia](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)



