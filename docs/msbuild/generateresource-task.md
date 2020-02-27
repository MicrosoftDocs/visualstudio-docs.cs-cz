---
title: Úloha GenerateResource – | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd5946612889e98b3b90f2ee3cb8665c43827a5e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634055"
---
# <a name="generateresource-task"></a>GenerateResource – úloha

Převádí soubory *. txt* a *. resx* (formát prostředků založený na jazyce XML) *a binární soubory* modulu CLR (Common Language Runtime), které mohou být vloženy do binárního spustitelného souboru modulu runtime nebo zkompilovány do satelitních sestavení. Tato úloha se obvykle používá k převodu souborů *. txt* nebo *. resx* na soubory *. Resources* . Úloha `GenerateResource` je funkčně podobná aplikaci [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry úlohy `GenerateResource`.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalInputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Obsahuje další vstupy pro kontrolu závislostí prováděné touto úlohou. Například soubory projektu a cíle obvykle by měly být vstupy, takže pokud jsou aktualizovány, všechny prostředky budou znovu vygenerovány.|
|`EnvironmentVariables`|Volitelný parametr `String[]`.<br /><br /> Určuje pole párů název-hodnota pro proměnné prostředí, které by měly být předány do vytvořeného nástroje *Resgen. exe*, a to společně s (nebo selektivním přepsáním) normálního bloku prostředí.|
|`ExcludedInputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje pole položek, které určují cesty, ze kterých budou během kontroly až do data ignorovány sledované vstupy.|
|`ExecuteAsTool`|Volitelný parametr `Boolean`.<br /><br /> V případě `true`spustí nástroj *Tlbimp. exe* a *Aximp. exe* z příslušného cílového rozhraní out-of-proc, aby se vygenerovala potřebná sestavení obálky. Tento parametr umožňuje více cílení na `ResolveComReferences`.|
|`FilesWritten`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje názvy všech souborů zapsaných na disk. To zahrnuje soubor mezipaměti, pokud existuje. Tento parametr je vhodný pro implementace čištění.|
|`MinimalRebuildFromTracking`|Volitelný parametr `Boolean`.<br /><br /> Získá nebo nastaví přepínač, který určuje, zda bude použito sledované přírůstkové sestavení. Pokud `true`, je přírůstkové sestavení zapnuté. v opačném případě bude vynuceno opětovné sestavení.|
|`NeverLockTypeAssemblies`|Volitelný parametr `Boolean`.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda má být vytvořena nová [doména](/dotnet/api/system.appdomain) aplikace pro vyhodnocení souborů*prostředků (true) nebo*pro vytvoření nové [domény](/dotnet/api/system.appdomain) aplikace pouze v případě, že soubory prostředků odkazují na sestavení uživatele (false).|
|`OutputResources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje název generovaných souborů, například soubory *. Resources* . Pokud název nezadáte, použije se název odpovídajícího vstupního souboru a soubor *. Resources* , který je vytvořen, je umístěn v adresáři, který obsahuje vstupní soubor.|
|`PublicClass`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vytvoří třídu prostředků silného typu jako veřejnou třídu.|
|`References`|Volitelný parametr `String[]`.<br /><br /> Odkazy na typy načítání v souborech *. resx* z. datové prvky souboru *. resx* mohou mít typ .NET. Při čtení souboru *. resx* je nutné ho vyřešit. Obvykle se vyřeší úspěšně pomocí standardních pravidel načítání typu. Pokud zadáte sestavení v `References`, budou mít přednost.<br /><br /> Tento parametr není vyžadován pro prostředky silného typu.|
|`SdkToolsPath`|Volitelný parametr `String`.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je *Resgen. exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které se mají převést. Položky předané tomuto parametru musí mít jednu z následujících přípon souborů:<br /><br /> -    *. txt*: Určuje příponu pro textový soubor, který se má převést. Textové soubory mohou obsahovat pouze řetězcové prostředky.<br />-    *. resx*: Určuje rozšíření souboru prostředků založeného na jazyce XML, které má být převedeno.<br />-    *. restext*: Určuje stejný formát jako *. txt*. Toto jiné rozšíření je užitečné, pokud chcete jasně odlišit zdrojové soubory, které obsahují prostředky z jiných zdrojových souborů v procesu sestavení.<br />-    *. Resources*: Určuje rozšíření pro soubor prostředků, který se má převést.|
|`StateFile`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje cestu k volitelnému souboru mezipaměti, který se používá k urychlení kontroly závislosti odkazů ve vstupních souborech *. resx* .|
|`StronglyTypedClassName`|Volitelný parametr `String`.<br /><br /> Určuje název třídy prostředku silně typovaného typu. Pokud není tento parametr zadán, použije se základní název souboru prostředků.|
|`StronglyTypedFilename`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název souboru pro zdrojový soubor. Není-li tento parametr zadán, název třídy je použit jako základní název souboru, přičemž přípona závisí na jazyku. Například: *MyClass.cs*.|
|`StronglyTypedLanguage`|Volitelný parametr `String`.<br /><br /> Určuje jazyk, který má být použit při generování zdroje třídy pro prostředek silného typu. Tento parametr musí odpovídat přesně jednomu z jazyků, které používá CodeDomProvider. Například: `VB` nebo `C#`.<br /><br /> Předáním hodnoty tomuto parametru dáte pokyn, aby úloha vygenerovala prostředky se silným typem.|
|`StronglyTypedManifestPrefix`|Volitelný parametr `String`.<br /><br /> Určuje obor názvů prostředku nebo předponu manifestu, který se použije ve vygenerovaném zdroji třídy pro prostředek silného typu.|
|`StronglyTypedNamespace`|Volitelný parametr `String`.<br /><br /> Určuje obor názvů, který se má použít pro zdroj vygenerovaných tříd pro prostředek se silným typem. Pokud tento parametr není zadán, všechny prostředky silného typu jsou v globálním oboru názvů.|
|`TLogReadFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které reprezentují protokoly sledování čtení.|
|`TLogWriteFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které reprezentují protokoly sledování zápisu.|
|`ToolArchitecture`|Volitelný parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Slouží k určení, zda je nutné použít *sledovací. exe* , aby bylo možné nástroj *Resgen. exe*vytvořit.<br /><br /> By měl být možné analyzovat pro člen <xref:Microsoft.Build.Utilities.ExecutableType> výčtu. Pokud `String.Empty`, používá heuristiku k určení výchozí architektury. By měl být možné analyzovat pro člen výčtu Microsoft. Build. Utilities. ExecutableType.|
|`TrackerFrameworkPath`|Volitelný parametr `String`.<br /><br /> Určuje cestu k příslušnému umístění .NET Framework, které obsahuje *soubor Tracks. dll*.<br /><br /> Pokud je nastaveno, uživatel vezme zodpovědnost za zajištění, že bitová verze souboru *. dll* , který předává, odpovídá bitová verze nástroje *Resgen. exe* , který hodlají použít. Pokud není nastavená, úloha na základě aktuální verze .NET Framework rozhodne o příslušné umístění.|
|`TrackerLogDirectory`|Volitelný parametr `String`.<br /><br /> Určuje zprostředkující adresář, do kterého se budou umístit protokoly sledování z běhu této úlohy.|
|`TrackerSdkPath`|Volitelný parametr `String`.<br /><br /> Určuje cestu k příslušnému umístění Windows SDK, které obsahuje *Nástroj pro sledování. exe*.<br /><br /> Pokud je nastaveno, uživatel vezme zodpovědnost za zajištění, že bitová verze souboru *. exe* , který předává, odpovídá bitová verze nástroje *Resgen. exe* , který hodlají použít. Pokud není nastaven, úloha podle aktuálního Windows SDK určí příslušné umístění.|
|`TrackFileAccess`|Volitelný parametr <xref:System.Boolean>.<br /><br /> Pokud má hodnotu true, použije se k překladu relativních cest k souborům Adresář vstupního souboru.|
|`UseSourcePath`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, určuje, že se má pro překlad relativních cest k souborům použít adresář vstupního souboru.|

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že soubory *. resx* mohou obsahovat odkazy na jiné soubory prostředků, není dostačující pouze k porovnání časových razítek souborů *. resx* a *. Resources* , aby bylo možné zjistit, zda jsou výstupy v aktuálním stavu. Místo toho `GenerateResource` úloha sleduje odkazy v souborech *. resx* a kontroluje také časová razítka propojených souborů. To znamená, že byste neměli obecně používat `Inputs` a `Outputs` atributy v cíli obsahující `GenerateResource` úkol, protože by to mohlo způsobit jeho přeskočení, když by se měl skutečně spustit.

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

Při použití MSBuild 4,0 k cílení na projekty .NET 3,5 může sestavení selhat u prostředků x86. Pokud chcete tento problém obejít, můžete vytvořit cíl jako sestavení AnyCPU.

## <a name="example"></a>Příklad

Následující příklad používá úlohu `GenerateResource` ke generování souborů *. Resources* ze souborů určených kolekcí `Resx` Item.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Úkol `GenerateResource` používá k pojmenování prostředku vloženého do sestavení \<logickou > metadat položky \<EmbeddedResource >.

Za předpokladu, že sestavení má název myAssembly, následující kód vygeneruje vložený prostředek s názvem *someQualifier. someResource. Resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<> metadat by byl prostředek pojmenovaný *MyAssembly. MyResource. Resources*.  Tento příklad se vztahuje pouze na proces Visual Basic a C# Visual Build.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
