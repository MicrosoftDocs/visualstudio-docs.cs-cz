---
title: Generateresource – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c830b640b3efb4e963d62402bbf68d1bc7dff0e9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176951"
---
# <a name="generateresource-task"></a>GenerateResource – úloha
Převádí mezi *.txt* a *RESX* (formát založený na formátu XML prostředků) soubory a binární common language runtime *.resources* soubory, které může být vložen do binárního modulu runtime spustitelný soubor nebo soubor zkompilovaný do satelitních sestavení. Tato úloha je obvykle používána pro převod *.txt* nebo *RESX* soubory *.resources* soubory. `GenerateResource` Úkolu je funkčně podobný [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GenerateResource` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AdditionalInputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Obsahuje další vstupy Kontrola závislosti, které se provádí tento úkol. Soubory projektu a cíle obvykle by měl být například vstupy, tak, že pokud jsou aktualizováni, všechny prostředky budou znovu vygenerovány.|  
|`EnvironmentVariables`|Volitelné `String[]` parametru.<br /><br /> Určuje pole dvojic název hodnota proměnných prostředí, které mají být předány do nové kopie *resgen.exe*, v dodatku (nebo selektivně přepsání) blok regulární prostředí.|  
|`ExcludedInputPaths`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje pole položek, které určují cesty, ze kterých budou ignorovány sledované vstupy během aktuální kontroly.|  
|`ExecuteAsTool`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, spustí *tlbimp.exe* a *aximp.exe* z příslušné cílové rozhraní framework z – mimoprocesovou ke generování sestavení obálky nezbytné. Tento parametr umožňuje cílení na více platforem z `ResolveComReferences`.|  
|`FilesWritten`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje názvy všech souborů zapsaných na disk. To zahrnuje souboru mezipaměti, pokud existuje. Tento parametr je užitečný pro implementace vyčistit.|  
|`MinimalRebuildFromTracking`|Volitelné `Boolean` parametru.<br /><br /> Získává nebo nastavuje přepínač, který určuje, jestli se použije sledované přírůstkové sestavení. Pokud `true`, je zapnuto přírůstkové sestavení; v opačném případě bude vynuceno opětovné sestavení.|  
|`NeverLockTypeAssemblies`|Volitelné `Boolean` parametru.<br /><br /> Získá nebo nastaví logickou hodnotu, která určuje, zda chcete vytvořit nový [AppDomain](/dotnet/api/system.appdomain) vyhodnotit prostředky (*RESX*) soubory (pravda) nebo vytvořit nový [AppDomain](/dotnet/api/system.appdomain) pouze tehdy, když soubory prostředků odkazují na sestavení uživatele (false).|  
|`OutputResources`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje název generovaných souborů, jako například *.resources* soubory. Pokud nezadáte název, použije se název odpovídající vstupního souboru a *.resources* soubor, který je vytvořen je umístěn v adresáři, který obsahuje vstupní soubor.|  
|`PublicClass`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, vytvoří třídu prostředků se silnými typy jako veřejnou třídu.|  
|`References`|Volitelné `String[]` parametru.<br /><br /> Odkazy na načíst typy v *RESX* souborů z doručené pošty. *resx* soubor datové prvky, může mít typ .NET. Když *RESX* soubor je pro čtení, musí jít přeložit. Obvykle se nevyřeší úspěšně pomocí standardní typ načítání pravidel. Pokud zadáte sestavení v `References`, jejich přednost.<br /><br /> Tento parametr není vyžadováno pro prostředky se silnými typy.|  
|`SdkToolsPath`|Volitelné `String` parametru.<br /><br /> Určuje cestu k sadě SDK nástroje, jako *resgen.exe*.|  
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které chcete převést. Položek předaných tomuto parametru musí mít jednu z následujících přípon:<br /><br /> -   *.txt*: Určuje příponu textový soubor převést. Textové soubory mohou obsahovat pouze řetězcové prostředky.<br />-   *resx*: Určuje rozšíření pro soubor prostředků založený na formátu XML pro převod.<br />-   *.restext*: Určuje stejný formát jako *.txt*. Toto různých rozšíření je užitečné, pokud budete chtít jasně odlišit zdrojové soubory, které obsahují prostředky z jiných zdrojových souborech v procesu sestavení.<br />-   *.Resources*: Určuje rozšíření souboru prostředků pro převod.|  
|`StateFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje cestu k souboru volitelné mezipaměti, který se používá ke zrychlení kontrolu odkazů na závislosti *RESX* vstupních souborů.|  
|`StronglyTypedClassName`|Volitelné `String` parametru.<br /><br /> Určuje název třídy pro třídu prostředků se silnými typy. Pokud není tento parametr zadán, je použít základní název souboru prostředků.|  
|`StronglyTypedFilename`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje název souboru pro zdrojový soubor. Pokud tento parametr nezadáte, název třídy se používá jako základní název souboru s příponou závisí na jazyku. Příklad: *MyClass.cs*.|  
|`StronglyTypedLanguage`|Volitelné `String` parametru.<br /><br /> Určuje jazyk, který má použít při generování třídy zdroje pro prostředek silného typu. Tento parametr musí odpovídat přesně jeden z těchto jazyků používané CodeDomProvider. Příklad: `VB` nebo `C#`.<br /><br /> Předejte hodnotu pro tento parametr, dáte pokyn úkolů ke generování prostředky se silnými typy.|  
|`StronglyTypedManifestPrefix`|Volitelné `String` parametru.<br /><br /> Určuje předponu oboru názvů nebo manifest prostředků pro účely prostředků se silnými typy ve vygenerované třídě zdroje.|  
|`StronglyTypedNamespace`|Volitelné `String` parametru.<br /><br /> Určuje obor názvů pro zdroj generovaná třída prostředků se silnými typy. Pokud není tento parametr zadán, jsou všechny prostředky se silnými typy v globálním oboru názvů.|  
|`TLogReadFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole objektů, které představují čtení protokoly sledování.|  
|`TLogWriteFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr jen pro čtení.<br /><br /> Získá pole položek, které představují zápis protokoly sledování.|  
|`ToolArchitecture`|Volitelné <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Umožňuje určit, jestli *Tracker.exe* musí být používán nejde vytvořit podřízený *ResGen.exe*.<br /><br /> By měl být analyzovatelný členovi <xref:Microsoft.Build.Utilities.ExecutableType> výčtu. Pokud `String.Empty`, používá k určení výchozí architektura heuristické metody. By měl být na člena výčtu Microsoft.Build.Utilities.ExecutableType možné analyzovat.|  
|`TrackerFrameworkPath`|Volitelné `String` parametru.<br /><br /> Určuje cestu k odpovídající umístění rozhraní .NET Framework, která obsahuje *FileTracker.dll*.<br /><br /> Pokud nastavíte, uživatel provede odpovědnost za zajištění, že počtu bitů *FileTracker.dll* bude úspěšné odpovídá počtu bitů *ResGen.exe* , které mají v úmyslu použít. Pokud není sada, rozhodne úlohy do příslušného umístění na základě aktuální verze rozhraní .NET Framework.|  
|`TrackerLogDirectory`|Volitelné `String` parametru.<br /><br /> Určuje zprostředkující adresář, do kterého bude umístěn protokoly sledování od spuštění této úlohy.|  
|`TrackerSdkPath`|Volitelné `String` parametru.<br /><br /> Určuje cestu k odpovídající umístění sady Windows SDK obsahující *Tracker.exe*.<br /><br /> Pokud nastavíte, uživatel provede odpovědnost za zajištění, že počtu bitů *Tracker.exe* bude úspěšné odpovídá počtu bitů *ResGen.exe* , které mají v úmyslu použít. Pokud není sada, rozhodne úlohy do příslušného umístění podle aktuální sady Windows SDK.|  
|`TrackFileAccess`|Volitelné <xref:System.Boolean> parametru.<br /><br /> Při hodnotě true se vstupního souboru se použije k vyřešení relativní cesty k souboru.|  
|`UseSourcePath`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, určuje, že adresář vstupního souboru se má použít k vyřešení relativní cesty k souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Protože *RESX* soubory mohou obsahovat odkazy na jiné soubory prostředků, nestačí jednoduše porovnat *RESX* a *.resources* souboru časová razítka, jestli jsou výstupy aktuální. Místo toho `GenerateResource` úkol sleduje odkazy v *RESX* soubory a zkontroluje časová razítka propojené soubory. To znamená, že byste neměli používat obecně `Inputs` a `Outputs` atributy cílové obsahující `GenerateResource` úlohy, což může způsobit ji přeskočit, pokud by měl běžet ve skutečnosti.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
 Při použití nástroje MSBuild 4.0 do projektů cílového rozhraní .NET 3.5, může být sestavení při x86 prostředky. Chcete-li tento problém vyřešit, můžete vytvořit cíl sestavení AnyCPU.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `GenerateResource` úkolů ke generování *.resources* soubory z určené soubory `Resx` kolekci položek.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Úloh používá \<LogicalName > metadata \<EmbeddedResource > položka název prostředku, který je vložen do sestavení.  
  
 Za předpokladu, že sestavení má název myAssembly, následující kód vygeneruje vložený prostředek s názvem *someQualifier.someResource.resources*:  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Bez \<LogicalName > metadata, by se pojmenoval prostředek *myAssembly.myResource.resources*.  Tento příklad se týká jenom procesem sestavení jazyka Visual Basic a Visual C#.  
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
