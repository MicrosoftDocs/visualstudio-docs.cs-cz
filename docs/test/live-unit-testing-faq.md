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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591538"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing nejčastějších dotazech

## <a name="supported-frameworks"></a>Podporované architektury

**Jaké testovací architektury Live Unit Testing podporují a jaké jsou minimální podporované verze?**

Live Unit Testing pracuje se třemi oblíbenými platformami testování částí uvedenými v následující tabulce. Minimální podporovaná verze jejich adaptéry a rozhraní je také uvedený v tabulce. Rozhraní testování částí jsou všechny dostupné z webu NuGet.org.

|Rozhraní pro testování  |Minimální verze aplikace Visual Studio adaptéru  |Minimální verze rozhraní Framework  |
|---------|---------|---------|
|xUnit.net |verze 2.2.0-beta3-build1187 xunit.Runner.VisualStudio |1\.9.2 xunit |
|NUnit |NUnit3TestAdapter verze 3.7.0 |NUnit verze 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Pokud máte starší projekty testů založené na MSTest, které odkazují na `Microsoft.VisualStudio.QualityTools.UnitTestFramework` a nechcete přejít na novější MSTest balíčky NuGet, upgradujte na Visual Studio 2019 nebo Visual Studio 2017.

V některých případech budete muset explicitně obnovit balíčky NuGet odkazované projekty v řešení v pořadí pro Live Unit Testing pro práci. Balíčky můžete obnovit buď explicitním sestavením řešení (vyberte **sestavit > znovu** **Sestavit řešení** z nabídky nejvyšší úrovně), nebo kliknutím pravým tlačítkem na řešení a výběrem možnosti **obnovit balíčky NuGet** před povolením živých jednotek testování.

## <a name="net-core-support"></a>Podpora .NET Core

**Funguje Live Unit Testing s .NET Core?**

Ano. Live Unit Testing funguje s .NET Core a .NET Framework.

## <a name="configuration"></a>Konfigurace

**Proč při zapínání neLive Unit Testing pracovat?**

V okně výstup (když se vybere rozevírací seznam Live Unit Testing) by vám měl sdělit, proč Live Unit Testing nefunguje. Live Unit Testing nemusí fungovat z některého z následujících důvodů:

- Pokud balíčky NuGet odkazované projekty v řešení nebyly obnoveny, Live Unit Testing nebudou fungovat. Před zapnutím Live Unit Testing by měl tento problém vyřešit explicitní sestavení řešení nebo obnovení balíčků NuGet v řešení.

- Pokud používáte testy založené na MSTest ve vašich projektech, nezapomeňte odebrat odkaz na `Microsoft.VisualStudio.QualityTools.UnitTestFramework`a přidat odkazy na nejnovější balíčky MSTest NuGet, `MSTest.TestAdapter` (vyžaduje se minimální verze 1.1.11) a `MSTest.TestFramework` (vyžaduje se minimální verze 1.1.11). Další informace naleznete v části "podporované testovací architektury" [v článku použití Live Unit Testing v aplikaci Visual Studio](live-unit-testing.md#supported-test-frameworks) .

- Nejméně jeden projekt ve vašem řešení by měl mít buď odkaz na NuGet, nebo přímý odkaz na rozhraní xUnit, NUnit nebo MSTest test Framework. Tento projekt by měl také odkazovat na odpovídající balíček NuGet testovacích adaptérů sady Visual Studio. Na testovací adaptér sady Visual Studio lze také odkazovat pomocí souboru *. runsettings* . Soubor *. runsettings* musí mít položku podobně jako v následujícím příkladu:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nesprávné pokrytí po upgradu

**Proč Live Unit Testing po upgradu testovacího adaptéru, na který se odkazuje v projektech Visual studia na podporovanou verzi, zobrazit nesprávné pokrytí?**

- Pokud více projektů v řešení odkazuje na balíček testovacího adaptéru NuGet, každá z nich musí být upgradována na podporovanou verzi.

- Ujistěte se, že soubor MSBuild *. props* importovaný z balíčku testovacího adaptéru je také správně aktualizován. Ověřte verzi balíčku NuGet nebo cestu k importu, která se obvykle nachází v horní části souboru projektu, jako je například následující:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Přizpůsobení sestavení

**Můžu přizpůsobit buildy Live Unit Testing?**

Pokud vaše řešení vyžaduje vlastní kroky k sestavení pro instrumentaci (Live Unit Testing), které nejsou vyžadovány pro "normální" neinstrumentované sestavení, pak můžete přidat kód do projektu nebo *. soubory cílů* , které kontrolují vlastnost `BuildingForLiveUnitTesting` a provádí vlastní kroky před/po sestavení. Můžete také zvolit odebrání některých kroků sestavení (například publikování nebo generování balíčků) nebo přidání kroků sestavení (například zkopírování požadavků) do Live Unit Testing sestavení na základě této vlastnosti projektu. Přizpůsobení sestavení na základě této vlastnosti nemění vaše pravidelné sestavení jakýmkoli způsobem a má vliv pouze na Live Unit Testing sestavení.

Může se například jednat o cíl, který vytváří balíčky NuGet během pravidelného sestavování. Pravděpodobně nechcete generovat balíčky NuGet po každé úpravě, kterou provedete. Proto můžete tento cíl v Live Unit Testing sestavení zakázat následujícím způsobem:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Chybové zprávy s \<OutputPath >, \<OutDir > nebo \<IntermediateOutputPath >

**Proč se při Live Unit Testing pokusu o sestavení řešení zobrazí následující chyba: "... Zdá se, že se nepodmíněně nastaví `<OutputPath>` nebo `<OutDir>`. Live Unit Testing neprovede testy z výstupního sestavení?**

K této chybě může dojít, pokud proces sestavení pro vaše řešení má vlastní logiku, která určuje, kde se mají vygenerovat binární soubory. Ve výchozím nastavení závisí umístění binárních souborů na `<OutputPath>`, `<OutDir>` nebo `<IntermediateOutputPath>` a také `<BaseOutputPath>` nebo `<BaseIntermediateOutputPath>`.

Live Unit Testing přepisuje tyto proměnné, aby bylo zajištěno, že artefakty sestavení jsou vyřazeny do složky Live Unit Testing artefakty a selže, pokud proces sestavení také přepíše tyto proměnné.

Existují dva hlavní přístupy k úspěšnému provedení Live Unit Testing sestavení. Pro snazší konfigurace sestavení můžete na `<BaseIntermediateOutputPath>`založit výstupní cesty. V případě složitějších konfigurací můžete na `<LiveUnitTestingBuildRootPath>`založit výstupní cesty.

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Přepisování `<OutputPath>`/`<IntermediateOutputPath>` podmíněně na základě `<BaseOutputPath>`/ `<BaseIntermediateOutputPath>`.

> [!NOTE]
> Chcete-li použít tento přístup, každý projekt musí být schopný sestavit nezávisle na sobě. Během sestavování nemusíte z jiného projektu provádět žádné artefakty odkazování na projekt. Nevytvářejte sestavení dynamicky načíst sestavení z jiného projektu za běhu (například volání `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`).

Během sestavování Live Unit Testing automaticky Přepisuje `<BaseOutputPath>`/`<BaseIntermediateOutputPath>` proměnných pro cílovou složku Live Unit Testing artefakty.

Například pokud vaše sestavení přepíše <OutputPath>, jak je znázorněno níže:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

pak ho můžete nahradit následujícím kódem XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Tím se zajistí, že `<OutputPath>` leží v rámci `<BaseOutputPath>` složky.

Nepřepisujte `<OutDir>` přímo v procesu sestavení; Přepište `<OutputPath>` místo toho, aby se artefakty sestavení vynechal na konkrétní místo.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Přepsání vlastností na základě vlastnosti `<LiveUnitTestingBuildRootPath>`.

> [!NOTE]
> V tomto přístupu musíte být opatrní o souborech přidaných do složky artefakty, které se během sestavení negenerují. Následující příklad ukazuje, co udělat při umístění složky Packages v části artefakty. Vzhledem k tomu, že obsah této složky není generován během sestavení, vlastnost MSBuild **by neměla být změněna**.

Během Live Unit Testing sestavení je vlastnost `<LiveUnitTestingBuildRootPath>` nastavena na umístění složky Live Unit Testing artefakty.

Předpokládejme například, že váš projekt má strukturu zobrazenou zde.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Během Live Unit Testing sestavení je vlastnost `<LiveUnitTestingBuildRootPath>` nastavena na úplnou cestu `.vs\...\lut\0\b`. Definuje-li projekt `<ArtifactsRoot>` vlastnost, která je mapována na adresář řešení, můžete projekt MSBuild aktualizovat následujícím způsobem:

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

## <a name="build-artifact-location"></a>Umístění artefaktu sestavení

**Chci, aby artefakty Live Unit Testing sestavení přešly do konkrétního umístění namísto výchozího umístění ve složce *. vs* . Jak můžu změnit tuto možnost?**

Nastavte `LiveUnitTesting_BuildRoot` proměnnou prostředí na úrovni uživatele na cestu, kam chcete vyřadit artefakty Live Unit Testing sestavení. 

## <a name="test-explorer-versus-live-unit-testing"></a>Průzkumník testů versus Live Unit Testing

**Jak se spouští testy z okna Průzkumníka testů, se liší od spuštění testů v Live Unit Testing?**

Existuje několik rozdílů:

- Spuštění nebo ladění testů z okna **Průzkumníka testů** spouští běžné binární soubory, zatímco Live Unit Testing spouští instrumentované binární soubory. Pokud chcete ladit instrumentované binární soubory, přidejte [ladicí program. spustit](xref:System.Diagnostics.Debugger.Launch) volání metody v testovací metodě způsobí, že se ladicí program spustí vždy, když se spustí Tato metoda (včetně toho, kdy se spustí pomocí Live Unit testing), a pak můžete připojit a ladit instrumentované binární soubory. Ale doufáme, že je instrumentace pro většinu uživatelských scénářů transparentní a že nepotřebujete ladit instrumentované binární soubory.

- Live Unit Testing nevytváří novou doménu aplikace pro spuštění testů, ale testy spouštěné z okna **Průzkumník testů** vytvoří novou doménu aplikace.

- Live Unit Testing spustí testy v každé sestavení testu postupně. V **Průzkumníku testů**můžete zvolit paralelní spuštění více testů.

- **Průzkumník testů** ve výchozím nastavení spouští testy v modelu STA (Single-threaded Apartment), zatímco Live Unit Testing spouští testy v modelu MTA (multi-threaded Apartment). Chcete-li spustit testy MSTest v modelu STA v Live Unit Testing, seupravte testovací metodu nebo obsahující třídu atributem `<STATestMethod>` nebo `<STATestClass>`, který lze nalézt v `MSTest.STAExtensions 1.0.3-beta` balíčku NuGet. Pro NUnit seupravte testovací metodu pomocí atributu `<RequiresThread(ApartmentState.STA)>` a pro xUnit s atributem `<STAFact>`.

## <a name="exclude-tests"></a>Vyloučit testy

**Návody vyloučit testy z účasti v Live Unit Testing?**

V části [použití Live Unit Testing v aplikaci Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) pro nastavení specifické pro uživatele naleznete informace v části "zahrnutí a vyloučení testovacích projektů a testovacích metod". Zahrnutí nebo vyloučení testů je užitečné, pokud chcete spustit konkrétní sadu testů pro určitou relaci úprav nebo zachovat vlastní osobní preference.

V případě nastavení specifických pro řešení můžete použít atribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> programově pro vyloučení metod, vlastností, tříd nebo struktur, ze kterých lze instrumentovat Live Unit Testing. Kromě toho můžete také nastavit vlastnost `<ExcludeFromCodeCoverage>` na `true` v souboru projektu tak, aby se vyloučil celý projekt z instrumentace. Live Unit Testing bude stále spouštět testy, které nebyly instrumentované, ale jejich pokrytí nebude vizuálně fungovat.

Můžete také ověřit, zda je `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` načtena v aktuální doméně aplikace, a zakázat testy založené na tom, proč. Pomocí xUnit můžete například udělat něco podobného jako následující:

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

## <a name="win32-pe-headers"></a>Hlavičky Win32 PE

**Proč se záhlaví Win32 PE liší v instrumentovaná sestavení vytvořená za provozu Live Unit Testing?**

Tento problém je vyřešen a neexistuje v aplikaci Visual Studio 2017 verze 15,3 a novější.

Pro starší verze sady Visual Studio 2017 existuje známá chyba, která může způsobit, že se sestavení Live Unit Testing nedaří vložit následující data hlavičky Win32 PE:

- Verze souboru (určená @System.Reflection.AssemblyFileVersionAttribute v kódu).

- Ikona Win32 (určená parametrem `/win32icon:` v příkazovém řádku).

- Manifest Win32 (určený parametrem `/win32manifest:` v příkazovém řádku).

Testy, které spoléhají na tyto hodnoty, mohou být při spuštění službou Live Unit Tests neúspěšné.

::: moniker-end

## <a name="continuous-builds"></a>Průběžná sestavení

**Proč živý test jednotek neustále sestavuje řešení i v případě, že neprovádíte žádné úpravy?**

Vaše řešení může sestavit i v případě, že neprovádíte úpravy, pokud proces sestavení generuje zdrojový kód, který je součástí samotného řešení, a vaše cílové soubory sestavení nemají odpovídající vstupy a výstupy. Cílům by měl být uveden seznam vstupů a výstupů, aby nástroj MSBuild mohl provádět příslušné kontroly a určit, zda je vyžadováno nové sestavení.

Live Unit Testing spustí sestavení pokaždé, když zjistí, že se změnily zdrojové soubory. Vzhledem k tomu, že sestavení řešení generuje zdrojové soubory, Live Unit Testing se dostane do nekonečné smyčky sestavení. Pokud jsou však vstupy a výstupy cíle zkontrolovány, když Live Unit Testing spustí druhé sestavení (po zjištění nově vygenerovaných zdrojových souborů z předchozího sestavení), dojde k zalomení smyčky sestavení, protože kontroly vstupů a výstupů signalizují, že všechno je v aktuálním stavu.

## <a name="editor-icons"></a>Ikony editoru

**Proč v editoru nevidím žádné ikony, i když Live Unit Testing zdá spustit testy na základě zpráv v okně výstup?**

V editoru se nemusí zobrazovat ikony, pokud sestavení, na kterých Live Unit Testing pracuje, nejsou z nějakého důvodu instrumentovaná. Například Live Unit Testing není kompatibilní s projekty, které nastavují `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. V takovém případě je třeba aktualizovat proces sestavení, aby toto nastavení buď odebralo, nebo bylo možné změnit `true` Live Unit Testing fungovat. 

## <a name="capture-logs"></a>Zaznamenat protokoly

**Návody shromažďovat podrobnější protokoly o chybách souborů?**

K shromažďování podrobnějších protokolů můžete provést několik věcí:

- Přejděte na **nástroje** > **Možnosti** > **Live Unit Testing** a změňte možnost protokolování na **verbose**. Podrobné protokolování způsobí, že se v okně **výstup** Zobrazí podrobnější protokoly.

- Nastavte `LiveUnitTesting_BuildLog` proměnnou prostředí uživatele na název souboru, který chcete použít k zachycení protokolu MSBuild. Podrobné zprávy protokolu MSBuild z Live Unit Testing sestavení je možné z tohoto souboru načíst.

- Nastavte `LiveUnitTesting_TestPlatformLog` proměnnou prostředí uživatele na `1` pro zachycení protokolu testovací platformy. Podrobné zprávy protokolu testovací platformy z Live Unit Testing spuštění lze následně načíst z `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Vytvořte proměnnou prostředí na úrovni uživatele s názvem `VS_UTE_DIAGNOSTICS` a nastavte ji na 1 (nebo libovolnou hodnotu) a restartujte Visual Studio. Nyní byste měli vidět spoustu protokolování na kartě **výstupní-testy** v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- [Živé testování částí](live-unit-testing.md)
