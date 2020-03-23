---
title: Nejčastější dotazy k funkci Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591538"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Nejčastější dotazy týkající se testování živých částí

## <a name="supported-frameworks"></a>Podporované architektury

**Jaké testovací architektury podporují testování živých částí a jaké jsou minimální podporované verze?**

Živé testování částí pracuje se třemi oblíbenými rozhraními pro testování částí uvedenými v následující tabulce. Minimální podporovaná verze jejich adaptérů a architektur je také uvedena v tabulce. Testování částí rámce jsou k dispozici od NuGet.org.

|Testovací rámec  |Minimální verze adaptéru Visual Studio  |Minimální verze rozhraní Framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio verze 2.2.0-beta3-build1187 |xjednotka 1,9,2 |
|NJednotka |NUnit3TestAdaptér verze 3.7.0 |NUnit verze 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší testovací projekty založené `Microsoft.VisualStudio.QualityTools.UnitTestFramework` na MSTest, které odkazují a nechcete přejít na novější balíčky MSTest NuGet, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech budete muset explicitně obnovit Balíčky NuGet odkazuje projekty v řešení, aby pro živé testování částí fungovat. Balíčky můžete obnovit buď provedením explicitní sestavení řešení (vyberte **sestavení** > **znovu sestavit řešení** z nabídky visual studio nejvyšší úrovně), nebo kliknutím pravým tlačítkem myši na řešení a výběrem obnovit **nuget balíčky** před povolením testování živé jednotky.

## <a name="net-core-support"></a>Podpora jádra .NET

**Funguje živé testování částí s jádrem .NET?**

Ano. Živé testování částí pracuje s rozhraním .NET Core a rozhraním .NET Framework.

## <a name="configuration"></a>Konfigurace

**Proč živé testování částí nefunguje, když ho zapnu?**

Okno Výstup (pokud je vybrána rozevírací nabídka Testování živých částí) by vám mělo sdělit, proč živé testování částí nefunguje. Testování živých částí nemusí fungovat z jednoho z následujících důvodů:

- Pokud balíčky NuGet odkazuje projekty v řešení nebyly obnoveny, živé testování částí nebude fungovat. Provádění explicitní sestavení řešení nebo obnovení nuget balíčky v řešení před zapnutím live testování částí by měl vyřešit tento problém.

- Pokud používáte testy založené na MSTest v projektech, ujistěte se, že odebrat odkaz na aplikaci `Microsoft.VisualStudio.QualityTools.UnitTestFramework`a přidat odkazy na nejnovější balíčky MSTest NuGet `MSTest.TestAdapter` (minimální verze 1.1.11 je vyžadována) a `MSTest.TestFramework` (minimální verze 1.1.11 je vyžadována). Další informace naleznete v části "Podporované testovací architektury" v článku [Použití živého testování částí v sadě Visual Studio.](live-unit-testing.md#supported-test-frameworks)

- Alespoň jeden projekt ve vašem řešení by měl mít buď Odkaz NuGet nebo přímý odkaz na xUnit, NUnit nebo MSTest testovací ho rámce. Tento projekt by měl také odkazovat na odpovídající visual studio testovací adaptéry NuGet balíček. Na testovací adaptér sady Visual Studio lze také odkazovat prostřednictvím souboru *.runsettings.* Soubor *.runsettings* musí mít položku jako následující příklad:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nesprávné pokrytí po upgradu

**Proč živé testování částí zobrazit nesprávné pokrytí po upgradu testovací adaptér odkazuje ve vašem Visual Studio projekty na podporovanou verzi?**

- Pokud více projektů v řešení odkaz na balíček testovací adaptér NuGet, každý z nich musí být upgradovány na podporovanou verzi.

- Ujistěte se, že soubor MSBuild *.props* importovaný z balíčku testovacího adaptéru je také správně aktualizován. Zkontrolujte verzi balíčku NuGet nebo cestu importu, který se obvykle nachází v horní části souboru projektu, například následující:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Přizpůsobení sestavení

**Mohu přizpůsobit svá sestavení testování živých částí?**

Pokud vaše řešení vyžaduje vlastní kroky k sestavení pro instrumentaci (Live Testování částí), které nejsou vyžadovány pro "pravidelné" neinstrumentované `BuildingForLiveUnitTesting` sestavení, pak můžete přidat kód do projektu nebo *.targets* soubory, které kontroluje vlastnost a provádí vlastní před a post sestavení kroky. Můžete také odebrat určité kroky sestavení (jako je publikování nebo generování balíčků) nebo přidat kroky sestavení (jako je kopírování požadavků) do sestavení živého testování částí na základě této vlastnosti projektu. Přizpůsobení sestavení na základě této vlastnosti žádným způsobem nezmění vaše pravidelné sestavení a má vliv pouze na sestavení živého testování částí.

Například může být cíl, který vytváří Balíčky NuGet během pravidelné sestavení. Pravděpodobně nechcete, aby byly balíčky NuGet generovány po každé úpravě, kterou provedete. Takže můžete zakázat tento cíl v sestavení live testování částí tím, že uděláte něco jako následující:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Chybové \<zprávy s \<OutputPath>, OutDir> nebo \<IntermediateOutputPath>

**Proč se zobrazuje následující chyba, když se živé testování částí pokusí vytvořit mé řešení: "... bezpodmínečně nastaveny `<OutputPath>` `<OutDir>`nebo . Živé testování částí neprovede testy z výstupního sestavení"?**

Tuto chybu můžete získat, pokud proces sestavení pro vaše řešení má vlastní logiku, která určuje, kde by měly být generovány binární soubory. Ve výchozím nastavení závisí umístění `<OutputPath>`binárních souborů na `<OutDir>` , nebo `<IntermediateOutputPath>` také `<BaseOutputPath>` na aplikaci nebo `<BaseIntermediateOutputPath>`.

Živé testování částí přepíše tyto proměnné, aby bylo zajištěno, že artefakty sestavení jsou vynechány do složky artefaktů živého testování částí a nezdaří se, pokud proces sestavení také přepíše tyto proměnné.

Existují dva hlavní přístupy k úspěšnému sestavení živého testování částí. Pro snadnější konfigurace sestavení můžete výstupní cesty `<BaseIntermediateOutputPath>`založit na . Pro složitější konfigurace můžete založit výstupní `<LiveUnitTestingBuildRootPath>`cesty na .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Přepsání `<OutputPath>` / `<IntermediateOutputPath>` podmíněně `<BaseOutputPath>` / `<BaseIntermediateOutputPath>`na základě .

> [!NOTE]
> Chcete-li použít tento přístup, každý projekt musí být schopen vytvářet nezávisle na sobě. Nemají jeden odkaz na projekt artefakty z jiného projektu během sestavení. Nemají jeden projekt dynamicky načíst sestavení z jiného projektu `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`za běhu (například volání).

Během sestavení live testování částí `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` automaticky přepíše proměnné cílit na složku artefakty živé testování částí.

Pokud například sestavení přepíše <OutputPath> následující postup:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

pak jej můžete nahradit následujícím XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Tím je `<OutputPath>` zajištěno, `<BaseOutputPath>` že leží ve složce.

Nepřepište `<OutDir>` přímo v procesu sestavení; přepište `<OutputPath>` místo toho přetažení artefakty sestavení do určitého umístění.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Přepsání vlastností `<LiveUnitTestingBuildRootPath>` na základě vlastnosti.

> [!NOTE]
> V tomto přístupu je třeba dávat pozor na soubory přidané do složky artefakty, které nejsou generovány během sestavení. Následující příklad ukazuje, co dělat při umísťování složky balíčků pod artefakty. Vzhledem k tomu, že obsah této složky nejsou generovány během sestavení, msbuild vlastnost **by neměla být změněna**.

Během sestavení živé testování `<LiveUnitTestingBuildRootPath>` částí je vlastnost nastavena na umístění složky artefaktů testování živých částí.

Předpokládejme například, že projekt má strukturu zobrazenou zde.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Během sestavení živé testování `<LiveUnitTestingBuildRootPath>` částí je vlastnost nastavena `.vs\...\lut\0\b`na úplnou cestu . Pokud projekt definuje `<ArtifactsRoot>` vlastnost, která se mapuje na dir řešení, můžete aktualizovat projekt MSBuild následujícím způsobem:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Umístění artefaktů sestavení

**Chci, aby artefakty sestavení živého testování částí přecčovalo do určitého umístění namísto výchozího umístění ve složce *.vs.* Jak to můžu změnit?**

Nastavte `LiveUnitTesting_BuildRoot` proměnnou prostředí na úrovni uživatele na cestu, kde chcete, aby artefakty sestavení živého testování částí byly vynechány. 

## <a name="test-explorer-versus-live-unit-testing"></a>Test Explorer versus živé testování částí

**Jak se spouštění testů z okna Průzkumníka testů liší od spuštění testů v testování živých částí?**

Existuje několik rozdílů:

- Spuštění nebo ladění testů z okna **Průzkumníka testů** spouští pravidelné binární soubory, zatímco živé testování částí spouští instrumentované binární soubory. Pokud chcete ladit instrumentované binární soubory, přidání [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) volání metody ve vaší testovací metody způsobí, že ladicí program spustit vždy, když je tato metoda spuštěna (včetně při spuštění live testování částí) a pak můžete připojit a ladit instrumentovaný binární. Doufáme však, že instrumentace je pro vás transparentní pro většinu uživatelských scénářů a že není nutné ladit instrumentované binární soubory.

- Živé testování částí nevytvoří novou doménu aplikace pro spuštění testů, ale testy spustit z okna **Průzkumníktestů** vytvořit novou doménu aplikace.

- Testování živých částí spustí testy v každé testovací sestavení postupně. V **Průzkumníkovi testů**můžete spustit více testů paralelně.

- **Průzkumník testů** spustí testy v bytě s jedním podprocesem (STA) ve výchozím nastavení, zatímco živé testování částí spustí testy v bytě s více vlákny (MTA). Chcete-li spustit testy MSTest v STA v živé testování částí, `<STATestMethod>` `<STATestClass>` ozdobte testovací metodu `MSTest.STAExtensions 1.0.3-beta` nebo obsahující třídu s atributem nebo, který lze nalézt v balíčku NuGet. Pro NUnit, ozdobte testovací `<RequiresThread(ApartmentState.STA)>` metodu s atributem `<STAFact>` a pro xUnit s atributem.

## <a name="exclude-tests"></a>Vyloučit testy

**Jak vyloučím testy z účasti na testování živých částí?**

Naleznete v části "Zahrnout a vyloučit testovací projekty a testovací metody" [použití živé testování částí v sadě Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) pro nastavení specifické pro uživatele. Zahrnutí nebo vyloučení testů je užitečné, pokud chcete spustit určitou sadu testů pro konkrétní relaci úprav nebo zachovat své vlastní osobní předvolby.

Pro nastavení specifické pro řešení <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> můžete použít atribut programově vyloučit metody, vlastnosti, třídy nebo struktury z instrumentace live testování částí. Kromě toho můžete také `<ExcludeFromCodeCoverage>` nastavit `true` vlastnost v souboru projektu vyloučit celý projekt z instrumentace. Živé testování částí bude stále spouštět testy, které nebyly instrumentovány, ale jejich pokrytí nebude vizualizováno.

Můžete také zkontrolovat, zda `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` je načten v aktuální doméně aplikace a zakázat testy na základě proč. Například můžete udělat něco jako následující s xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Win32 PE záhlaví

**Proč se záhlaví win32 PE liší v instrumentovaných sestaveních vytvořených testováním živých jednotek?**

Tento problém je vyřešen a neexistuje ve Visual Studio 2017 verze 15.3 a novější.

Pro starší verze Sady Visual Studio 2017 je známá chyba, která může mít za následek live testování částí sestavení nepodaří vložit následující win32 PE záhlaví dat:

- Verze souboru @System.Reflection.AssemblyFileVersionAttribute (určená v kódu).

- Ikona Win32 (určená `/win32icon:` na příkazovém řádku).

- Manifest win32 (určený `/win32manifest:` na příkazovém řádku).

Testy, které spoléhají na tyto hodnoty může selhat při spuštění testování live jednotky.

::: moniker-end

## <a name="continuous-builds"></a>Kontinuální sestavení

**Proč live unit testování neustále buduje mé řešení, i když neprovádím žádné úpravy?**

Vaše řešení můžete sestavit i v případě, že neprovádíte úpravy, pokud proces sestavení generuje zdrojový kód, který je součástí samotného řešení, a cílové soubory sestavení nemají zadané příslušné vstupy a výstupy. Cíle by měl y mít seznam vstupů a výstupů, aby msbuild mohl provádět příslušné aktuální kontroly a určit, zda je vyžadováno nové sestavení.

Živé testování částí spustí sestavení vždy, když zjistí, že se změnily zdrojové soubory. Vzhledem k tomu, že sestavení vašeho řešení generuje zdrojové soubory, live testování částí se dostane do nekonečné smyčky sestavení. Pokud však vstupy a výstupy cíle jsou kontrolovány při live testování částí spustí druhé sestavení (po zjištění nově generované zdrojové soubory z předchozího sestavení), vypukne ze smyčky sestavení, protože kontroly vstupů a výstupů označují, že vše je aktuální.

## <a name="editor-icons"></a>Ikony editoru

**Proč nevidím žádné ikony v editoru, i když live testování částí se zdá být spuštěntesty na základě zpráv v okně Výstup?**

Nemusí se zobrazit ikony v editoru, pokud sestavení, které live testování částí pracuje na nejsou instrumentovány z jakéhokoli důvodu. Například živé testování částí není kompatibilní `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`s projekty, které nastavují . V takovém případě je třeba aktualizovat proces sestavení, aby bylo `true` toto nastavení buď odebrání nebo jeho změna, aby fungovalo testování živých částí. 

## <a name="capture-logs"></a>Protokoly zachycení

**Jak lze shromažďovat podrobnější protokoly pro hlášení o chybách?**

Můžete provést několik věcí shromažďovat podrobnější protokoly:

- Přejděte na**možnosti** >  **nástrojů** > **živé testování částí** a změňte možnost protokolování na **Verbose**. Podrobné protokolování způsobí podrobnější protokoly, které mají být zobrazeny v okně **Výstup.**

- Nastavte `LiveUnitTesting_BuildLog` proměnnou uživatelského prostředí na název souboru, který chcete použít k zachycení protokolu MSBuild. Podrobné zprávy protokolu MSBuild z sestavení živého testování částí lze pak načíst z tohoto souboru.

- Nastavte `LiveUnitTesting_TestPlatformLog` proměnnou uživatelského prostředí tak, aby `1` zachycovalo protokol testovací platformy. Podrobné zprávy protokolu testovací platformy z živých `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`testování částí lze potom načíst z aplikace .

- Vytvořte proměnnou prostředí `VS_UTE_DIAGNOSTICS` na úrovni uživatele s názvem a nastavte ji na hodnotu 1 (nebo libovolnou hodnotu) a restartujte sadu Visual Studio. Nyní byste měli vidět velké množství protokolování na **kartě Výstup – testy** v sadě Visual Studio.

## <a name="see-also"></a>Viz také

- [Testování živých částí](live-unit-testing.md)
