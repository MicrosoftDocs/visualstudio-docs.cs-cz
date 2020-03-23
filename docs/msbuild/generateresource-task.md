---
title: Úloha generovat zdroje | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634055"
---
# <a name="generateresource-task"></a>GenerateResource – úloha

Převádí mezi soubory *TXT* a *.resx* (formát prostředků založený na XML) a soubory *binárních prostředků .resources* v běžném jazyce, které mohou být vloženy do binárního spustitelného souboru runtime nebo zkompilovány do satelitních sestavení. Tato úloha se obvykle používá k převodu souborů *TXT* nebo *Resx* na soubory *.resources.* Úloha `GenerateResource` je funkčně podobná [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `GenerateResource` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalInputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Obsahuje další vstupy pro kontrolu závislostí provedené tímto úkolem. Například projekt a cíle soubory obvykle by měly být vstupy, tak, že pokud jsou aktualizovány, všechny prostředky jsou obnoveny.|
|`EnvironmentVariables`|Volitelný `String[]` parametr.<br /><br /> Určuje pole dvojic název-hodnota proměnných prostředí, které by měly být předány spawned *resgen.exe*, kromě (nebo selektivně přepsání) bloku běžného prostředí.|
|`ExcludedInputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje pole položek, které určují cesty, ze kterých budou sledované vstupy během kontroly aktuálního stavu ignorovány.|
|`ExecuteAsTool`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`spustí *tlbimp.exe* a *aximp.exe* z příslušného cílového rozhraní mimo proc a vygeneruje potřebné sestavy obálky. Tento parametr umožňuje vícenásobné cílení . `ResolveComReferences`|
|`FilesWritten`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje názvy všech souborů zapsaných na disk. To zahrnuje soubor mezipaměti, pokud existuje. Tento parametr je užitečný pro implementace Clean.|
|`MinimalRebuildFromTracking`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví přepínač, který určuje, zda bude použito sledované přírůstkové sestavení. Pokud `true`je přírůstkové sestavení zapnuto; v opačném případě bude vynuceno obnovení.|
|`NeverLockTypeAssemblies`|Volitelný `Boolean` parametr.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda chcete vytvořit novou [AppDomain](/dotnet/api/system.appdomain) k vyhodnocení souborů prostředků *(.resx)*(true) nebo vytvořit novou [AppDomain](/dotnet/api/system.appdomain) pouze v případě, že soubory prostředků odkazují na sestavení uživatele (false).|
|`OutputResources`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje název generovaných souborů, například souborů *.resources.* Pokud název nezadáte, bude použit název odpovídajícího vstupního souboru a vytvořený soubor *.resources* bude umístěn do adresáře, který obsahuje vstupní soubor.|
|`PublicClass`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, vytvoří třídu prostředků silného typu jako veřejnou třídu.|
|`References`|Volitelný `String[]` parametr.<br /><br /> Odkazy na načtení typů v souborech *RESX* z. Datové prvky souboru *RESX* mohou mít typ .NET. Při čtení souboru *Resx* je to nutné vyřešit. Obvykle je úspěšně vyřešen pomocí standardních pravidel načítání typu. Pokud zadáte sestavení `References`v , mají přednost.<br /><br /> Tento parametr není vyžadován pro prostředky silného typu.|
|`SdkToolsPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, například *resgen.exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které chcete převést. Položky předané tomuto parametru musí mít jednu z následujících přípon souborů:<br /><br /> -   *.txt*: Určuje příponu textového souboru, který má být převeden. Textové soubory mohou obsahovat pouze prostředky řetězce.<br />-   *.resx*: Určuje příponu pro převést soubor prostředků xml.<br />-   *.restext*: Určuje stejný formát jako *soubor TXT*. Toto jiné rozšíření je užitečné, pokud chcete jasně rozlišit zdrojové soubory, které obsahují prostředky z jiných zdrojových souborů v procesu sestavení.<br />-   *.resources*: Určuje příponu pro převedení souboru prostředků.|
|`StateFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje cestu k volitelnému souboru mezipaměti, který se používá k urychlení kontroly závislostí odkazů ve vstupních souborech *.resx.*|
|`StronglyTypedClassName`|Volitelný `String` parametr.<br /><br /> Určuje název třídy pro třídu prostředků silného typu. Pokud tento parametr není zadán, použije se základní název souboru prostředků.|
|`StronglyTypedFilename`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje název souboru zdrojového souboru. Pokud tento parametr není zadán, název třídy se používá jako název základního souboru, s příponou v závislosti na jazyku. Například: *MyClass.cs*.|
|`StronglyTypedLanguage`|Volitelný `String` parametr.<br /><br /> Určuje jazyk, který se má použít při generování zdroje třídy pro prostředek silného typu. Tento parametr musí odpovídat přesně jeden z jazyků používaných CodeDomProvider. Například: `VB` `C#`nebo .<br /><br /> Předáním hodnoty tomuto parametru dáte pokyn úkolu, aby generoval prostředky silného typu.|
|`StronglyTypedManifestPrefix`|Volitelný `String` parametr.<br /><br /> Určuje obor názvů prostředků nebo předponu manifestu, která má být používána ve zdroji generované třídy pro prostředek silného typu.|
|`StronglyTypedNamespace`|Volitelný `String` parametr.<br /><br /> Určuje obor názvů, který se má použít pro generovaný zdroj třídy pro prostředek silného typu. Pokud tento parametr není zadán, všechny prostředky silného typu jsou v globálním oboru názvů.|
|`TLogReadFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které představují protokoly sledování čtení.|
|`TLogWriteFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které představují protokoly sledování zápisu.|
|`ToolArchitecture`|Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Používá se k určení, zda *tracker.exe* je třeba použít k tření *ResGen.exe*.<br /><br /> By měla být analyzovatelná pro <xref:Microsoft.Build.Utilities.ExecutableType> člena výčtu. Pokud `String.Empty`aplikace používá k určení výchozí architektury heuristickou architekturu. By měla být analyzovatelná na člena výčtu Microsoft.Build.Utilities.ExecutableType.|
|`TrackerFrameworkPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k příslušnému umístění rozhraní .NET Framework, které obsahuje *soubor FileTracker.dll*.<br /><br /> Pokud je nastavena, uživatel přebírá odpovědnost za to, že bitness *SouborTracker.dll,* které předávají odpovídá bitness *ResGen.exe,* které mají v úmyslu použít. Pokud není nastavena, úkol rozhodne o vhodném umístění na základě aktuální verze rozhraní .NET Framework.|
|`TrackerLogDirectory`|Volitelný `String` parametr.<br /><br /> Určuje zprostředkující adresář, do kterého budou umístěny protokoly sledování ze spuštění této úlohy.|
|`TrackerSdkPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k příslušnému umístění sady Windows SDK, které obsahuje *nástroj Sledování.exe*.<br /><br /> Pokud je nastavena, uživatel přebírá odpovědnost za to, že bitness *Tracker.exe,* které předávají odpovídá bitness *ResGen.exe,* které mají v úmyslu použít. Pokud není nastavena, úkol rozhodne o vhodném umístění na základě aktuální sady Windows SDK.|
|`TrackFileAccess`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud true, adresář vstupního souboru se používá pro řešení relativnícesty souborů.|
|`UseSourcePath`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`aplikace určuje, že adresář vstupního souboru má být použit k řešení relativních cest k souborům.|

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že soubory *RESX* mohou obsahovat odkazy na jiné soubory prostředků, nestačí jednoduše porovnat časová razítka *souborů Resx* a *.resources,* abyste zjistili, zda jsou výstupy aktuální. Místo toho `GenerateResource` úkol sleduje odkazy v souborech *RESX* a kontroluje také časová razítka propojených souborů. To znamená, že byste `Inputs` `Outputs` obecně neměli používat a `GenerateResource` atributy na cíl obsahující úlohu, protože to může způsobit, že bude přeskočen, když by měl skutečně spustit.

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

Při použití MSBuild 4.0 cílit .NET 3.5 projekty, sestavení může selhat na x86 prostředky. Chcete-li tento problém vyřešit, můžete vytvořit cíl jako sestavení AnyCPU.

## <a name="example"></a>Příklad

Následující příklad používá `GenerateResource` tuto úlohu ke generování souborů `Resx` *.resources* ze souborů určených kolekcí položek.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Úloha `GenerateResource` používá \<metadata LogicalName \<> položky EmbeddedResource> k pojmenování prostředku, který je vložen do sestavení.

Za předpokladu, že sestavení je pojmenováno myAssembly, následující kód generuje vložený prostředek s názvem *someQualifier.someResource.resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<LogicalName> by se prostředek jmenoval *myAssembly.myResource.resources*.  Tento příklad platí pouze pro proces sestavení jazyka Visual Basic a Visual C#.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
