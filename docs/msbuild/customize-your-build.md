---
title: Přizpůsobení sestav | Microsoft Docs
description: Seznamte se s několika hooky rozšiřitelnosti, které můžete použít k přizpůsobení projektů MSBuild, které používají standardní proces sestavení.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19dafcbb956634eeea5fa0ed967e93a8a8d5e546
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588446"
---
# <a name="customize-your-build"></a>Přizpůsobení sestavení

Projekty MSBuild, které používají standardní proces sestavení (import *Microsoft.Common.props* a *Microsoft.Common.targets),* mají několik zachytávání rozšiřitelnosti, které můžete použít k přizpůsobení procesu sestavení.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Přidání argumentů do volání MSBuildu pro váš projekt z příkazového řádku

Na sestavení příkazového řádku projektu se použije soubor *Directory.Build.rsp* ve zdrojovém adresáři nebo vyšším. Podrobnosti najdete v tématu Soubory [odpovědí nástroje MSBuild.](../msbuild/msbuild-response-files.md#directorybuildrsp)

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props a Directory.Build.targets

Pokud jste před msbuildem verze 15 chtěli do projektů v řešení zadat novou vlastní vlastnost, museli jste ručně přidat odkaz na tuto vlastnost do každého souboru projektu v řešení. Nebo jste museli definovat vlastnost v souboru *.props* a pak explicitně importovat soubor *.props* do každého projektu v řešení, mimo jiné.

Teď ale můžete do každého projektu v jednom kroku přidat novou vlastnost tak, že ji definujete v jednom souboru s názvem *Directory.Build.props* v kořenové složce, která obsahuje váš zdroj. Při spuštění nástroje MSBuild hledá soubor *Directory.Build.props* ve vaší adresářové struktuře (a *Microsoft.Common.targets* hledá *Directory.Build.targets).*  Pokud ho najde, naimportuje vlastnost . *Directory.Build.props* je uživatelem definovaný soubor, který umožňuje přizpůsobení projektů v adresáři.

> [!NOTE]
> V linuxových systémech souborů se rozlišují malá a velká písmena. Ujistěte se, že se název souboru Directory.Build.props přesně shoduje, jinak se během procesu sestavení nezjme.
>
> Další [informace najdete v tomto problému na GitHubu.](https://github.com/dotnet/core/issues/1991#issue-368441031)

### <a name="directorybuildprops-example"></a>Příklad Directory.Build.props

Pokud například chcete povolit všem projektům přístup k nové funkci Roslyn **/deterministic** (která je zveřejněná v cíli Roslyn vlastností ), můžete `CoreCompile` provést následující `$(Deterministic)` akce.

1. V kořenovém adresáři vašeho adresáře vytvořte nový soubor s názvem *Directory.Build.props.*
2. Do souboru přidejte následující kód XML.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Spusťte nástroj MSBuild. Existující importy *Microsoft.Common.props* a *Microsoft.Common.targets* vašeho projektu najdou soubor a naimportuje ho.

### <a name="search-scope"></a>Obor hledání

Při hledání souboru *Directory.Build.props* nástroj MSBuild provede adresářovou strukturu směrem nahoru od umístění projektu ( ) a zastaví se po nalezení souboru `$(MSBuildProjectFullPath)` *Directory.Build.props.* Pokud jste například byli `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1*, nástroj MSBuild by tam začal hledat a pak prohledá adresářovou strukturu směrem nahoru, dokud by nenašla soubor *Directory.Build.props* jako v následující adresářové struktuře.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Umístění souboru řešení není pro *Directory.Build.props relevantní.*

### <a name="import-order"></a>Pořadí importu

*Directory.Build.props* je importován velmi brzy v *Microsoft.Common.props* a vlastnosti definované později nejsou k dispozici. Proto se vyhněte odkazování na vlastnosti, které ještě nejsou definované (a vyhodnotí se jako prázdné).

Vlastnosti, které jsou nastavené v *Directory.Build.props,* je možné přepsat jinde v souboru projektu nebo v importovaných souborech, takže byste si měli nastavení v *Souboru Directory.Build.props* myslet jako na určení výchozích hodnot pro vaše projekty.

*Directory.Build.targets* se importuje z *Microsoft.Common.targets* po importu *souborů .targets* z balíčků NuGet. Může tak přepsat vlastnosti a cíle definované ve většině logiky sestavení nebo nastavit vlastnosti pro všechny projekty bez ohledu na to, co jednotlivé projekty nastaví.

Pokud potřebujete nastavit vlastnost nebo definovat cíl pro jednotlivý projekt, který přepíše předchozí nastavení, dejte tuto logiku do souboru projektu po posledním importu. Abyste to mohli udělat v projektu ve stylu sady SDK, musíte nejprve nahradit atribut ve stylu sady SDK ekvivalentními importy. Viz Použití projektových sdk [nástroje MSBuild.](how-to-use-project-sdk.md)

> [!NOTE]
> Modul MSBuild během vyhodnocování čte ve všech importovaných souborech před zahájením provádění sestavení pro libovolný projekt (včetně libovolného), takže se neočekává, že tyto soubory budou upraveny žádným jiným procesem `PreBuildEvent` `PreBuildEvent` sestavení. Žádné úpravy se nepro projeví až při příštím vyvolání *MSBuild.exe* nebo dalšího Visual Studio sestavení.

### <a name="use-case-multi-level-merging"></a>Případ použití: sloučení na více úrovních

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

Může být žádoucí mít společné vlastnosti pro všechny projekty *(1),* společné vlastnosti pro projekty *src*  *(2-src)* a společné vlastnosti pro projekty testů *(2-test).*

Aby nástroj MSBuild správně sloučí "vnitřní" soubory (*2-src* a *2-test*) s "vnějším" souborem (*1*), musíte vzít v úvahu, že jakmile nástroj MSBuild najde soubor *Directory.Build.props,* zastaví další kontrolu. Pokud chcete pokračovat v prohledávání a sloučení do vnějšího souboru, umístěte tento kód do obou vnitřních souborů:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Obecný přístup nástroje MSBuild je následující:

- U libovolného projektu nástroj MSBuild najde první soubor *Directory.Build.props* směrem nahoru ve struktuře řešení, sloučí ho s výchozími nastaveními a zastaví vyhledávání dalších.
- Pokud chcete najít a sloučit více úrovní, [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) pak (viz výše) vnější soubor z "vnitřního" souboru.
- Pokud "vnější" soubor sám neimportuje něco nad něj, zastaví se kontrola.
- Pokud chcete řídit proces skenování/slučování, použijte a . `$(DirectoryBuildPropsPath)``$(ImportDirectoryBuildProps)`

Nebo jednodušeji: první *Directory.Build.props,* který nic neimportuje, je místo, kde se zastaví nástroj MSBuild.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Volba mezi přidáním vlastností do souboru .props nebo .targets

Nástroj MSBuild je závislý na pořadí importu a poslední definicí vlastnosti (nebo `UsingTask` cíle) je použitá definice.

Při použití explicitních importů můžete kdykoli importovat ze *souboru .props* nebo *.targets.* Tady je běžně používaná konvence:

- *Soubory .props* jsou importovány v rané fázi pořadí importu.

- *Soubory .targets*  se importuje později v pořadí sestavení.

Tato konvence se vynucuje importy (to znamená, že import `<Project Sdk="SdkName">` *souboru Sdk.props* je na prvním místě, před veškerým obsahem souboru je *sdk.targets* na posledním místě po veškerém obsahu souboru).

Při rozhodování, kam umístit vlastnosti, použijte následující obecné pokyny:

- U mnoha vlastností nezáleží na tom, kde jsou definovány, protože nejsou přepsány a budou čteny pouze při spuštění.

- Pro chování, které lze přizpůsobit v jednotlivých projektech, nastavte výchozí hodnoty v *souborech .props.*

- Vyhněte se nastavení závislých vlastností v souborech *.props* přečtením hodnoty pravděpodobně přizpůsobené vlastnosti, protože k přizpůsobení nedojde, dokud nástroj MSBuild nečte projekt uživatele.

- Nastavte závislé vlastnosti *v souborech .targets,* protože si vyberou vlastní nastavení z jednotlivých projektů.

- Pokud potřebujete přepsat vlastnosti, udělejte to v souboru *.targets* poté, co se všechna vlastní nastavení uživatelských projektů projeví. Buďte opatrní při používání odvozených vlastností. Je možné, že bude nutné přepsat také odvozené vlastnosti.

- Zahrnutí položek *do souborů .props* (podmíněných vlastností) Všechny vlastnosti se zvažují před jakoukoli položkou, takže přizpůsobení vlastností uživatelského projektu se převezou, což dává projektu uživatele příležitost nebo jakoukoli položku, kterou import `Remove` `Update` přináší.

- Definujte cíle v *souborech .targets.* Pokud je ale soubor *.targets* importován sadou SDK, mějte na paměti, že tento scénář ztěžuje přepsání cíle, protože projekt uživatele nemá místo, kde by ho ve výchozím nastavení přepisoval.

- Pokud je to možné, upřednostňte přizpůsobení vlastností při vyhodnocování před změnou vlastností uvnitř cíle. Tento návod usnadňuje načtení projektu a pochopení jeho práce.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Ve výchozím nastavení *importuje Microsoft.Common.props* a `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` *Microsoft.Common.targets* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` . Výchozí hodnota je `MSBuildProjectExtensionsPath` `$(BaseIntermediateOutputPath)` , `obj/` . NuGet používá tento mechanismus k odkazování na logiku sestavení dodanou s balíčky. To znamená, že v době obnovení vytvoří `{project}.nuget.g.props` soubory, které odkazují na obsah balíčku.

Tento mechanismus rozšiřitelnosti můžete zakázat nastavením vlastnosti na hodnotu `ImportProjectExtensionProps` v `false` souboru *Directory.Build.props* nebo před importem souboru *Microsoft.Common.props*.

> [!NOTE]
> Zakázání importů MSBuildProjectExtensionsPath zabrání použití logiky sestavení doručené v balíčcích NuGet na váš projekt. Některé balíčky NuGet vyžadují k provádění své funkce logiku sestavení a budou nepoužitelné, pokud je tato možnost zakázaná.

## <a name="user-file"></a>Soubor .user

*Microsoft.Common.CurrentVersion.targets importuje* , pokud existuje, takže můžete vytvořit soubor vedle projektu s `$(MSBuildProjectFullPath).user` tímto dalším rozšířením. U dlouhodobých změn, které plánujete sesouvat do správy zdrojového kódu, upřednostňujte změnu samotného projektu tak, aby o tomto mechanismu rozšíření nemusí vědět budoucí údržbáři.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath a MSBuildUserExtensionsPath

> [!WARNING]
> Použití těchto rozšiřujících mechanismů ztěžuje opakované sestavení napříč počítači. Zkuste použít konfiguraci, kterou je možné zkontrolovat v systému správy zdrojového kódu a sdílet ji mezi všemi vývojáři vašeho základního kódu.

Podle konvence importuje mnoho základních souborů logiky sestavení.

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

před jejich obsahem, a

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Potom. Tato konvence umožňuje nainstalovaným sdk rozšířit logiku sestavení běžných typů projektů.

Stejná adresářová struktura se prohledá v adresáři , což je složka pro uživatele `$(MSBuildUserExtensionsPath)` *%LOCALAPPDATA%\Microsoft\MSBuild*. Soubory umístěné do této složky budou importovány pro všechna sestavení odpovídajícího typu projektu spuštěná pod přihlašovacími údaji tohoto uživatele. Uživatelská rozšíření můžete zakázat nastavením vlastností pojmenovaných podle importovaného souboru ve vzoru `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` . Pokud například nastavíte `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` na `false` , zabráníte importu `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` .

## <a name="customize-the-solution-build"></a>Přizpůsobení sestavení řešení

> [!IMPORTANT]
> Přizpůsobení sestavení řešení tímto způsobem se vztahuje pouze na sestavení příkazového řádku s *MSBuild.exe*. Nevztahuje **se** na sestavení uvnitř Visual Studio. Z tohoto důvodu se nedoporučuje přizpůsobovat na úrovni řešení. Lepší alternativou pro přizpůsobení všech projektů v řešení je použití souborů *Directory.Build.props* a *Directory.build.targets* ve složce řešení, jak je popsáno jinde v tomto článku.

Když nástroj MSBuild sestaví soubor řešení, nejprve ho interně přeloží do souboru projektu a pak ho sestaví. Vygenerovaný soubor projektu importuje před definováním cílů a po importu cílů, včetně cílů `before.{solutionname}.sln.targets` `after.{solutionname}.sln.targets` nainstalovaných do `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` adresářů a `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` .

Můžete například definovat nový cíl pro zápis vlastní zprávy protokolu po sestavení *MyCustomizedSolution.sln* vytvořením souboru ve stejném adresáři *pojmenovaném po. MyCustomizedSolution.sln.targets obsahující*

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Sestavení řešení je oddělené od sestavení projektu, takže nastavení zde nemá vliv na sestavení projektu.

## <a name="customize-all-net-builds"></a>Přizpůsobení všech sestavení .NET

Při údržbě serveru sestavení může být nutné nakonfigurovat nastavení MSBuild globálně pro všechna sestavení na serveru.  V zásadě můžete upravit globální soubory *Microsoft. Common. targets* nebo *Microsoft. Common. props* , ale existuje lepší způsob. Můžete ovlivnit všechna sestavení určitého typu projektu (například všechny projekty jazyka C#) pomocí určitých vlastností MSBuild a přidat určité vlastní `.targets` `.props` soubory a.

Aby ovlivnila všechna sestavení C# nebo Visual Basic, která se řídí instalací nástroje MSBuild nebo Visual Studio, vytvořte *vlastní soubor. před. Microsoft. Common. targets* nebo *Custom. After. Microsoft. Common. cílí* na cíle, které se spustí před *nebo po* *Microsoft.* Common. Targets nebo Custom................. *..* ............ *. Common.*

Umístění těchto souborů můžete určit pomocí následujících vlastností nástroje MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

*Společné* verze těchto vlastností mají vliv na projekty C# i Visual Basic. Tyto vlastnosti lze nastavit v příkazovém řádku nástroje MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Nejlepší přístup závisí na vašem scénáři. Pomocí rozšiřitelnosti sady Visual Studio můžete přizpůsobit systém sestavení a poskytnout mechanizmus pro instalaci a správu úprav.

Pokud máte vyhrazený server sestavení a chcete zajistit, aby se určité cíle vždy spouštěly na všech sestaveních příslušného typu projektu, které na tomto serveru běží, pak použijte globální vlastní `.targets` soubor nebo `.props` smysl.  Pokud chcete, aby se vlastní cíle prováděly pouze v případě, že platí určité podmínky, použijte jiné umístění souboru a nastavte cestu k tomuto souboru nastavením příslušné vlastnosti MSBuild v příkazovém řádku MSBuild pouze v případě potřeby.

> [!WARNING]
> Visual Studio používá vlastní `.targets` soubory nebo, `.props` Pokud je nalezne ve složce MSBuild vždy, když vytvoří libovolný projekt odpovídajícího typu. To může mít nežádoucí následky a v případě nesprávného fungování může aplikace Visual Studio zakázat možnost sestavení v počítači.

## <a name="customize-c-builds"></a>Přizpůsobení sestavení C++

V případě projektů v jazyce C++ nelze použít dříve zmíněné soubory Custom *. targets* a *. props* stejným způsobem, než bude možné přepsat výchozí nastavení. *Adresář. Build. props* importovala *Společnost Microsoft. Common. props*, který je importován v `Microsoft.Cpp.Default.props` i když je většina výchozích hodnot definována v souboru *Microsoft. cpp. props* a pro určitý počet vlastností a "Pokud ještě není definováno", nelze použít, protože vlastnost je již definována, ale výchozí hodnota musí být odlišná pro konkrétní vlastnosti projektu definované v `PropertyGroup` with `Label="Configuration"` (viz [struktura souborů. vcxproj a. props](/cpp/build/reference/vcxproj-file-structure)).

Pomocí následujících vlastností ale můžete určit soubory *. props* , které se mají automaticky importovat před nebo po *\* Microsoft. cpp.* Files:

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Chcete-li přizpůsobit výchozí hodnoty vlastností pro všechna sestavení v jazyce C++, vytvořte další soubor *. props* (například *MyProps. props*) a definujte `ForceImportAfterCppProps` vlastnost v `Directory.Build.props` nasměrování:

<PropertyGroup><ForceImportAfterCppProps>$ (MsbuildThisFileDirectory) \MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps. props* budou automaticky importovány na konci na konci *Microsoft. cpp. props*.

## <a name="customize-all-c-builds"></a>Přizpůsobení všech sestavení v jazyce C++

Přizpůsobení instalace sady Visual Studio se nedoporučuje, protože není snadné sledovat taková vlastní nastavení, ale pokud rozšiřujete sadu Visual Studio o přizpůsobení sestavení C++ pro konkrétní platformu, můžete vytvořit `.targets` soubory pro každou platformu a umístit je do odpovídajících složek pro import pro tyto platformy jako součást rozšíření sady Visual Studio.

`.targets`Soubor pro platformu Win32, *Microsoft. cpp. Win32. targets* obsahuje následující `Import` element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Poblíž konce stejného souboru je podobný element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Podobné prvky importu existují pro jiné cílové platformy ve *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ Platformch \* .

Po umístění `.targets` souboru do příslušné `ImportAfter` složky podle platformy nástroj MSBuild importuje soubor do každého sestavení v jazyce C++ pro tuto platformu. `.targets`V případě potřeby můžete umístit více souborů. 

Pomocí rozšiřitelnosti sady Visual Studio je možné provádět další úpravy, jako je například definování nové platformy. Další informace naleznete v tématu [rozšiřitelnost projektů C++](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Zadat vlastní import na příkazovém řádku

Pro vlastní `.targets` , které chcete zahrnout pro konkrétní sestavení projektu C++, nastavte jednu nebo obě vlastnosti `ForceImportBeforeCppTargets` a `ForceImportAfterCppTargets` na příkazovém řádku.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Pro globální nastavení (to znamená, že všechna sestavení C++ pro platformu na serveru sestavení) existují dvě metody. Nejdřív můžete tyto vlastnosti nastavit pomocí proměnné prostředí systému, která je vždycky nastavená. Tento postup funguje, protože nástroj MSBuild vždy přečte prostředí a vytvoří (nebo Přepisuje) vlastnosti pro všechny proměnné prostředí.

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
