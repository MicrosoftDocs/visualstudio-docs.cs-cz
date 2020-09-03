---
title: Task – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202271"
---
# <a name="task-element-msbuild"></a>Task – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří a spustí instanci [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkolu. Název elementu je určen názvem vytvářeného úkolu.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Nepovinný atribut. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v `Target` elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nepovede, zbývající úkoly v `Target` elementu a sestavení se nezpracují a celý `Target` element a sestavení se považuje za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporovaly pouze `true` `false` hodnoty a.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Vyžaduje se, pokud třída Task obsahuje jednu nebo více vlastností, které jsou označeny `[Required]` atributem.<br /><br /> Uživatelsky definovaný parametr úkolu, který obsahuje hodnotu parametru jako hodnotu. V elementu může být libovolný počet parametrů `Task` , přičemž každý atribut je mapován na vlastnost .NET ve třídě Task.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Výstup](../msbuild/output-element-msbuild.md)|Ukládá výstupy z úkolu v souboru projektu. V úkolu může být nula nebo více `Output` prvků.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Cílové](../msbuild/target-element-msbuild.md)|Prvek kontejneru pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úlohy.|  
  
## <a name="remarks"></a>Poznámky  
 `Task`Prvek v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu vytvoří instanci úlohy, nastaví v ní vlastnosti a provede ji. `Output`Element ukládá výstupní parametry do vlastností nebo položek, které mají být použity jinde v souboru projektu.  
  
 Pokud v nadřazeném [OnError](../msbuild/onerror-element-msbuild.md) elementu úlohy existují nějaké prvky Error `Target` , budou vyhodnoceny i v případě, že úloha selže a `ContinueOnError` má hodnotu `false` . Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří instanci třídy [úlohy CSC](../msbuild/csc-task.md) , nastaví šest vlastností a spustí úlohu. Po spuštění se hodnota `OutputAssembly` vlastnosti objektu umístí do seznamu položek s názvem `FinalAssemblyName` .  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
