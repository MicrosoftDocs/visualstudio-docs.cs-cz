---
title: Úloha GenerateResource – | Microsoft Docs
description: Použijte úlohu MSBuild GenerateResource – k převodu mezi soubory. txt nebo. resx a binární soubory. Resources modulu CLR (Common Language Runtime).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 810cbd4987277416b5be545603908d9818bff890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914760"
---
# <a name="generateresource-task"></a>GenerateResource – úloha

Převádí soubory *. txt* a *. resx* (formát prostředků založený na jazyce XML) *a binární soubory* modulu CLR (Common Language Runtime), které mohou být vloženy do binárního spustitelného souboru modulu runtime nebo zkompilovány do satelitních sestavení. Tato úloha se obvykle používá k převodu souborů *. txt* nebo *. resx* na soubory *. Resources* . `GenerateResource`Úkol je funkčně podobný [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `GenerateResource` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalInputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Obsahuje další vstupy pro kontrolu závislostí prováděné touto úlohou. Například soubory projektu a cíle obvykle by měly být vstupy, takže pokud jsou aktualizovány, všechny prostředky budou znovu vygenerovány.|
|`EnvironmentVariables`|Volitelný `String[]` parametr.<br /><br /> Určuje pole párů název-hodnota pro proměnné prostředí, které by měly být předány do vytvořeného *resgen.exe*, kromě (nebo selektivního přepsání) normálního bloku prostředí.|
|`ExcludedInputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje pole položek, které určují cesty, ze kterých budou během kontroly až do data ignorovány sledované vstupy.|
|`ExecuteAsTool`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je spuštěna *tlbimp.exe* a *aximp.exe* z příslušného cílového rozhraní out-of-proc pro generování potřebných sestavení obálky. Tento parametr umožňuje cílení na více verzí `ResolveComReferences` .|
|`FilesWritten`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje názvy všech souborů zapsaných na disk. To zahrnuje soubor mezipaměti, pokud existuje. Tento parametr je vhodný pro implementace čištění.|
|`MinimalRebuildFromTracking`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví přepínač, který určuje, zda bude použito sledované přírůstkové sestavení. `true`V případě, že je zapnuto přírůstkové sestavení. v opačném případě bude vynuceno opětovné sestavení.|
|`NeverLockTypeAssemblies`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda má být vytvořena nová [doména](/dotnet/api/system.appdomain) aplikace pro vyhodnocení souborů *prostředků (true) nebo* pro vytvoření nové [domény](/dotnet/api/system.appdomain) aplikace pouze v případě, že soubory prostředků odkazují na sestavení uživatele (false).|
|`OutputResources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje název generovaných souborů, například soubory *. Resources* . Pokud název nezadáte, použije se název odpovídajícího vstupního souboru a soubor *. Resources* , který je vytvořen, je umístěn v adresáři, který obsahuje vstupní soubor.|
|`PublicClass`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vytvoří třídu prostředků silného typu jako veřejnou třídu.|
|`References`|Volitelný `String[]` parametr.<br /><br /> Odkazy na typy načítání v souborech *. resx* z. datové prvky souboru *. resx* mohou mít typ .NET. Při čtení souboru *. resx* je nutné ho vyřešit. Obvykle se vyřeší úspěšně pomocí standardních pravidel načítání typu. Pokud zadáte sestavení v `References` , budou mít přednost.<br /><br /> Tento parametr není vyžadován pro prostředky silného typu.|
|`SdkToolsPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je například *resgen.exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které se mají převést. Položky předané tomuto parametru musí mít jednu z následujících přípon souborů:<br /><br /> -   *. txt*: Určuje příponu pro textový soubor, který se má převést. Textové soubory mohou obsahovat pouze řetězcové prostředky.<br />-   *. resx*: Určuje rozšíření souboru prostředků založeného na jazyce XML, které má být převedeno.<br />-   *. restext*: Určuje stejný formát jako *. txt*. Toto jiné rozšíření je užitečné, pokud chcete jasně odlišit zdrojové soubory, které obsahují prostředky z jiných zdrojových souborů v procesu sestavení.<br />-   *. Resources*: Určuje příponu pro soubor prostředků, který se má převést.|
|`StateFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cestu k volitelnému souboru mezipaměti, který se používá k urychlení kontroly závislosti odkazů ve vstupních souborech *. resx* .|
|`StronglyTypedClassName`|Volitelný `String` parametr.<br /><br /> Určuje název třídy prostředku silně typovaného typu. Pokud není tento parametr zadán, použije se základní název souboru prostředků.|
|`StronglyTypedFilename`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje název souboru pro zdrojový soubor. Není-li tento parametr zadán, název třídy je použit jako základní název souboru, přičemž přípona závisí na jazyku. Například: *MyClass.cs*.|
|`StronglyTypedLanguage`|Volitelný `String` parametr.<br /><br /> Určuje jazyk, který má být použit při generování zdroje třídy pro prostředek silného typu. Tento parametr musí odpovídat přesně jednomu z jazyků, které používá CodeDomProvider. Například: `VB` nebo `C#` .<br /><br /> Předáním hodnoty tomuto parametru dáte pokyn, aby úloha vygenerovala prostředky se silným typem.|
|`StronglyTypedManifestPrefix`|Volitelný `String` parametr.<br /><br /> Určuje obor názvů prostředku nebo předponu manifestu, který se použije ve vygenerovaném zdroji třídy pro prostředek silného typu.|
|`StronglyTypedNamespace`|Volitelný `String` parametr.<br /><br /> Určuje obor názvů, který se má použít pro zdroj vygenerovaných tříd pro prostředek se silným typem. Pokud tento parametr není zadán, všechny prostředky silného typu jsou v globálním oboru názvů.|
|`TLogReadFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které reprezentují protokoly sledování čtení.|
|`TLogWriteFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které reprezentují protokoly sledování zápisu.|
|`ToolArchitecture`|Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Slouží k určení, zda *Tracker.exe* nutné použít k vytvoření *ResGen.exe*.<br /><br /> By měl být možné analyzovat pro člen <xref:Microsoft.Build.Utilities.ExecutableType> výčtu. Pokud nástroj `String.Empty` používá heuristickou k určení výchozí architektury. By měl být možné analyzovat na člen Microsoft.Build.Utilities.Exevýčtu cutableType.|
|`TrackerFrameworkPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k příslušnému umístění .NET Framework, které obsahuje *FileTracker.dll*.<br /><br /> Pokud je nastaveno, uživatel vezme zodpovědnost za zajištění, že bitová verze *FileTracker.dll* , který předává, odpovídá bitová verze *ResGen.exe* , kterou chtějí používat. Pokud není nastavená, úloha na základě aktuální verze .NET Framework rozhodne o příslušné umístění.|
|`TrackerLogDirectory`|Volitelný `String` parametr.<br /><br /> Určuje zprostředkující adresář, do kterého se budou umístit protokoly sledování z běhu této úlohy.|
|`TrackerSdkPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k příslušnému umístění Windows SDK, které obsahuje *Tracker.exe*.<br /><br /> Pokud je nastaveno, uživatel vezme zodpovědnost za zajištění, že bitová verze *Tracker.exe* , který předává, odpovídá bitová verze *ResGen.exe* , kterou chtějí používat. Pokud není nastaven, úloha podle aktuálního Windows SDK určí příslušné umístění.|
|`TrackFileAccess`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud má hodnotu true, použije se k překladu relativních cest k souborům Adresář vstupního souboru.|
|`UseSourcePath`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` Určuje, zda má být adresář vstupního souboru použit k překladu relativních cest k souborům.|

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že soubory *. resx* mohou obsahovat odkazy na jiné soubory prostředků, není dostačující pouze k porovnání časových razítek souborů *. resx* a *. Resources* , aby bylo možné zjistit, zda jsou výstupy v aktuálním stavu. Místo toho `GenerateResource` úloha sleduje odkazy v souborech *. resx* a kontroluje také časová razítka propojených souborů. To znamená, že byste neměli obecně používat `Inputs` `Outputs` atributy a v cíli obsahující `GenerateResource` úkol, protože by to mohlo způsobit jeho přeskočení, když by se měl skutečně spustit.

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

Při použití MSBuild 4,0 k cílení na projekty .NET 3,5 může sestavení selhat u prostředků x86. Pokud chcete tento problém obejít, můžete vytvořit cíl jako sestavení AnyCPU.

## <a name="example"></a>Příklad

Následující příklad používá `GenerateResource` úlohu k vygenerování souborů *. Resources* ze souborů určených `Resx` kolekcí položek.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

`GenerateResource`Úkol používá \<LogicalName> Metadata \<EmbeddedResource> položky k pojmenování prostředku, který je vložen do sestavení.

Za předpokladu, že sestavení má název myAssembly, následující kód vygeneruje vložený prostředek s názvem *someQualifier. someResource. Resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<LogicalName> metadat by měl prostředek název *MyAssembly. MyResource. Resources*.  Tento příklad se vztahuje pouze na proces sestavení Visual Basic a Visual C#.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
