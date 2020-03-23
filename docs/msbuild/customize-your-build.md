---
title: Přizpůsobení sestavení | Dokumenty společnosti Microsoft
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652791"
---
# <a name="customize-your-build"></a>Přizpůsobení sestavení

Projekty MSBuild, které používají standardní proces sestavení (import *microsoft.common.props* a *Microsoft.Common.targets)* mají několik připojitelných háků rozšiřitelnosti, které můžete použít k přizpůsobení procesu sestavení.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Přidání argumentů do příkazového řádku MSBuild vyvolání projektu

Pro sestavení řídicího řádku projektu bude použit soubor *Directory.Build.rsp* ve zdrojovém adresáři nebo nad ním. Podrobnosti naleznete v [tématu MSBuild response files](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props a Directory.Build.targets

Před MSBuild verze 15, pokud jste chtěli poskytnout nové, vlastní vlastnosti projekty ve vašem řešení, bylo nutné ručně přidat odkaz na tuto vlastnost do každého souboru projektu v řešení. Nebo jste museli definovat vlastnost v souboru *.props* a pak explicitně importovat soubor *.props* v každém projektu v řešení, mimo jiné.

Nyní však můžete přidat novou vlastnost do každého projektu v jednom kroku definováním v jednom souboru s názvem *Directory.Build.props* v kořenové složce, která obsahuje zdroj. Při spuštění nástroje MSBuild vyhledá *soubor Microsoft.Common.props* ve struktuře adresářů soubor *Directory.Build.props* (a *soubor Microsoft.Common.targets* vyhledá *soubor Directory.Build.targets*). Pokud najde jeden, importuje vlastnost. *Directory.Build.props* je uživatelem definovaný soubor, který poskytuje vlastní nastavení projektů mj.

> [!NOTE]
> Linuxové souborové systémy rozlišují malá a velká písmena. Ujistěte se, že velikost názvu souboru Directory.Build.props přesně odpovídá, jinak nebude během procesu sestavení rozpoznána.
>
> Další informace najdete v [tomto problému s GitHubem.](https://github.com/dotnet/core/issues/1991#issue-368441031)

### <a name="directorybuildprops-example"></a>Příklad souboru Directory.Build.props

Například pokud jste chtěli povolit všechny vaše projekty pro přístup k nové Roslyn **/deterministický** prvek (který je vystaven v Roslyn `CoreCompile` cíl vlastnost `$(Deterministic)`), můžete provést následující akce.

1. Vytvořte nový soubor v kořenovém adresáři úložiště s názvem *Directory.Build.props*.
2. Přidejte do souboru následující xml.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Spusťte msbuild. Existující importy *microsoft.common.props* a *microsoft.common.targets* v projektu najdou soubor a importují ho.

### <a name="search-scope"></a>Obor hledání

Při hledání souboru *Directory.Build.props* msbuild chodí adresářové struktury směrem`$(MSBuildProjectFullPath)`nahoru z umístění projektu ( ), zastavení po vyhledá *souborDirectory.Build.props.* Pokud jste například `$(MSBuildProjectFullPath)` byli *c:\users\username\code\test\case1*, msbuild by tam začal hledat a pak by prohledával adresářovou strukturu směrem nahoru, dokud by nenašel soubor *Directory.Build.props,* jako v následující adresářové struktuře.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Umístění souboru řešení je irelevantní pro *Directory.Build.props*.

### <a name="import-order"></a>Dovozní objednávka

*Soubor Directory.Build.props* je importován velmi brzy do *souboru Microsoft.Common.props*a vlastnosti definované později nejsou k dispozici. Takže se vyhněte odkazování na vlastnosti, které ještě nejsou definovány (a vyhodnotí prázdné).

*Directory.Build.targets* je importován z *Microsoft.Common.targets* po importu souborů *.targets* z balíčků NuGet. Tak to může přepsat vlastnosti a cíle definované ve většině logiky sestavení, ale někdy budete muset přizpůsobit soubor projektu po konečném importu.

### <a name="use-case-multi-level-merging"></a>Případ použití: víceúrovňové sloučení

Předpokládejme, že máte tuto standardní strukturu řešení:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Může být žádoucí mít společné vlastnosti pro všechny projekty *(1),* společné vlastnosti pro *projekty src* *(2-src)* a společné vlastnosti pro *testovací* projekty *(2-test)*.

Chcete-li, aby MSBuild správně sloučit "vnitřní" soubory (*2-src* a *2-test*) s "vnější" soubor (*1*), je třeba vzít v úvahu, že jakmile MSBuild najde *Directory.Build.props* soubor, zastaví další skenování. Chcete-li pokračovat v prohledávání a sloučit do vnějšího souboru, umístěte tento kód do obou vnitřních souborů:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Souhrn obecného přístupu MSBuild je následující:

- Pro daný projekt MSBuild najde první *Directory.Build.props* nahoru ve struktuře řešení, sloučí ji s výchozí mise a zastaví skenování pro více
- Pokud chcete najít a sloučit [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) více úrovní, pak (viz výše) "vnější" soubor z "vnitřního" souboru
- Pokud "vnější" soubor není sám také import ovat něco nad ním, pak skenování zastaví tam
- Pro řízení procesu skenování/slučování použijte `$(DirectoryBuildPropsPath)` a`$(ImportDirectoryBuildProps)`

Nebo jednodušeji: první *Directory.Build.props,* který neimportuje nic je místo, kde MSBuild zastaví.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Výběr mezi přidáním vlastností do souboru .props nebo .targets

MSBuild závisí na pořadí importu a poslední definice `UsingTask` vlastnosti (nebo nebo cíl) je definice používá.

Při použití explicitních importů můžete importovat ze souboru *.props* nebo *.targets* kdykoli. Zde je široce používán konvence:

- *Soubory .props* jsou importovány v rané fázi importu.

- *.targets* soubory jsou importovány pozdě v pořadí sestavení.

Tato konvence je `<Project Sdk="SdkName">` vynucena importy (to znamená, že import *Sdk.props* je na prvním místě, před veškerý obsah souboru, pak *Sdk.targets* je poslední, po všech obsah souboru).

Při rozhodování o tom, kam umístit vlastnosti, použijte následující obecné pokyny:

- Pro mnoho vlastností nezáleží na tom, kde jsou definovány, protože nejsou přepsány a budou jen pro čtení v době spuštění.

- Pro chování, které může být přizpůsobeno v jednotlivém projektu, nastavte výchozí hodnoty v souborech *.props.*

- Vyhněte se nastavení závislých vlastností v souborech *.props* čtením hodnoty případně přizpůsobené vlastnosti, protože k vlastnímu nastavení nedojde, dokud MSBuild nepřečte projekt uživatele.

- Nastavte závislé vlastnosti v souborech *.targets,* protože budou vybírat vlastní nastavení z jednotlivých projektů.

- Pokud potřebujete přepsat vlastnosti, proveďte to v souboru *.targets* poté, co všechna vlastní nastavení uživatelského projektu měla šanci se projevit. Buďte opatrní při použití odvozených vlastností; odvozené vlastnosti může být nutné přepsat také.

- Zahrnout položky do souborů *.props* (podmíněno vlastností). Všechny vlastnosti jsou považovány za před libovolnou položkou, takže vlastní nastavení vlastností projektu `Remove` `Update` uživatele získat vyzvednout, a to dává projektu uživatele příležitost nebo jakékoli položky přinesl importu.

- Definujte cíle v souborech *.targets.* Pokud je však soubor *.targets* importován sadou SDK, nezapomeňte, že tento scénář ztěžuje přepsání cíle, protože projekt uživatele nemá ve výchozím nastavení místo, které by jej přepsalo.

- Pokud je to možné, upřednostňujte přizpůsobení vlastností v době vyhodnocení před změnou vlastností uvnitř cíle. Tento pokyn usnadňuje načtení projektu a pochopení toho, co dělá.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Ve výchozím nastavení importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` *soubor Microsoft.Common.props* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`a importy *Microsoft.Common.targets* . Výchozí hodnota `MSBuildProjectExtensionsPath` je `$(BaseIntermediateOutputPath)` `obj/`, . NuGet používá tento mechanismus odkazovat na sestavení logiky dodané s balíčky; to znamená, že v `{project}.nuget.g.props` době obnovení vytvoří soubory, které odkazují na obsah balíčku.

Tento mechanismus rozšiřitelnosti můžete zakázat nastavením vlastnosti `ImportProjectExtensionProps` `false` v *souboru Directory.Build.props* nebo před importem *souboru Microsoft.Common.props*.

> [!NOTE]
> Zakázání importu MSBuildProjectExtensionsPath zabrání logice sestavení dodané v balíčcích NuGet v aplikaci. Některé balíčky NuGet vyžadují logiku sestavení k provedení své funkce a budou vykresleny k ničemu, pokud je tato funkce zakázána.

## <a name="user-file"></a>Soubor UŽIVATELE .user

*Microsoft.Common.CurrentVersion.cíle* importuje, `$(MSBuildProjectFullPath).user` pokud existuje, takže můžete vytvořit soubor vedle projektu s tímto dalším rozšířením. Pro dlouhodobé změny, které plánujete zkontrolovat do správy zdrojového kódu, raději změnit samotný projekt tak, aby budoucí správci nemusí vědět o tomto mechanismu rozšíření.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath a MSBuildUserExtensionsPath

> [!WARNING]
> Pomocí těchto rozšiřujících mechanismů je těžší získat opakovatelné sestavení napříč počítači. Zkuste použít konfiguraci, která může být zařazována do systému správy zdrojového kódu a sdílena mezi všemi vývojáři vašeho základu kódu.

Podle konvence importuje mnoho souborů logiky jádra sestavení

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

před jejich obsahem a

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Potom. Tato konvence umožňuje nainstalovaným sadám SDK rozšířit logiku sestavení běžných typů projektů.

V aplikaci je `$(MSBuildUserExtensionsPath)`prohledána stejná adresářová struktura , což je složka *%LOCALAPPDATA%\Microsoft\MSBuild*. Soubory umístěné v této složce budou importovány pro všechna sestavení odpovídajícího typu projektu spuštěná pod pověřeními tohoto uživatele. Přípony uživatele můžete zakázat nastavením vlastností pojmenovaných `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`po importu souboru ve vzorku . Například nastavení `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` by zabránit `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`importu .

## <a name="customize-the-solution-build"></a>Přizpůsobení sestavení řešení

> [!IMPORTANT]
> Přizpůsobení sestavení řešení tímto způsobem platí pouze pro sestavení příkazového řádku pomocí *msbuild.exe*. **Nevztahuje** se na sestavení uvnitř sady Visual Studio.

Když MSBuild vytvoří soubor řešení, nejprve převede interně do souboru projektu a pak jej vytvoří. Generovaný soubor projektu `before.{solutionname}.sln.targets` importuje před `after.{solutionname}.sln.targets` definováním cíle a po `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` importu cílů, včetně cílů nainstalovaných do adresářů a. `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`

Můžete například definovat nový cíl pro zápis vlastní zprávy protokolu po vytvoření *mycustomizedsolution.sln* vytvořením souboru ve stejném adresáři pojmenované *po. MyCustomizedSolution.sln.targets,* který obsahuje

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>Přizpůsobit všechna sestavení rozhraní .NET

Při údržbě serveru sestavení může být nutné globálně nakonfigurovat nastavení MSBuild pro všechna sestavení na serveru.  V zásadě můžete upravit globální soubory *Microsoft.Common.Targets* nebo *Microsoft.Common.Props,* ale existuje lepší způsob. Můžete ovlivnit všechna sestavení určitého typu projektu (například všechny projekty Jazyka C#) `.targets` pomocí `.props` určitých vlastností MSBuild a přidáním určitých vlastních a souborů.

Chcete-li ovlivnit všechna sestavení jazyka C# nebo Visual Basic, která se řídí instalací sady MSBuild nebo Visual Studio, vytvořte soubor *Custom.Before.Microsoft.Common.Targets* nebo *Custom.After.Microsoft.Common.Targets* s cíli, které budou spuštěny před nebo po *microsoft.common.targets*nebo souborcustom.before.microsoft.common.props nebo *Custom.Before.Microsoft.Common.Props* *custom.after.microsoft.common.props* s vlastnostmi, které budou zpracovány před nebo po *Microsoft.Common.rekvizity*.

Umístění těchto souborů můžete určit pomocí následujících vlastností MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicCíle
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

*Běžné* verze těchto vlastností ovlivňují projekty jazyka C# i Visual Basic. Tyto vlastnosti můžete nastavit v příkazovém řádku MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Nejlepší přístup závisí na vašem scénáři. Pokud máte vyhrazený server sestavení a chcete zajistit, aby určité cíle vždy spustit na všech sestavení ch `.targets` příslušného typu projektu, které se spustí na tomto serveru, pak pomocí globální vlastní nebo `.props` soubor má smysl.  Pokud chcete, aby se vlastní cíle spouštěli pouze v případě, že platí určité podmínky, použijte jiné umístění souboru a nastavte cestu k tomuto souboru nastavením příslušné vlastnosti MSBuild v příkazovém řádku MSBuild pouze v případě potřeby.

> [!WARNING]
> Visual Studio používá `.targets` `.props` vlastní nebo soubory, pokud je najde ve složce MSBuild vždy, když vytvoří libovolný projekt odpovídajícího typu. To může mít nezamýšlené důsledky a pokud provádí nesprávně, můžete zakázat možnost Sady Visual Studio stavět v počítači.

## <a name="customize-all-c-builds"></a>Přizpůsobení všech sestavení c++

Pro projekty jazyka C++ `.targets` jsou `.props` dříve uvedené vlastní a soubory ignorovány. Pro projekty jazyka C++ můžete vytvořit `.targets` soubory pro každou platformu a umístit je do příslušných složek importu pro tyto platformy.

Soubor `.targets` pro platformu Win32, *Microsoft.Cpp.Win32.targets* `Import` , obsahuje následující prvek:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Na konci stejného souboru je podobný prvek:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Podobné prvky importu existují pro jiné cílové platformy v aplikaci *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms\*.

Jakmile umístíte `.targets` soubor do příslušné složky podle platformy, MSBuild importuje soubor do každého sestavení Jazyka C++ pro tuto platformu. V případě `.targets` potřeby tam můžete umístit více souborů.

### <a name="specify-a-custom-import-on-the-command-line"></a>Určení vlastního importu na příkazovém řádku

Pro `.targets` vlastní, které chcete zahrnout pro konkrétní sestavení projektu Jazyka C++, `ForceImportBeforeCppTargets` `ForceImportAfterCppTargets` nastavte jednu nebo obě vlastnosti a na příkazovém řádku.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Pro globální nastavení (ovlivnit, řekněme, všechny sestavení Jazyka C++ pro platformu na serveru sestavení), existují dvě metody. Nejprve můžete nastavit tyto vlastnosti pomocí proměnné prostředí systému, která je vždy nastavena. To funguje, protože MSBuild vždy čte prostředí a vytváří (nebo přepíše) vlastnosti pro všechny proměnné prostředí.

## <a name="see-also"></a>Viz také

- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
