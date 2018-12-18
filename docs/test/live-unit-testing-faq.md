---
title: Nejčastější dotazy k funkci Live Unit Testing
ms.date: 2017-10-03
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2c0c81bc8413b9d1698e2ad7c21d0d9f397834ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849070"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing – nejčastější dotazy

## <a name="latest-features"></a>Nejnovější funkce
**Live Unit Testing je vylepšená a rozšířeného pravidelně. Jak může najít informace o nejnovější nové funkce a vylepšení?**

Další informace o nové funkce a vylepšení, které byly provedeny Live Unit Testing od verze Visual Studio 2017 verze 15.3, naleznete v tématu [co je nového ve službě Live Unit Testing](live-unit-testing-whats-new.md).

## <a name="supported-frameworks-and-versions"></a>Podporované architektury a verze
**Jaká testovací rozhraní nemá podporu Live Unit Testing a jaké jsou minimální podporované verze?**

Live Unit Testing spolupracuje s tři rozhraní testování částí oblíbených uvedené v následující tabulce. Minimální podporovaná verze jejich adaptéry a rozhraní je také uvedený v tabulce. Rozhraní testování částí jsou všechny dostupné z webu NuGet.org.

<table>
<tr>
   <th>Rozhraní pro testování</th>
   <th>Minimální verze aplikace Visual Studio adaptéru</th>
   <th>Minimální verze rozhraní Framework</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> verze 2.2.0-beta3-build1187 xunit.Runner.VisualStudio</td>
   <td>1.9.2 xunit</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter verzí 3.5.1</td>
   <td>NUnit verze 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Pokud máte starší založené na MSTest testovací projekty tento odkaz `Microsoft.VisualStudio.QualityTools.UnitTestFramework` a nechcete přesunout na novější balíčky MSTest NuGet, proveďte upgrade na Visual Studio 2017 verze 15.4.

V některých případech budete muset explicitně obnovit balíčky NuGet odkazované projekty v řešení v pořadí pro Live Unit Testing pro práci. Balíčky můžete obnovit buď tímto způsobem vytvořte explicitní sestavení řešení (vyberte **sestavení**, **znovu sestavit řešení** z nejvyšší úrovně nabídky sady Visual Studio), nebo kliknutím pravým tlačítkem na řešení a Výběr **obnovit balíčky NuGet** před povolením živých Unit Testing.

## <a name="net-core-support"></a>Podpora .NET core
**Live Unit Testing funguje s .NET Core?**

Ano. Live Unit Testing spolupracuje s .NET Core a .NET Framework. Nedávno byla přidána podpora pro .NET Core v sadě Visual Studio 2017 verze 15.3. Upgradovat na tuto verzi sady Visual Studio, pokud chcete podporu Live Unit Testing pro .NET Core.

## <a name="configuration"></a>Konfigurace
**Proč Live Unit Testing nefunguje, pokud můžu ho zapnout?**

**Okno výstup** (když je vybraná Live Unit Testing rozevíracího seznamu) vám měl říct, proč Live Unit Testing nefunguje. Live Unit Testing nemusí fungovat pro jednu z následujících důvodů:

- Pokud se balíčky NuGet odkazované projekty v řešení nebyly obnoveny, Live Unit Testing nebude fungovat. Způsobem vytvořte explicitní sestavení řešení nebo při obnovování balíčků NuGet v rámci řešení před zapnutím Live Unit Testing by měla tento problém vyřešit.

- Pokud používáte testy založené na MSTest ve svých projektech, ujistěte se, že odkaz na odebrat `Microsoft.VisualStudio.QualityTools.UnitTestFramework`a přidejte odkazy na nejnovější balíčky MSTest NuGet `MSTest.TestAdapter` (minimálně verze 1.1.11 je vyžadována) a `MSTest.TestFramework` (minimální verze 1.1.11 je povinný). Další informace najdete v části "Podporované testovacích architektur" [pomocí Live Unit Testing v aplikaci Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks) článku.

- Nejméně jeden projekt ve vašem řešení by měl mít odkaz na NuGet nebo přímý odkaz na xUnit, NUnit, nebo testovací rozhraní MSTest. Tento projekt by měly odkazovat také odpovídající balíček NuGet sady Visual Studio test adaptéry. Adaptér testu sady Visual Studio lze také odkazovat prostřednictvím *s příponou .runsettings* souboru. *s příponou .runsettings* souboru musí mít položku jako v následujícím příkladu:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nesprávný pokrytí po upgradu
**Proč Live Unit Testing zobrazuje nesprávný pokrytí po upgradu testovací adaptér, který je odkazováno v projektech Visual Studio na podporovanou verzi?**

- Pokud více projektů v řešení odkazu NuGet otestovat balíček adaptéru, každý z nich musí upgradovat na podporovanou verzi.

- Ujistěte se, že MSBuild *.props* soubor se importoval z balíčku adaptér testu správně aktualizovat také. Zkontrolujte NuGet balíček verze/cestu importu, který můžete obvykle nachází v horní části souboru projektu, jako je následující:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Přizpůsobení sestavení
**Můžete přizpůsobit Moje sestavení Live Unit Testing?**

Pokud vaše řešení vyžaduje vlastní postup pro sestavení pro instrumentaci (Live Unit Testing), které nejsou povinné pro "regulárního" neinstrumentovaného sestavení, pak můžete přidat kód do projektu nebo *.targets* souborů, které kontroluje, `BuildingForLiveUnitTesting` vlastnost a provede vlastní předzálohovacího nebo pozálohovacího kroky sestavení. Můžete také odebrat určité kroky sestavení (třeba publikování nebo generování balíčků) nebo přidat kroky sestavení (jako je kopírování požadavky) Live Unit Testing sestavení na základě této vlastnosti projektu. Přizpůsobení sestavení na základě této vlastnosti regulárního sestavení nijak nezmění a ovlivní pouze Live Unit Testing sestavení.

Například může být cílem, který vytváří balíčky NuGet během regulárního sestavení. Pravděpodobně nechcete, aby balíčky NuGet, se vygeneruje po každé úpravě, které provedete. Proto můžete zakázat, které se zaměřují v buildu Live Unit Testing tímto způsobem přibližně takto:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Chybové zprávy s &lt;OutputPath&gt; nebo &lt;OutDir&gt;
**Proč se při Live Unit Testing se pokusí vytvořit Moje řešení zobrazí následující chyba: ".. .se objeví bezpodmínečně nastavit `<OutputPath>` nebo `<OutDir>`. Live Unit Testing nebudou spouštět testy z výstupního sestavení"?**

Této chybě může dojít, pokud proces sestavení pro vaše řešení bezpodmínečně přepíše `<OutputPath>` nebo `<OutDir>` tak, že se nejedná o podadresář `<BaseOutputPath>`. V takových případech Live Unit Testing nebude fungovat, protože Potlačí také tyto hodnoty k zajištění, že se zahodí artefakty sestavení do složky v `<BaseOutputPath>`. Pokud je nutné přepsat místo, kam chcete artefaktům sestavení zahodí v regulárního sestavení, přepsat `<OutputPath>` podmíněně na základě `<BaseOutputPath>`.

Například, pokud přepsání sestavení `<OutputPath>` jak je znázorněno níže:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

potom můžete nahradit za následující kód XML:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

To zajistí, že `<OutputPath>` spočívá v rámci `<BaseOutputPath>` složky.

Nesmí být přepsána `<OutDir>` přímo v procesu sestavení; přepsat `<OutputPath>` místo toho vyřadit artefakty sestavení do určitého umístění.

## <a name="set-the-location-of-build-artifacts"></a>Nastavit umístění artefaktů sestavení
**Chci, aby artefakty sestavení Live Unit Testing pro přejít na konkrétní umístění, namísto výchozího umístění v rámci *.vs* složky. Jak lze změnit, který?**

Nastavte `LiveUnitTesting_BuildRoot` proměnnou individuální prostředí pro cestu, kde chcete Live Unit Testing artefakty sestavení do vyřadit. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>Test Explorer vs. Live Unit Testing testovací běhy 
**Jak je spouštění testů z okna Průzkumníka testů liší od spuštění testů v Live Unit Testing?**

Existuje několik rozdílů:

- Spuštění nebo ladění testů z **Průzkumník testů** okna ICT regulární binární soubory, zatímco Live Unit Testing běží instrumentované binární soubory. Pokud chcete ladit instrumentované binární soubory, přidávání [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) volání metody v testovací metodě způsobí, že ladicí program ke spuštění vždy, když, že metoda je proveden (včetně při spuštění pomocí Live Unit Testing) a pak můžete připojení a ladění instrumentovaný binární soubor. Naše naděje však je, že instrumentace je transparentní pro vás pro většinu scénářů uživatelů, a, není potřeba ladění instrumentované binární soubory.

- Live Unit Testing nevytvoří novou doménu aplikace pro spuštění testů, ale testy spustit z **Průzkumník testů** okno Vytvořit novou doménu aplikace.

- Live Unit Testing spustí testy v každé sestavení testu postupně, že při spuštění více testů z **Průzkumníka testů** okno a jste vybrali **spustit testy paralelně** tlačítko, poběží paralelní.

- Vyhledávání a provádění testů v Live Unit Testing používá verzi 2 `TestPlatform`, že **Průzkumník testů** okno používá verze 1. I když nebude Všimněte si rozdílu ve většině případů.

- **Průzkumník testů** aktuálně spustí testy v jednovláknový apartment (STA) ve výchozím nastavení, že Live Unit Testing spustí testy v apartmentu s více vlákny (MTA). Ke spuštění testů MSTest v STA v Live Unit Testing, uspořádání testovací metody nebo obsahující třídu `<STATestMethod>` nebo `<STATestClass>` atribut, který najdete v `MSTest.STAExtensions 1.0.3-beta` balíček NuGet. NUnit, uspořádání testovací metody s `<RequiresThread(ApartmentState.STA)>` atribut a pro xUnit, se `<STAFact>` atribut.

## <a name="exclude-tests"></a>Vyloučit testy
**Jak vyloučit testy ze Live Unit Testing?**

Najdete v části "zahrnutí a vyloučení projekty testů a testovací metody" [pomocí Live Unit Testing v aplikaci Visual Studio 2017 Enterprise Edition](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) článku pro uživatelská nastavení. Zahrnutí nebo vyloučení testů je užitečné, pokud chcete spustit konkrétní sadu testů pro konkrétní Upravit relaci nebo k uchování vašich vlastních předvoleb osobní.
 
U nastavení specifická pro řešení, můžete použít <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atribut prostřednictvím kódu programu k vyloučení je instrumentováno nástrojem Live Unit Testing metody, vlastnosti, třídy nebo struktury. Kromě toho můžete také nastavit `<ExcludeFromCodeCoverage>` vlastnost `true` v souboru projektu k vyloučení je instrumentováno celého projektu. Live Unit Testing stále poběží testy, které nebyly byla instrumentována, ale nebude možné vizualizovat jejich pokrytí.

Můžete také zkontrolovat, zda `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` je načteno do aktuální domény aplikace a zakázat testy založené na důvod, proč. Například lze provádět podobné následujícímu s použitím xUnit:

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

## <a name="win32-pe-headers"></a>Záhlaví Win32 PE
**Proč se liší v instrumentovaném sestavení vytvořená pomocí Live Unit testing záhlaví Win32 PE**

Tento problém je vyřešený a neexistuje v sadě Visual Studio 2017 verze 15.3. Upgradovat na tuto verzi sady Visual Studio.

Pro starší verze sady Visual Studio 2017 je známého problému, který může mít za následek Live Unit Testing sestavení neúspěšné k vložení dat následující záhlaví PE Win32:

- Verze souboru (určená @System.Reflection.AssemblyFileVersionAttribute v kódu).

- Ikona Win32 (určená `/win32icon:` na příkazovém řádku).

- Win32 Manifest (určená `/win32manifest:` na příkazovém řádku).

Testy, které využívají tyto hodnoty může selhat při spuštění metodou Live Unit testing.

## <a name="continuous-builds"></a>Průběžné vytváření sestavení
**Proč Live Unit testing zachovat vytváření Moje řešení neustále i v případě, že mám mi provádění veškeré úpravy?**

Vaše řešení můžete vytvářet i v případě, že nejsou provádění úprav, pokud proces sestavení vašeho řešení generuje zdrojový kód, který je součástí vlastním řešením a cílové soubory sestavení nemají odpovídající vstupy a výstupy zadán. Cíle by se měly provádět seznam vstupů a výstupů tak, aby MSBuild může provést příslušné kontroly aktuální a určit, jestli je potřeba nové sestavení.

Live Unit Testing spustí sestavení pokaždé, když se zjistí, že došlo ke změně zdrojových souborů. Protože sestavení vašeho řešení generuje zdrojové soubory, Live Unit Testing dostane do sestavení nekonečné smyčky. Pokud však vstupy a výstupy cíle jsou kontrolovány při Live Unit Testing (po zjištění nově vytvořených zdrojových souborů z předchozího buildu) spuštění druhé sestavení, protože se vstupy a výstupy kontroly, ji budou přerušit ze smyčky sestavení Označuje, že všechno, co je aktuální.  

## <a name="lightweight-solution-load"></a>Zjednodušené načtení řešení
**Live Unit testing práce s funkce zjednodušeného řešení načtení jak?**

Live Unit Testing nyní nefunguje s funkce zjednodušeného načtení řešení. Funguje pouze po nejméně jeden z testovacích projektů načtení. Dokud to neuděláte, nebude fungovat, protože Live Unit Testing je závislá na alespoň jeden z testovacích projektů odkazující na adaptér testu (MSTest, xUnit a NUnit) načítán.

> [!NOTE]
> Zjednodušené načtení řešení již není k dispozici v sadě Visual Studio 2017 verze 15.5 nebo novější. V sadě Visual Studio 2017 verze 15.5 nebo novější spravované velká řešení obsahující kód zatížení mnohem rychleji než dřív, i bez zjednodušené načtení řešení.

## <a name="new-process-coverage"></a>Nový proces pokrytí
**Proč Live Unit Testing nezachytí pokrytí z nový proces vytvořil testu?**

Jedná se o známý problém, by měl být stanovena v následné aktualizaci sady Visual Studio 2017.

## <a name="including-or-excluding-tests-not-working"></a>Zahrnutí nebo vyloučení testů nefunguje
**Proč k tomu nic dochází po můžu zahrnout nebo vyloučit testů ze sady Live Test?**

Tento problém je vyřešený a neexistuje v sadě Visual Studio 2017 verze 15.3. Upgradovat na tuto verzi sady Visual Studio.

Pro starší verze sady Visual Studio 2017 jde o známý problém. Chcete-li tento problém obejít, je potřeba upravte libovolný soubor po zahrnuty nebo vyloučeny testy. 

## <a name="editor-icons"></a>Editor ikon
**Proč se mi nezobrazují všechny ikony v editoru i v případě, že Live Unit Testing se zdá být spouštění testů na základě zpráv v okně Výstup?**

Pokud z nějakého důvodu nejsou instrumentované sestavení, která Live Unit Testing pracuje na se nemusí zobrazovat ikony v editoru. Například není kompatibilní s projekty, nastavte Live Unit Testing `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. V takovém případě je potřeba aktualizovat buď odeberte toto nastavení, nebo změňte ho na váš proces sestavení `true` pro Live Unit Testing pro práci. 

## <a name="capture-logs"></a>Zachycení protokoly
**Jak shromáždím podrobnější protokoly do souborů zpráv o chybách?**

Máte několik možností, jak shromažďovat podrobné protokoly:

- Přejděte na **nástroje** > **možnosti** > **Live Unit Testing** a změňte možnost protokolování **Verbose**. Podrobné protokolování podrobnější protokoly zobrazený v způsobí, že **výstup** okna.

- Nastavte `LiveUnitTesting_BuildLog` uživatelské proměnné prostředí na název souboru, kterou chcete použít k zachycení protokolu MSBuild. Podrobné zprávy protokolu MSBuild z Live Unit Testing sestavení mohou být načteny pak z tohoto souboru.

- Nastavte `LiveUnitTesting_TestPlatformLog` proměnnou prostředí k `1` zaznamenat do protokolu testovací platforma sady. Podrobné zprávy protokolu testovací platforma sady běhů Live Unit Testing je pak možné načíst z `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Vytvořte individuální prostředí proměnnou s názvem `VS_UTE_DIAGNOSTICS` a nastavte ho na hodnotu 1 (nebo libovolná hodnota) a restartujte aplikaci Visual Studio. Teď byste měli vidět řadu protokolování v **výstup – testy** kartu v sadě Visual Studio.

## <a name="see-also"></a>Viz také:

- [Živé testování částí](live-unit-testing.md)
