---
title: UsingTask – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf2882120f2e4c27e33b105585ba56261122055d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815400"
---
# <a name="usingtask-element-msbuild"></a>UsingTask – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapuje úlohu, na kterou je odkazováno v elementu [Task](../msbuild/task-element-msbuild.md) , na sestavení, které obsahuje implementaci úlohy.  
  
 \<Project>  
 \<UsingTask>  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`AssemblyName`|`AssemblyName`Je vyžadován buď atribut, nebo `AssemblyFile` atribut.<br /><br /> Název sestavení, které chcete načíst. `AssemblyName`Atribut přijímá sestavení se silným názvem, i když silné pojmenovávání není vyžadováno. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí <xref:System.Reflection.Assembly.Load%2A> metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li `AssemblyFile` použit atribut.|  
|`AssemblyFile`|`AssemblyName` `AssemblyFile` Je vyžadován buď atribut, nebo.<br /><br /> Cesta k souboru sestavení. Tento atribut přijímá úplné cesty nebo relativní cesty. Relativní cesty jsou relativní vzhledem k adresáři souboru projektu nebo souboru cílů, kde `UsingTask` je element deklarovaný. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li `AssemblyName` použit atribut.|  
|`TaskFactory`|Nepovinný atribut.<br /><br /> Určuje třídu v sestavení, která je zodpovědná za generování instancí zadaného `Task` názvu.  Uživatel může také určit `TaskBody` jako podřízený prvek, který objekt pro vytváření úloh obdrží a použije k vygenerování úlohy. Obsah je `TaskBody` specifický pro objekt pro vytváření úloh.|  
|`TaskName`|Požadovaný atribut.<br /><br /> Název úkolu, který se má odkazovat ze sestavení. Pokud je to možné, měl by tento atribut vždy určovat celé obory názvů. Pokud existují dvojznačnosti, nástroj MSBuild zvolí libovolnou shodu, což by mohlo způsobit neočekávané výsledky.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[ParameterGroup –](../msbuild/parametergroup-element.md)|Sada parametrů, která se zobrazí na úkolu vygenerovaného zadaným `TaskFactory` .|  
|[Úkol](../msbuild/task-element-msbuild.md)|Data předaná do `TaskFactory` pro vygenerování instance úkolu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
  
## <a name="remarks"></a>Poznámky  
 Proměnné prostředí, vlastnosti příkazového řádku a vlastnosti na úrovni projektu mohou být odkazovány kdekoli v `UsingTask` prvku, pokud se zobrazí v souboru projektu buď explicitně, nebo prostřednictvím importovaného souboru projektu. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
> Vlastnosti na úrovni projektu nemají žádný význam, pokud `UsingTask` prvek přichází z jednoho ze souborů. Tasks, které jsou globálně registrovány v modulu MSBuild. Vlastnosti na úrovni projektu nejsou globálním pro MSBuild.  
  
 V MSBuild 4,0 lze pomocí úloh načíst ze souborů. overridetask.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `UsingTask` element s `AssemblyName` atributem.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `UsingTask` element s `AssemblyFile` atributem.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
