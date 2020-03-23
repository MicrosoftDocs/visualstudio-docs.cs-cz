---
title: Rezervované a dobře známé vlastnosti msbuild | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633249"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Vyhrazené a dobře známé vlastnosti msbuild

MSBuild poskytuje sadu předdefinovaných vlastností, které ukládají informace o souboru projektu a binárních souborech MSBuild. Tyto vlastnosti jsou vyhodnocovány stejným způsobem jako ostatní vlastnosti MSBuild. Chcete-li například `MSBuildProjectFile` použít vlastnost, zadejte `$(MSBuildProjectFile)`.

 MSBuild používá hodnoty v následující tabulce k předdefinování vyhrazených a dobře známých vlastností. Vyhrazené vlastnosti nelze přepsat, ale dobře známé vlastnosti lze přepsat pomocí identicky pojmenovaných vlastností prostředí, globálních vlastností nebo vlastností, které jsou deklarovány v souboru projektu.

## <a name="reserved-and-well-known-properties"></a>Vyhrazené a dobře známé nemovitosti

 Následující tabulka popisuje předdefinované vlastnosti MSBuild.

| Vlastnost | Rezervovaný nebo dobře známý | Popis |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Vyhrazeno | Absolutní cesta ke složce, ve které jsou aktuálně používány binární soubory MSBuild (například *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>*). Tato vlastnost je užitečná, pokud máte odkazovat na soubory v adresáři MSBuild.<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildExtensionsPath` | Well-known | Zavedeno v rozhraní .NET Framework 4: neexistuje žádný `MSBuildExtensionsPath` `MSBuildExtensionsPath32`rozdíl mezi výchozí hodnoty a . Proměnnou `MSBUILDLEGACYEXTENSIONSPATH` prostředí můžete nastavit na hodnotu bez nuly, abyste `MSBuildExtensionsPath` povolili chování výchozí hodnoty v dřívějších verzích.<br /><br /> Ve složce .NET Framework 3.5 a `MSBuildExtensionsPath` starší je výchozí hodnota odkazuje na cestu podsložky MSBuild ve složce *\Program Files\\ * nebo *\Program Files (x86)* v závislosti na bittě aktuálního procesu. Například pro 32bitový proces v 64bitovém počítači tato vlastnost odkazuje na složku *\Program Files (x86).* U 64bitového procesu v 64bitovém počítači tato vlastnost odkazuje na složku *\Program Files.*<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost.<br /><br /> Toto umístění je užitečné místo pro umístění vlastních cílových souborů. Cílové soubory mohou být například nainstalovány na *\Program Files\MSBuild\MyFiles\Northwind.targets* a poté importovány do souborů projektu pomocí tohoto kódu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Well-known | Cesta k podsložce MSBuild ve složce *\Program Files* nebo *\Program Files (x86).* Cesta vždy odkazuje na složku *32bitových \Program Files (x86)* v 32bitovém počítači a *\Program Files* v 64bitovém počítači.". Viz `MSBuildExtensionsPath` také `MSBuildExtensionsPath64`a .<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildExtensionsPath64` | Well-known | Cesta k podsložce MSBuild ve složce *\Program Files.* U 64bitového počítače tato cesta vždy odkazuje na složku *\Program Files.* Pro 32bitový počítač je tato cesta prázdná. Viz `MSBuildExtensionsPath` také `MSBuildExtensionsPath32`a .<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildInteractive` | Vyhrazeno | `true`Pokud MSBuild běží interaktivně, povolení vstupu uživatele. Toto nastavení je `-interactive` řízeno možností příkazového řádku. |
| `MSBuildLastTaskResult` | Vyhrazeno | `true`pokud byl předchozí úkol dokončen bez chyb (i `false` když došlo k upozorněním) nebo pokud předchozí úkol měl chyby. Obvykle dojde k chybě v úkolu, chyba je poslední věc, která se stane v tomto projektu. Proto hodnota této vlastnosti `false`je nikdy , s výjimkou v těchto scénářích:<br /><br /> - Když `ContinueOnError` je atribut [Task element (MSBuild)](../msbuild/task-element-msbuild.md) `true`nastavenna `ErrorAndContinue` `WarnAndContinue` na (nebo ) nebo .<br /><br /> - Když `Target` má [OnError element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako podřízený prvek. |
| `MSBuildNodeCount` | Vyhrazeno | Maximální počet souběžných procesů, které se používají při vytváření. Toto je hodnota, kterou jste zadali pro **-maxcpucount** na příkazovém řádku. Pokud jste zadali **-maxcpucount** bez `MSBuildNodeCount` zadání hodnoty, pak určuje počet procesorů v počítači. Další informace naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md) a [sestavení více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Vyhrazeno | Umístění 32bitové složky programu; například *C:\Program Files (x86)*.<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildProjectDefaultTargets` | Vyhrazeno | Úplný seznam cílů, které jsou `DefaultTargets` určeny `Project` v atributu prvku. Například následující `Project` prvek by `MSBuildDefaultTargets` měl hodnotu vlastnosti `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Vyhrazeno | Absolutní cesta k adresáři, ve kterém je soubor projektu umístěn, například *C:\MyCompany\MyProduct*.<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildProjectDirectoryNoRoot` | Vyhrazeno | Hodnota vlastnosti, `MSBuildProjectDirectory` s výjimkou kořenové jednotky.<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildProjectExtension` | Vyhrazeno | Přípona názvu souboru projektu, včetně období; například *.proj*. |
| `MSBuildProjectFile` | Vyhrazeno | Úplný název souboru projektu, včetně přípony názvu souboru; například *MyApp.proj*. |
| `MSBuildProjectFullPath` | Vyhrazeno | Absolutní cesta a úplný název souboru projektu, včetně přípony názvu souboru; například *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Vyhrazeno | Název souboru projektu bez přípony názvu souboru; například *MyApp*. |
| `MSBuildRuntimeType` | Vyhrazeno | Typ modulu runtime, který je aktuálně spuštěn. Představenv MSBuild 15. Hodnota může být nedefinovaná (před `Full` msbuild 15), označující, že MSBuild je spuštěn na ploše .NET Framework, označující, `Core` že MSBuild je spuštěn na .NET Core (například v `dotnet build`) nebo `Mono` označující, že MSBuild je spuštěn na Mono. |
| `MSBuildStartupDirectory` | Vyhrazeno | Absolutní cesta složky, kde msbuild je volána. Pomocí této vlastnosti můžete vytvořit vše pod určitým bodem ve stromu projektu bez vytváření * \<souborů dirs>.proj* v každém adresáři. Místo toho máte pouze jeden projekt – například *c:\traversal.proj*, jak je znázorněno zde:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Chcete-li vytvořit v libovolném bodě stromu, zadejte:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nezahrnejte konečné zpětné lomítko na tuto vlastnost. |
| `MSBuildThisFile` | Vyhrazeno | Část aplikace `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Vyhrazeno | Adresářová část `MSBuildThisFileFullPath`aplikace .<br /><br /> Do cesty zahrňte konečné zpětné lomítko. |
| `MSBuildThisFileDirectoryNoRoot` | Vyhrazeno | Část adresáře `MSBuildThisFileFullPath`, s výjimkou kořenové jednotky.<br /><br /> Do cesty zahrňte konečné zpětné lomítko. |
| `MSBuildThisFileExtension` | Vyhrazeno | Část přípony názvu `MSBuildThisFileFullPath`souboru . |
| `MSBuildThisFileFullPath` | Vyhrazeno | Absolutní cesta projektu nebo cíle souboru, který obsahuje cíl, který je spuštěn.<br /><br /> Tip: V souboru cílů můžete určit relativní cestu, která je relativní k souboru cílů a není relativní k původnímu souboru projektu. |
| `MSBuildThisFileName` | Vyhrazeno | Část s názvem `MSBuildThisFileFullPath`souboru aplikace , bez přípony názvu souboru. |
| `MSBuildToolsPath` | Vyhrazeno | Instalační cesta verze MSBuild, která je přidružena `MSBuildToolsVersion`k hodnotě aplikace .<br /><br /> Konečné zpětné lomítko do cesty nezahrnte.<br /><br /> Tuto vlastnost nelze přepsat. |
| `MSBuildToolsVersion` | Vyhrazeno | Verze sady nástrojů MSBuild, která se používá k sestavení projektu.<br /><br /> Poznámka: Sada nástrojů MSBuild se skládá z úkolů, cílů a nástrojů, které se používají k vytvoření aplikace. Nástroje zahrnují kompilátory, například *csc.exe* a *vbc.exe*. Další informace naleznete v [tématech Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)a [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Vyhrazeno | Verze MSBuild slouží k sestavení projektu. <br /><br/> Tuto vlastnost nelze přepsat, jinak je `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` vrácena chybová zpráva. |

## <a name="names-that-conflict-with-msbuild-elements"></a>Názvy, které jsou v konfliktu s prvky MSBuild

Kromě výše uvedeného nelze pro uživatelem definované vlastnosti, položky nebo metadata položky použít názvy odpovídající prvkům jazyka MSBuild:

* Projekt VisualStudioProject
* Cíl
* Propertygroup
* Výstup
* Skupina položek
* UsingTask
* Rozšíření projektu
* Přichybě
* Skupina importu
* Pomocí volby
* Kdy
* Jinak

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)

- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)
