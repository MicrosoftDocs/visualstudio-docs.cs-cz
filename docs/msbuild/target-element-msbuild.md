---
title: Cíl – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9085861418f11ed63f76a6493a6927c63530759b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918789"
---
# <a name="target-element-msbuild"></a>Target – element (MSBuild)
Obsahuje sadu úkolů pro [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] provádět sekvenčně.  

 \<Project>  
 \<Cíl >  

## <a name="syntax"></a>Syntaxe  

```xml  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <OnError... />  
</Target>  
```  

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  

### <a name="attributes"></a>Atributy  

|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadovaný atribut.<br /><br /> Název cíle|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Pokud je podmínka vyhodnocena jako `false`, cíl neprovede tělo cíl nebo veškerých cílů, které jsou nastaveny v `DependsOnTargets` atribut. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Nepovinný atribut.<br /><br /> Soubory, které tvoří vstupy do tohoto cíle. Více souborů jsou odděleny středníky. Časová razítka souborů bude porovnána s časovými razítky souborů v `Outputs` k určení, zda `Target` je aktuální. Další informace najdete v tématu [přírůstková sestavení](../msbuild/incremental-builds.md), [postupy: přírůstkové sestavování](../msbuild/how-to-build-incrementally.md), a [transformuje](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Nepovinný atribut.<br /><br /> Soubory, které výstupy do tohoto cíle. Více souborů jsou odděleny středníky. Časová razítka souborů bude porovnána s časovými razítky souborů v `Inputs` k určení, zda `Target` je aktuální. Další informace najdete v tématu [přírůstková sestavení](../msbuild/incremental-builds.md), [postupy: přírůstkové sestavování](../msbuild/how-to-build-incrementally.md), a [transformuje](../msbuild/msbuild-transforms.md).|  
|`Returns`|Nepovinný atribut.<br /><br /> Sadu položek, které bude k dispozici pro úlohy, které vyvolávají tento cíl, například úlohy nástroje MSBuild. Několik cílů jsou odděleny středníky. Pokud nemají cíle v souboru `Returns` atributy, výstupy atributy se používají místo pro tento účel.|  
|`KeepDuplicateOutputs`|Volitelný logický atribut.<br /><br /> Pokud `true`, se zaznamenávají více odkazů na stejné položky v návratových hodnotách elementu target.  Ve výchozím nastavení, tento atribut je `false`.|  
|`BeforeTargets`|Nepovinný atribut.<br /><br /> Středníkem oddělený seznam cílových názvů.  Při zadán, znamená to, že před zadaného cíle nebo cílů by měl být spuštěn tento cíl. Díky tomu Autor projektu rozšíření existující sady cílů beze jejich změny přímo. Další informace najdete v tématu [pořadí sestavení cílové](../msbuild/target-build-order.md).|  
|`AfterTargets`|Nepovinný atribut.<br /><br /> Středníkem oddělený seznam cílových názvů. Při zadán, znamená to, že po zadaný cíl nebo cíle by měl být spuštěn tento cíl. Díky tomu Autor projektu rozšíření existující sady cílů beze jejich změny přímo. Další informace najdete v tématu [pořadí sestavení cílové](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Nepovinný atribut.<br /><br /> Může dojít, cíle, které je třeba spustit předtím, než můžete spustit tento cíl nebo analýza závislosti nejvyšší úrovně. Několik cílů jsou odděleny středníky.|  
|`Label`|Nepovinný atribut.<br /><br /> Identifikátor, který může identifikaci nebo třídění systémových a uživatelských elementů.|  

### <a name="child-elements"></a>Podřízené prvky  

| Prvek | Popis |
| - | - |
| [Úloha](../msbuild/task-element-msbuild.md) | Vytvoří a spustí instanci [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úloh. V cíli může být nula nebo více úloh. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Obsahuje sadu uživatelem definované `Property` elementy. Od verze rozhraní .NET Framework 3.5 `Target` element může obsahovat `PropertyGroup` elementy. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Obsahuje sadu uživatelem definované `Item` elementy. Od verze rozhraní .NET Framework 3.5 `Target` element může obsahovat `ItemGroup` elementy. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md). |
| [Onerror –](../msbuild/onerror-element-msbuild.md) | Způsobí, že jeden nebo více cílů ke spuštění, pokud `ContinueOnError` atribut je ErrorAndStop (nebo `false`) pro neúspěšné úlohy. Může být nula nebo více `OnError` prvky v cíli. Pokud `OnError` prvky jsou k dispozici, musí být poslední prvky v `Target` elementu.<br /><br /> Informace o tom, `ContinueOnError` atributu naleznete v tématu [Task – element (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Nadřazené prvky  

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] souboru projektu. |

## <a name="remarks"></a>Poznámky  
 V době běhu je zadán první cíl ke spuštění. Cíle může mít závislosti na jiných cílů. Například cíl nasazení závisí na cíli pro kompilaci. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Modul provádí v pořadí, v jakém jsou uvedeny v závislosti `DependsOnTargets` atribut zleva doprava. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).  

 Cíl pouze provádí jednou během sestavení, i v případě, že více než jeden cíl závislý na něj.  

 Pokud je cíl vynechán, protože jeho `Condition` atributů vyhodnotí jako `false`, se můžete stále provést Pokud je vyvolána později v sestavení a jeho `Condition` atributů vyhodnotí jako `true` v daném čase.  

 Před MSBuild 4 `Target` vrátí všechny položky, které byly zadány v `Outputs` atribut.  K tomuto účelu nástroj MSBuild museli zaznamenávat položky v případě, že je požadovali úloh později v sestavení. Protože neexistoval způsob, jak k označení cíle, které má výstupy, které by vyžadovaly volajícím, MSBuild sbírají všechny položky ze všech `Outputs` ve všech vyvolána `Target`s. Tato realizace škálování problémy pro sestavení, která má velký počet položek výstup.  

 Pokud uživatel zadá `Returns` na žádném `Target` prvku v projektu, pak pouze ty `Target`, které mají `Returns` atribut zaznamenávat tyto položky.  

 A `Target` může obsahovat i `Outputs` atribut a `Returns` atribut.  `Outputs` se používá s `Inputs` k určení, zda je aktuální cíl. `Returns`, pokud existuje, přepíše hodnotu `Outputs` určit položky, které jsou vráceny volajícímu.  Pokud `Returns` není k dispozici, pak `Outputs` bude k dispozici volajících s výjimkou v případě popsané výše.  

 Před 4 nástroje MSBuild, který kdykoli `Target` zahrnuté více odkazů na stejné položky v jeho `Outputs`, by zaznamenávají tyto duplicitní položky. Ve velmi velké sestavení, který měl velký počet výstupů a mnoho vzájemné závislosti projektu, došlo by k vzájemnému velké množství paměti, aby byly ztraceny, protože duplicitní položky nebyly žádné použití. Když `KeepDuplicateOutputs` atribut je nastaven na `true`, zaznamenávají tyto duplikáty.  

## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `Target` element, který se spustí `Csc` úloh.  

```xml  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Viz také:  
 [Cíle](../msbuild/msbuild-targets.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
