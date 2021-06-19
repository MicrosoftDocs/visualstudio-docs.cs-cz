---
title: Vyhrazené a dobře známé vlastnosti nástroje MSBuild | Microsoft Docs
description: Přečtěte si o rezervovaných a známých vlastnostech MSBuild, předdefinovaných vlastnostech, které ukládají informace o souboru projektu a binárních souborech MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384925"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Vyhrazené a známé vlastnosti nástroje MSBuild

Nástroj MSBuild poskytuje sadu předdefinovaných vlastností, které ukládají informace o souboru projektu a binárních souborech nástroje MSBuild. Tyto vlastnosti jsou vyhodnocovány stejným způsobem jako ostatní vlastnosti MSBuild. Chcete-li například použít `MSBuildProjectFile` vlastnost, zadáte `$(MSBuildProjectFile)` .

 Nástroj MSBuild používá hodnoty v následující tabulce k předdefinování rezervovaných a dobře známých vlastností. Vyhrazené vlastnosti nelze přepsat, ale známé vlastnosti lze přepsat pomocí identicky pojmenovaných vlastností prostředí, globálních vlastností nebo vlastností, které jsou deklarovány v souboru projektu.

## <a name="reserved-and-well-known-properties"></a>Vyhrazené a dobře známé vlastnosti

Tabulka v této části zobrazuje předdefinované vlastnosti MSBuild. Vzorový sloupec v tabulce se vztahuje k následujícímu ukázkovému souboru projektu, který se má umístit na `C:\Source\Repos\ConsoleApp1\ConsoleApp1` , a ukazuje hodnoty těchto vlastností, které jsou v souboru projektu k dispozici, když je nástroj MSBuild vyvolán bez speciálních možností příkazového řádku, se sestavením verze Preview sady Visual Studio 2019 verze 16,7.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Vlastnost | Rezervované nebo dobře známé | Popis | Příklad |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Vyhrazené | Absolutní cesta ke složce, ve které jsou aktuálně používány binární soubory nástroje MSBuild (například *C:\Windows\Microsoft.NET\Framework \\ \<versionNumber>*). Tato vlastnost je užitečná, pokud musíte odkazovat na soubory v adresáři MSBuild.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Dobře známé | Zavedeno v .NET Framework 4: neexistuje žádný rozdíl mezi výchozími hodnotami `MSBuildExtensionsPath` a `MSBuildExtensionsPath32` . Proměnnou prostředí lze nastavit `MSBUILDLEGACYEXTENSIONSPATH` na hodnotu, která není null, chcete-li povolit chování výchozí hodnoty `MSBuildExtensionsPath` v předchozích verzích.<br /><br /> V .NET Framework 3,5 a starších verzích výchozí hodnota `MSBuildExtensionsPath` odkazuje na cestu podsložky MSBuild ve složce *\\ \Program Files* nebo *\Program Files (x86)* v závislosti na bitová verze aktuálního procesu. Například pro 32 proces na 64 počítači tato vlastnost odkazuje na složku *\Program Files (x86)* . Pro 64 proces na 64 počítači tato vlastnost odkazuje na složku *\Program Files* .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.<br /><br /> Toto umístění je užitečné místo pro vložení vlastních cílových souborů. Například vaše cílové soubory mohou být nainstalovány do *složky \Program Files\MSBuild\MyFiles\Northwind.targets* a následně importovány do souborů projektu pomocí tohoto kódu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Dobře známé | Cesta podsložky MSBuild ve složce *\Program Files* nebo *\Program Files (x86)* . Tato cesta vždy odkazuje na 32 složku *\Program Files (x86)* na 32 počítači a *\Program Files* na počítači s podporou 64. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath64` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Dobře známé | Cesta podsložky MSBuild ve složce *\Program Files* Pro 64 počítač tato cesta vždy odkazuje na složku *\Program Files* . Pro 32 počítač je tato cesta prázdná. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath32` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Vyhrazené | `true` Pokud nástroj MSBuild běží interaktivně, umožňuje vstup uživatele. Toto nastavení je řízeno `-interactive` možností příkazového řádku. | `false` |
| `MSBuildLastTaskResult` | Vyhrazené | `true` v případě, že předchozí úloha byla dokončena bez chyb (i v případě výskytu upozornění) nebo `false` v případě, že předchozí úloha obsahovala chyby. Při výskytu chyby v úloze obvykle dojde k chybě poslední věcí, ke které dojde v projektu. Hodnota této vlastnosti proto nikdy není `false` , s výjimkou těchto scénářů:<br /><br /> – Pokud `ContinueOnError` je atribut [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) nastaven na `WarnAndContinue` (nebo `true` ) nebo `ErrorAndContinue` .<br /><br /> – Pokud `Target` má [element Error (MSBuild)](../msbuild/onerror-element-msbuild.md) jako podřízený element. | `true` |
| `MSBuildNodeCount` | Vyhrazené | Maximální počet souběžných procesů, které jsou používány při sestavování. Toto je hodnota, kterou jste zadali pro parametr **-maxcpucount** na příkazovém řádku. Pokud jste zadali **-maxcpucount** bez zadání hodnoty, pak `MSBuildNodeCount` určí počet procesorů v počítači. Další informace naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md) a [Souběžné sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Vyhrazené | Umístění 32 složky programu; například *C:\Program Files (x86)*.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Vyhrazené | Úplný seznam cílů, které jsou zadány v `DefaultTargets` atributu `Project` elementu. Například následující `Project` element by měl `MSBuildDefaultTargets` hodnotu vlastnosti `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Vyhrazené | Absolutní cesta k adresáři, kde je umístěn soubor projektu, například *C:\MyCompany\MyProduct*.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Vyhrazené | Hodnota `MSBuildProjectDirectory` vlastnosti s výjimkou kořenové jednotky.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Vyhrazené | Přípona názvu souboru projektu, včetně období; například *. proj*. | `.csproj`|
| `MSBuildProjectFile` | Vyhrazené | Úplný název souboru projektu, včetně přípony názvu souboru; například *MyApp. proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Vyhrazené | Absolutní cesta a úplný název souboru projektu, včetně přípony názvu souboru; například *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Vyhrazené | Název souboru projektu bez přípony názvu souboru; například *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Vyhrazené | Typ modulu runtime, který je právě spuštěn. Představeno v MSBuild 15. Hodnota může být nedefinovaná (před MSBuild 15), která `Full` značí, že nástroj MSBuild běží na desktopové .NET Framework, `Core` což značí, že nástroj MSBuild běží v .NET Core (například v `dotnet build` ), nebo `Mono` označuje, že nástroj MSBuild běží na mono. | `Full` |
| `MSBuildStartupDirectory` | Vyhrazené | Absolutní cesta ke složce, ve které je volána aplikace MSBuild. Pomocí této vlastnosti můžete sestavit vše pod konkrétním bodem ve stromové struktuře projektu bez vytváření souborů *\<dirs> . proj* v každém adresáři. Místo toho máte pouze jeden projekt – například *c:\traversal.proj*, jak je znázorněno zde:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Chcete-li vytvořit libovolný bod stromu, zadejte:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Vyhrazené | Část názvu souboru a přípony souboru `MSBuildThisFileFullPath` . | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Vyhrazené | Část adresáře `MSBuildThisFileFullPath` .<br /><br /> V cestě zahrňte konečné zpětné lomítko. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Vyhrazené | Část adresáře s `MSBuildThisFileFullPath` výjimkou kořenové jednotky.<br /><br /> V cestě zahrňte konečné zpětné lomítko. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Vyhrazené | Část s příponou názvu souboru `MSBuildThisFileFullPath` . | `.csproj` |
| `MSBuildThisFileFullPath` | Vyhrazené | Absolutní cesta k souboru projektu nebo cíle, který obsahuje cíl, na kterém je spuštěný.<br /><br /> Tip: v souboru cílů můžete zadat relativní cestu, která je relativní vzhledem k souboru cílů, a není relativní vzhledem k původnímu souboru projektu. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Vyhrazené | Část názvu souboru `MSBuildThisFileFullPath` bez přípony názvu souboru. | `ConsoleApp1` |
| `MSBuildToolsPath` | Vyhrazené | Instalační cesta verze nástroje MSBuild, která je přidružena k hodnotě `MSBuildToolsVersion` .<br /><br /> Do cesty nezahrnujte koncové zpětné lomítko.<br /><br /> Tuto vlastnost nelze přepsat. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Vyhrazené | Verze sady nástrojů MSBuild, která se používá k sestavení projektu.<br /><br /> Poznámka: sada nástrojů MSBuild se skládá z úloh, cílů a nástrojů, které se používají k sestavení aplikace. Mezi tyto nástroje patří kompilátory, jako jsou *csc.exe* a *vbc.exe*. Další informace najdete v tématech [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)a [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Vyhrazené | Verze nástroje MSBuild použitá k sestavení projektu. <br /><br/> Tuto vlastnost nelze přepsat, jinak je vrácena chybová zpráva `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` . | 16.11.0 |
| `MSBuildAssemblyVersion` | Vyhrazené | Verze sestavení nástroje MSBuild použité k sestavení projektu. | 16,0 |
| `MSBuildFileVersion` | Vyhrazené | Verze 4 části sestavení nástroje MSBuild použité k sestavení projektu. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Vyhrazené | Úplná verze 2,0 semver sady MSBuild pro sestavení projektu. | 16.11.0-Preview-21302-05 + 5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Názvy, které jsou v konfliktu s elementy MSBuild

Kromě výše uvedených názvů nelze názvy odpovídající elementům jazyka MSBuild použít pro uživatelem definované vlastnosti, položky nebo metadata položky:

* VisualStudioProject
* Cíl
* PropertyGroup
* Výstup
* ItemGroup
* UsingTask
* ProjectExtensions –
* OnError
* ImportGroup –
* Pomocí volby
* Když
* Případech

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

- [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
