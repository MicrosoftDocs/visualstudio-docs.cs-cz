---
title: Generateresource – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6686e34ade66a3d4f2ec8ef23c9649bb5d7a1c47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212495"
---
# <a name="generateresource-task"></a>GenerateResource – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Převede mezi txt a souborů .resx (formát založený na formátu XML prostředků) a common language runtime binárních souborů .resources, které může být vložen do binárního spustitelného souboru modulu nebo zkompilovány do satelitních sestavení. Tato úloha je obvykle používána pro převod souborů .txt nebo .resx na soubory Resource. `GenerateResource` Úkolu je funkčně podobný [resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GenerateResource` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalInputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Obsahuje další vstupy Kontrola závislosti, které se provádí tento úkol. Soubory projektu a cíle obvykle by měl být například vstupy, tak, že pokud jsou aktualizováni, všechny prostředky budou znovu vygenerovány.|  
|`EnvironmentVariables`|Volitelné `String[]` parametru.<br /><br /> Určuje pole dvojic název hodnota prostředí proměnné, které by měly být předány vytvořenému resgen.exe kromě (nebo selektivně přepsání) blok regulární prostředí.|  
|`ExcludedInputPaths`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje pole položek, které určují cesty, ze kterých budou ignorovány sledované vstupy během aktuální kontroly.|  
|`ExecuteAsTool`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, spustí tlbimp.exe a aximp.exe od příslušné cílové rozhraní framework z – mimoprocesovou ke generování sestavení obálky nezbytné. Tento parametr umožňuje cílení na více platforem z `ResolveComReferences`.|  
|`FilesWritten`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje názvy všech souborů zapsaných na disk. To zahrnuje souboru mezipaměti, pokud existuje. Tento parametr je užitečný pro implementace vyčistit.|  
|`MinimalRebuildFromTracking`|Volitelné `Boolean` parametru.<br /><br /> Získává nebo nastavuje přepínač, který určuje, jestli se použije sledované přírůstkové sestavení. Pokud `true`, je zapnuto přírůstkové sestavení; v opačném případě bude vynuceno opětovné sestavení.|  
|`NeverLockTypeAssemblies`|Volitelné `Boolean` parametru.<br /><br /> Určuje název generovaných souborů, jako jsou například soubory .resources. Pokud název nezadáte, název odpovídající vstupní soubor se používá a je umístěn soubor .resources, který je vytvořen v adresáři, který obsahuje vstupní soubor.|  
|`OutputResources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje název generovaných souborů, jako jsou například soubory .resources. Pokud název nezadáte, název odpovídající vstupní soubor se používá a je umístěn soubor .resources, který je vytvořen v adresáři, který obsahuje vstupní soubor.|  
|`PublicClass`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vytvoří třídu prostředků se silnými typy jako veřejnou třídu.|  
|`References`|Volitelné `String[]` parametru.<br /><br /> Odkazy na načíst typy v souborech .resx z. Elementy datového souboru RESX může mít typ .NET. Při čtení souboru .resx to musí být vyřešeny. Obvykle se nevyřeší úspěšně pomocí standardní typ načítání pravidel. Pokud zadáte sestavení v `References`, jejich přednost.<br /><br /> Tento parametr není vyžadováno pro prostředky se silnými typy.|  
|`SdkToolsPath`|Volitelné `String` parametru.<br /><br /> Určuje cestu k sadě SDK nástroje, jako je resgen.exe.|  
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které chcete převést. Položek předaných tomuto parametru musí mít jednu z následujících přípon:<br /><br /> -   `.txt`: Určuje příponu textový soubor převést. Textové soubory mohou obsahovat pouze řetězcové prostředky.<br />-   `.resx`: Určuje rozšíření pro soubor prostředků založený na formátu XML pro převod.<br />-   `.restext`: Určuje stejný formát jako .txt. Toto různých rozšíření je užitečné, pokud budete chtít jasně odlišit zdrojové soubory, které obsahují prostředky z jiných zdrojových souborech v procesu sestavení.<br />-   `.resources`: Určuje rozšíření souboru prostředků pro převod.|  
|`StateFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje cestu k souboru volitelné mezipaměti, který se používá ke zrychlení závislost kontroly odkazů na vstupní soubory .resx.|  
|`StronglyTypedClassName`|Volitelné `String` parametru.<br /><br /> Určuje název třídy pro třídu prostředků se silnými typy. Pokud není tento parametr zadán, je použít základní název souboru prostředků.|  
|`StronglyTypedFilename`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje název souboru pro zdrojový soubor. Pokud tento parametr nezadáte, název třídy se používá jako základní název souboru s příponou závisí na jazyku. Příklad: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Volitelné `String` parametru.<br /><br /> Určuje jazyk, který má použít při generování třídy zdroje pro prostředek silného typu. Tento parametr musí odpovídat přesně jeden z těchto jazyků používané CodeDomProvider. Příklad: `VB` nebo `C#`.<br /><br /> Předejte hodnotu pro tento parametr, dáte pokyn úkolů ke generování prostředky se silnými typy.|  
|`StronglyTypedManifestPrefix`|Volitelné `String` parametru.<br /><br /> Určuje předponu oboru názvů nebo manifest prostředků pro účely prostředků se silnými typy ve vygenerované třídě zdroje.|  
|`StronglyTypedNamespace`|Volitelné `String` parametru.<br /><br /> Určuje obor názvů pro zdroj generovaná třída prostředků se silnými typy. Pokud není tento parametr zadán, jsou všechny prostředky se silnými typy v globálním oboru názvů.|  
|`TLogReadFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole objektů, které představují čtení protokoly sledování.|  
|`TLogWriteFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které představují zápis protokoly sledování.|  
|`ToolArchitecture`|Volitelné [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Slouží k určení, zda je potřeba použít ResGen.exe nejde vytvořit podřízený Tracker.exe.<br /><br /> By měl být analyzovatelný členovi <xref:Microsoft.Build.Utilities.ExecutableType> výčtu. Pokud `String.Empty`, používá k určení výchozí architektura heuristické metody. By měl být na člena výčtu Microsoft.Build.Utilities.ExecutableType možné analyzovat.|  
|`TrackerFrameworkPath`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje cestu k odpovídající umístění rozhraní .NET Framework, která obsahuje FileTracker.dll.<br /><br /> Pokud sada, uživatel přebírá odpovědnost za zajištění, že odpovídá počtu bitů FileTracker.dll, který předávají bitové verze nástroje ResGen.exe, které mají v úmyslu použít. Pokud není sada, rozhodne úlohy do příslušného umístění na základě aktuální verze rozhraní .NET Framework.|  
|`TrackerLogDirectory`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje zprostředkující adresář, do kterého bude umístěn protokoly sledování od spuštění této úlohy.|  
|`TrackerSdkPath`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje cestu k odpovídající umístění sady Windows SDK obsahující Tracker.exe.<br /><br /> Pokud sada, uživatel přebírá odpovědnost za zajištění, že odpovídá počtu bitů Tracker.exe, který předávají bitové verze nástroje ResGen.exe, které mají v úmyslu použít. Pokud není sada, rozhodne úlohy do příslušného umístění podle aktuální sady Windows SDK.|  
|`TrackFileAccess`|Volitelná [logická hodnota] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Při hodnotě true se vstupního souboru se použije k vyřešení relativní cesty k souboru.|  
|`UseSourcePath`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že adresář vstupního souboru se má použít k vyřešení relativní cesty k souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že soubory .resx mohou obsahovat odkazy na další soubory prostředků, není dostatečná k jednoduše porovnat resx a Resource časová razítka souborů jestli výstupy jsou aktuální. Místo toho `GenerateResource` úkol sleduje odkazy v souborech .resx a zkontroluje časová razítka propojené soubory. To znamená, že byste neměli používat obecně `Inputs` a `Outputs` atributy cílové obsahující `GenerateResource` úlohy, což může způsobit ji přeskočit, pokud by měl běžet ve skutečnosti.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
 Při použití nástroje MSBuild 4.0 do projektů cílového rozhraní .NET 3.5, může být sestavení při x86 prostředky. Chcete-li tento problém vyřešit, můžete vytvořit cíl sestavení AnyCPU.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `GenerateResource` úkolů ke generování souborů .resources z soubory určené `Resx` kolekci položek.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Úloh používá \<LogicalName > metadata \<EmbeddedResource > položka název prostředku, který je vložen do sestavení.  
  
 Za předpokladu, že sestavení má název myAssembly, následující kód vygeneruje vložený prostředek s názvem someQualifier.someResource.resources:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Bez \<LogicalName > metadata prostředku by se pojmenoval myAssembly.myResource.resources.  Tento příklad se týká jenom procesem sestavení jazyka Visual Basic a Visual C#.  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



