---
title: Přizpůsobení sestavení | Microsoft Docs
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
ms.sourcegitcommit: a80489d216c4316fde2579a0a2d7fdb54478abdf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652791"
---
# <a name="customize-your-build"></a>Přizpůsobení sestavení

Projekty nástroje MSBuild, které používají standardní proces sestavení (import *Microsoft. Common. props* a *Microsoft. Common. targets*) mají několik zavěšení rozšíření, které lze použít k přizpůsobení procesu sestavení.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Přidání argumentů pro volání MSBuild příkazového řádku pro váš projekt

Soubor *Directory. Build. rsp* ve zdrojovém adresáři nebo nad ním bude použit pro sestavení projektu z příkazového řádku. Podrobnosti najdete v tématu [soubory odezvy nástroje MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory. Build. props a Directory. Build. targets

Pokud jste před nástrojem MSBuild verze 15 chtěli poskytnout novou vlastní vlastnost projektům ve vašem řešení, museli jste ručně přidat odkaz na tuto vlastnost do každého souboru projektu v řešení. Nebo jste museli definovat vlastnost v souboru *. props* a pak explicitně naimportovat soubor *. props* do každého projektu v řešení, mimo jiné.

Nyní však můžete přidat novou vlastnost do každého projektu v jednom kroku definováním v jednom souboru s názvem *Directory. Build. props* v kořenové složce, která obsahuje váš zdroj. Při spuštění nástroje MSBuild vyhledá *Microsoft. Common. props* vaši adresářovou strukturu *. soubor. Build. props* (a *Microsoft. Common. targets* vyhledává pro *Directory. Build. targets*). Pokud ho najde, importuje vlastnost. *Directory. Build. props* je uživatelsky definovaný soubor, který poskytuje přizpůsobení projektům v adresáři.

> [!NOTE]
> Systémy souborů se systémem Linux rozlišují velká a malá písmena. Ujistěte se, že velká a malá písmena adresáře. Build. props se přesně shodují, nebo se v procesu sestavení nerozpozná.
>
> Další informace najdete v [tomto problému GitHubu](https://github.com/dotnet/core/issues/1991#issue-368441031) .

### <a name="directorybuildprops-example"></a>Příklad Directory. Build. props

Pokud jste například chtěli povolit všem vašim projektům přístup k nové funkci Roslyn **/Deterministic** (která je vystavena v Roslyn `CoreCompile` cíli vlastností `$(Deterministic)`), můžete provést následující.

1. Vytvořte nový soubor v kořenovém adresáři úložiště s názvem *Directory. Build. props*.
2. Do souboru přidejte následující kód XML.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Spusťte nástroj MSBuild. Stávající importy *Microsoft. Common. props* a *Microsoft. Common. targets* vyhledá soubor a naimportuje ho.

### <a name="search-scope"></a>Obor vyhledávání

Při hledání souboru *Directory. Build. props* provede MSBuild strukturu adresáře směrem nahoru z umístění projektu (`$(MSBuildProjectFullPath)`) a zastavuje se, jakmile nalezne soubor *Directory. Build. props* . Pokud jste například `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1*, MSBuild by začal hledat a potom hledat ve struktuře adresáře vzhůru až do chvíle, kdy se nachází v souboru *Directory. Build. props* , jako v následující adresářové struktuře.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Umístění souboru řešení je irelevantní pro *Directory. Build. props*.

### <a name="import-order"></a>Pořadí importu

*Adresář. Build. props* je importován velmi brzy v *Microsoft. Common. props*a vlastnosti, které jsou definovány později, nejsou k dispozici. Proto se vyhněte odkazování na vlastnosti, které ještě nejsou definovány (a vyhodnotí je prázdné).

*Adresář. Build. targets* se importuje z *Microsoft. Common. targets* po importu *. soubory cílí* z balíčků NuGet. Proto může přepsat vlastnosti a cíle definované ve většině logiky sestavení, ale někdy může být nutné přizpůsobit soubor projektu po konečném importu.

### <a name="use-case-multi-level-merging"></a>Případ použití: sloučení na více úrovní

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

Může být žádoucí mít společné vlastnosti pro všechny projekty *(1)* , společné vlastnosti pro *srcch* projektů *(2 – src)* a běžné vlastnosti pro *testovací* projekty *(2-test)* .

Aby nástroj MSBuild správně sloučil "vnitřní" soubory (*2 – src* a *2-test*) se "vnějším" souborem (*1*), je nutné vzít v úvahu, že jakmile nástroj MSBuild nalezne soubor *Directory. Build. props* , zastaví se další skenování. Chcete-li pokračovat v kontrole a sloučení do vnějšího souboru, umístěte tento kód do obou vnitřních souborů:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Souhrn obecného přístupu MSBuild je následující:

- Pro každý daný projekt MSBuild najde první *adresář. Build. props* směrem nahoru ve struktuře řešení, sloučí ho s výchozími a zastaví vyhledávání.
- Pokud chcete najít a sloučit více úrovní, pak [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (viz výše) "vnější" soubor ze souboru "vnitřní".
- Pokud soubor "vnější" sám naimportuje něco nad ním, pak se kontrola zastaví.
- Chcete-li řídit proces skenování nebo sloučení, použijte `$(DirectoryBuildPropsPath)` a `$(ImportDirectoryBuildProps)`

Nebo jednoduše: první *adresář. Build. props* , který neimportuje cokoli, je místo, kde se MSBuild zastaví.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Výběr mezi přidáváním vlastností do souboru. props nebo. targets

MSBuild je závislý na pořadí importu a poslední definice vlastnosti (nebo `UsingTask` nebo cíle) je použitá definice.

Při použití explicitních importů můžete v libovolném bodě importovat ze souboru *. props* nebo *. targets* . Tady je široce používaná konvence:

- soubory *. props* jsou importovány do začátku v pořadí importu.

- soubory *. targets* se v pořadí sestavení importují pozdě.

Tato konvence se vynutila `<Project Sdk="SdkName">` importy (to znamená, že se nejdřív naváží *sada SDK. props* , před celý obsah souboru, potom *sada SDK. targets* ), a to po celém obsahu souboru.

Při rozhodování, kam umístit vlastnosti, použijte následující obecné pokyny:

- Pro mnoho vlastností nezáleží na tom, kde jsou definovány, protože nejsou přepsány a budou načteny pouze v době spuštění.

- Pro chování, které je možné přizpůsobit v individuálním projektu, nastavte výchozí hodnoty v souborech *. props* .

- Vyhněte se nastavení závislých vlastností v souborech *. props* čtením hodnoty potenciálně přizpůsobené vlastnosti, protože vlastní nastavení se neprovede, dokud nástroj MSBuild nenačte projekt uživatele.

- Nastavte závislé vlastnosti v souborech *. targets* , protože si budou vybírat vlastní nastavení z jednotlivých projektů.

- Pokud potřebujete přepsat vlastnosti, udělejte to v souboru *. targets* , poté, co všichni vlastní nastavení projektu uživatele mají možnost se projevit. Buďte opatrní při používání odvozených vlastností; je možné, že musí být přepsány také odvozené vlastnosti.

- Zahrnout položky do souborů *. props* (podmíněné na vlastnost). Všechny vlastnosti jsou zváženy před jakoukoliv položkou, takže přizpůsobení vlastností projektu uživatele se vybírají, takže uživatel bude mít možnost `Remove` nebo `Update` jakékoliv položce, kterou importuje.

- Definujte cíle v souborech *. targets* . Pokud je však soubor *. targets* IMPORTOVÁN sadou SDK, pamatujte, že tento scénář usnadňuje přepsání cíle, protože projekt uživatele nemá místo pro jeho přepsání ve výchozím nastavení.

- Pokud je to možné, preferovat přizpůsobení vlastností v době hodnocení přes změnu vlastností v cíli. Tyto zásady usnadňují načtení projektu a pochopení, co dělá.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Ve výchozím nastavení importuje *Microsoft. Common. props* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` a *Microsoft. Common. targets* Imports `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Výchozí hodnota `MSBuildProjectExtensionsPath` je `$(BaseIntermediateOutputPath)``obj/`. NuGet používá tento mechanismus k odkazování na logiku sestavení, která se dodává s balíčky. To znamená, že v době obnovení vytvoří `{project}.nuget.g.props` soubory, které odkazují na obsah balíčku.

Tento mechanismus rozšiřitelnosti můžete zakázat nastavením vlastnosti `ImportProjectExtensionProps` na `false` v *adresáři. Build. props* nebo před importováním *Microsoft. Common. props*.

> [!NOTE]
> Zakázání importů MSBuildProjectExtensionsPath zabrání logice sestavení dodávané v balíčcích NuGet pro použití na váš projekt. Některé balíčky NuGet vyžadují pro svou funkci logiku sestavení a budou vygenerovány nepotřebné, pokud je tato funkce zakázána.

## <a name="user-file"></a>soubor. User

*Microsoft. Common. CurrentVersion. targets* importuje `$(MSBuildProjectFullPath).user`, pokud existuje, takže můžete vytvořit soubor vedle projektu s tímto dodatečným rozšířením. V případě dlouhodobých změn, které plánujete vrátit do správy zdrojových kódů, dáváte přednost změně samotného projektu, aby budoucí údržba nemusela znát tento mechanismus rozšíření.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath a MSBuildUserExtensionsPath

> [!WARNING]
> Pomocí těchto mechanismů rozšíření je obtížnější získat opakované sestavení napříč počítači. Zkuste použít konfiguraci, kterou můžete vrátit do systému správy zdrojů a sdílet mezi všemi vývojáři vašeho základu kódu.

Podle konvence importuje mnoho základních souborů logiky sestavení

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

před jejich obsahem a

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

následně. Tato konvence umožňuje nainstalovaným sadám SDK rozšířit logiku sestavení běžných typů projektů.

V `$(MSBuildUserExtensionsPath)`je prohledávána stejná adresářová struktura, což je složka pro jednotlivé uživatele, která je *%localappdata%\Microsoft\MSBuild*. Soubory umístěné v této složce budou naimportovány pro všechna sestavení odpovídajícího typu projektu spuštěná v rámci pověření tohoto uživatele. Rozšíření uživatelů můžete zakázat nastavením vlastností pojmenovaných po importu souboru ve vzorovém `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Například nastavení `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` na `false` by zabránilo importování `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Přizpůsobení buildu řešení

> [!IMPORTANT]
> Přizpůsobení řešení sestavení tímto způsobem se vztahuje pouze na sestavení příkazového řádku pomocí nástroje *MSBuild. exe*. Nevztahuje **se** na sestavení v rámci sady Visual Studio.

Když nástroj MSBuild vytvoří soubor řešení, nejprve ho přeloží do souboru projektu a poté sestaví. Vygenerovaný soubor projektu importuje `before.{solutionname}.sln.targets` před definováním cílů a `after.{solutionname}.sln.targets` po importu cílů, včetně cílů nainstalovaných do `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` a `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` adresářů.

Můžete například definovat nový cíl pro zápis vlastní zprávy protokolu po sestavení *MyCustomizedSolution. sln* vytvořením souboru ve stejném adresáři s názvem *po. MyCustomizedSolution. sln. cíle* , které obsahují

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>Přizpůsobení všech sestavení .NET

Při údržbě serveru sestavení může být nutné nakonfigurovat nastavení MSBuild globálně pro všechna sestavení na serveru.  V zásadě můžete upravit globální soubory *Microsoft. Common. targets* nebo *Microsoft. Common. props* , ale existuje lepší způsob. Můžete ovlivnit všechna sestavení určitého typu projektu (například všechny C# projekty) pomocí určitých vlastností nástroje MSBuild a přidat určité vlastní `.targets` a soubory `.props`.

Aby bylo možné C# ovlivnit všechna nebo Visual Basic sestavení, která se řídí instalací nástroje MSBuild nebo Visual Studio, vytvořte *vlastní soubor. před. Microsoft. Common. targets* nebo *Custom. After. Microsoft. Common. cílí* na cíle, které se spustí před *nebo po* *Microsoft.* Common. Targets nebo Custom................. *..* ............ *. Common.*

Umístění těchto souborů můžete určit pomocí následujících vlastností nástroje MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

*Společné* verze těchto vlastností mají vliv i C# na projekty Visual Basic. Tyto vlastnosti lze nastavit v příkazovém řádku nástroje MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Nejlepší přístup závisí na vašem scénáři. Pokud máte vyhrazený server sestavení a chcete zajistit, aby se určité cíle vždy spouštěly na všech sestaveních vhodného typu projektu, které na tomto serveru běží, pak použití globálního vlastního `.targets` nebo `.props` souboru dává smysl.  Pokud chcete, aby se vlastní cíle prováděly pouze v případě, že platí určité podmínky, použijte jiné umístění souboru a nastavte cestu k tomuto souboru nastavením příslušné vlastnosti MSBuild v příkazovém řádku MSBuild pouze v případě potřeby.

> [!WARNING]
> Visual Studio používá vlastní `.targets` nebo `.props` soubory, pokud je nalezne ve složce MSBuild vždy, když sestaví projekt odpovídajícího typu. To může mít nežádoucí následky a v případě nesprávného fungování může aplikace Visual Studio zakázat možnost sestavení v počítači.

## <a name="customize-all-c-builds"></a>Přizpůsobit všechna C++ sestavení

V C++ případě projektů jsou dříve zmíněné vlastní `.targets` a soubory `.props` ignorovány. Pro C++ projekty můžete vytvořit `.targets` soubory pro každou platformu a umístit je do odpovídajících složek pro import pro tyto platformy.

Soubor `.targets` pro platformu Win32, *Microsoft. cpp. Win32. targets*obsahuje následující prvek `Import`:

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

Podobné prvky importu existují pro jiné cílové platformy ve *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ Platforms\*.

Po umístění souboru `.targets` do příslušné složky podle platformy nástroj MSBuild importuje soubor do každého C++ sestavení pro tuto platformu. V případě potřeby můžete do nějakého umístění zadat více `.targets` souborů.

### <a name="specify-a-custom-import-on-the-command-line"></a>Zadat vlastní import na příkazovém řádku

Pro vlastní `.targets`, které chcete zahrnout pro konkrétní sestavení C++ projektu, nastavte jednu nebo obě vlastnosti `ForceImportBeforeCppTargets` a `ForceImportAfterCppTargets` na příkazovém řádku.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Pro globální nastavení (to znamená, že všechna C++ sestavení pro platformu na serveru sestavení) existují dvě metody. Nejdřív můžete tyto vlastnosti nastavit pomocí proměnné prostředí systému, která je vždycky nastavená. Tento postup funguje, protože nástroj MSBuild vždy přečte prostředí a vytvoří (nebo Přepisuje) vlastnosti pro všechny proměnné prostředí.

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
