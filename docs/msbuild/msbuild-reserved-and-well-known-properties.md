---
title: Vyhrazené a dobře známé vlastnosti nástroje MSBuild | Microsoft Docs
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
ms.openlocfilehash: 1ab4c18006834cc1bef6841864e42609e09bc3a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585831"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Rezervované a dobře známé vlastnosti nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje sadu předdefinovaných vlastností, které ukládají informace o souboru projektu a binárních souborech [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tyto vlastnosti jsou vyhodnocovány stejným způsobem jako ostatní vlastnosti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Chcete-li například použít vlastnost `MSBuildProjectFile`, zadáte `$(MSBuildProjectFile)`.

 Nástroj MSBuild používá hodnoty v následující tabulce k předdefinování rezervovaných a dobře známých vlastností. Vyhrazené vlastnosti nelze přepsat, ale známé vlastnosti lze přepsat pomocí identicky pojmenovaných vlastností prostředí, globálních vlastností nebo vlastností, které jsou deklarovány v souboru projektu.

## <a name="reserved-and-well-known-properties"></a>Vyhrazené a dobře známé vlastnosti
 Následující tabulka popisuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] předdefinovaných vlastností.

| Vlastnost | Rezervované nebo dobře známé | Popis |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Rezervované | Absolutní cesta ke složce, ve které jsou právě používány binární soubory [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] (například *C:\Windows\Microsoft.Net\Framework\\\<* číslo verze >). Tato vlastnost je užitečná, pokud se musíte odkazovat na soubory v adresáři [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildExtensionsPath` | Dobře známé | Zavedeno v .NET Framework 4: neexistuje žádný rozdíl mezi výchozími hodnotami `MSBuildExtensionsPath` a `MSBuildExtensionsPath32`. Můžete nastavit proměnnou prostředí `MSBUILDLEGACYEXTENSIONSPATH` na hodnotu jinou než null, chcete-li povolit chování výchozí hodnoty `MSBuildExtensionsPath` v předchozích verzích.<br /><br /> V .NET Framework 3,5 a starších verzích se výchozí hodnota `MSBuildExtensionsPath` odkazuje na cestu podsložky MSBuild ve složce *\Program files\\* nebo *\Program Files (x86)* v závislosti na bitová verze aktuálního procesu. Například pro 32 proces na 64 počítači tato vlastnost odkazuje na složku *\Program Files (x86)* . Pro 64 proces na 64 počítači tato vlastnost odkazuje na složku *\Program Files* .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.<br /><br /> Toto umístění je užitečné místo pro vložení vlastních cílových souborů. Například vaše cílové soubory mohou být nainstalovány do *složky \Program Files\MSBuild\MyFiles\Northwind.targets* a následně importovány do souborů projektu pomocí tohoto kódu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Dobře známé | Cesta k podsložce [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ve složce *\Program Files* nebo *\Program Files (x86)* . Tato cesta vždy odkazuje na 32 složku *\Program Files (x86)* na 32 počítači a *\Program Files* na počítači s podporou 64. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath64`.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildExtensionsPath64` | Dobře známé | Cesta k podsložce [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ve složce *\Program Files* Pro 64 počítač tato cesta vždy odkazuje na složku *\Program Files* . Pro 32 počítač je tato cesta prázdná. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath32`.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildLastTaskResult` | Rezervované | `true`, zda byla předchozí úloha dokončena bez chyb (i v případě výskytu upozornění), nebo `false` v případě, že předchozí úloha obsahovala chyby. Při výskytu chyby v úloze obvykle dojde k chybě poslední věcí, ke které dojde v projektu. Hodnota této vlastnosti proto nikdy ne`false`, s výjimkou v těchto scénářích:<br /><br /> – Při nastavení atributu `ContinueOnError` [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) na hodnotu `WarnAndContinue` (nebo `true`) nebo `ErrorAndContinue`.<br /><br /> – Pokud `Target` obsahuje [element Error (MSBuild)](../msbuild/onerror-element-msbuild.md) jako podřízený element. |
| `MSBuildNodeCount` | Rezervované | Maximální počet souběžných procesů, které jsou používány při sestavování. Toto je hodnota, kterou jste zadali pro parametr **-maxcpucount** na příkazovém řádku. Pokud jste zadali parametr **-maxcpucount** bez zadání hodnoty, `MSBuildNodeCount` určuje počet procesorů v počítači. Další informace naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md) a [Souběžné sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Rezervované | Umístění 32 složky programu; například *C:\Program Files (x86)* .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildProjectDefaultTargets` | Rezervované | Úplný seznam cílů, které jsou zadány v atributu `DefaultTargets` `Project` elementu. Například následující `Project` prvek by měl hodnotu vlastnosti `MSBuildDefaultTargets` `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Rezervované | Absolutní cesta k adresáři, kde je umístěn soubor projektu, například *C:\MyCompany\MyProduct*.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildProjectDirectoryNoRoot` | Rezervované | Hodnota vlastnosti `MSBuildProjectDirectory` s výjimkou kořenové jednotky.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildProjectExtension` | Rezervované | Přípona názvu souboru projektu, včetně období; například *. proj*. |
| `MSBuildProjectFile` | Rezervované | Úplný název souboru projektu, včetně přípony názvu souboru; například *MyApp. proj*. |
| `MSBuildProjectFullPath` | Rezervované | Absolutní cesta a úplný název souboru projektu, včetně přípony názvu souboru; například *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Rezervované | Název souboru projektu bez přípony názvu souboru; například *MyApp*. |
| `MSBuildRuntimeType` | Rezervované | Typ modulu runtime, který je právě spuštěn. Představeno v MSBuild 15. Hodnota může být nedefinovaná (před MSBuild 15), `Full` označující, že nástroj MSBuild běží na desktopovém .NET Framework, `Core` označující, že nástroj MSBuild běží na .NET Core (například v `dotnet build`), nebo `Mono` označující, že nástroj MSBuild běží na mono. |
| `MSBuildStartupDirectory` | Rezervované | Absolutní cesta ke složce, ve které je volána [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pomocí této vlastnosti můžete sestavit vše pod konkrétním bodem ve stromové struktuře projektu bez vytváření *\<adresářů > soubory. proj* v každém adresáři. Místo toho máte pouze jeden projekt – například *c:\traversal.proj*, jak je znázorněno zde:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Chcete-li vytvořit libovolný bod stromu, zadejte:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko. |
| `MSBuildThisFile` | Rezervované | Část `MSBuildThisFileFullPath`název souboru a Přípona souboru. |
| `MSBuildThisFileDirectory` | Rezervované | Část `MSBuildThisFileFullPath`adresáře.<br /><br /> V cestě zahrňte konečné zpětné lomítko. |
| `MSBuildThisFileDirectoryNoRoot` | Rezervované | Část `MSBuildThisFileFullPath`adresáře s výjimkou kořenové jednotky.<br /><br /> V cestě zahrňte konečné zpětné lomítko. |
| `MSBuildThisFileExtension` | Rezervované | Část `MSBuildThisFileFullPath`přípona názvu souboru. |
| `MSBuildThisFileFullPath` | Rezervované | Absolutní cesta k souboru projektu nebo cíle, který obsahuje cíl, na kterém je spuštěný.<br /><br /> Tip: v souboru cílů můžete zadat relativní cestu, která je relativní vzhledem k souboru cílů, a není relativní vzhledem k původnímu souboru projektu. |
| `MSBuildThisFileName` | Rezervované | Část `MSBuildThisFileFullPath`název souboru bez přípony názvu souboru. |
| `MSBuildToolsPath` | Rezervované | Instalační cesta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verze, která je přidružená k hodnotě `MSBuildToolsVersion`.<br /><br /> Do cesty nezahrnujte koncové zpětné lomítko.<br /><br /> Tuto vlastnost nelze přepsat. |
| `MSBuildToolsVersion` | Rezervované | Verze sady nástrojů [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], která se používá k sestavení projektu.<br /><br /> Poznámka: sada nástrojů [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsahuje úlohy, cíle a nástroje, které se používají k sestavení aplikace. Mezi tyto nástroje patří kompilátory, jako *CSc. exe* a *Vbc. exe*. Další informace najdete v tématech [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)a [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Rezervované | Verze [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] použitá k sestavení projektu. <br /><br/> Tuto vlastnost nelze přepsat, jinak je vrácena chybová zpráva `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. |

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
* ImportGroup
* Možnost
* Když
* Případech

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

- [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
