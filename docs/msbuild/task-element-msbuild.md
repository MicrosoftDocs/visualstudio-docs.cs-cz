---
title: Úloha – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 512675f0752f675bd393f324220eece87301af8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914824"
---
# <a name="task-element-msbuild"></a>Task – element (MSBuild)
Vytvoří a spustí instanci [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úloh. Název elementu je určen název úkolu vytváří.  

 \<Project>  
 \<Cíl >  

## <a name="syntax"></a>Syntaxe  

```xml  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  

### <a name="attributes"></a>Atributy  

|Atribut|Popis|  
|---------------|-----------------|  
|`Condition`|Nepovinný atribut. Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Nepovinný atribut. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Při selhání úkolu, následné úlohy v [cílové](../msbuild/target-element-msbuild.md) elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Při selhání úkolu, následné úlohy v `Target` elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považována za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Při selhání úkolu, ve zbývajících úkolech v `Target` elementu a sestavení nejsou provedeny a celé `Target` elementu a sestavení se považuje za neúspěšný.<br /><br /> Verze rozhraní .NET Framework před 4.5 podporována pouze `true` a `false` hodnoty.<br /><br /> Další informace najdete v tématu [postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Vyžaduje-li třída úlohy obsahuje jeden nebo více vlastností označené `[Required]` atribut.<br /><br /> Parametr uživatelského úkolu, který obsahuje hodnotu parametru jako hodnotu. Může být libovolný počet parametrů `Task` element s každý atribut je namapovaný na vlastnost ve třídě úlohy .NET.|  

### <a name="child-elements"></a>Podřízené prvky  

|Prvek|Popis|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Ukládá výstup z úlohy v souboru projektu. Může být nula nebo více `Output` elementů v rámci úlohy.|  

### <a name="parent-elements"></a>Nadřazené prvky  

| Prvek | Popis |
| - | - |
| [Cíl](../msbuild/target-element-msbuild.md) | Prvek kontejneru pro [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úlohy. |

## <a name="remarks"></a>Poznámky  
 A `Task` prvek [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubor projektu vytvoří instanci úlohy, nastaví vlastnosti a spustí ho. `Output` Element ukládá výstupní parametry ve vlastnostech nebo položky se použije jinde v souboru projektu.  

 Pokud tam nějaké jsou [onerror –](../msbuild/onerror-element-msbuild.md) prvky v nadřazeném prvku `Target` element úlohy, se budou vyhodnocovat pořád Pokud se úloha nezdaří a `ContinueOnError` má hodnotu `false`. Další informace o úlohách najdete v části [úlohy](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří instanci [CSC – úloha](../msbuild/csc-task.md) třídy, nastaví šest vlastností a spustí úlohu. Po spuštění se hodnota `OutputAssembly` vlastnosti objektu jsou umístěny do seznamu položek s názvem `FinalAssemblyName`.  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
