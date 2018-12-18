---
title: Usingtask – Element (MSBuild) | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: e412fce1169b0e68c6b2f924b95c5433728be3a7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871937"
---
# <a name="usingtask-element-msbuild"></a>UsingTask – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Mapuje na úkol, který se odkazuje v [úloh](../msbuild/task-element-msbuild.md) element na sestavení, které obsahuje implementaci úkolu.  
  
 \<Project>  
 \<Usingtask – >  
  
## <a name="syntax"></a>Syntaxe  
  
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
|`AssemblyName`|Buď `AssemblyName` atribut nebo `AssemblyFile` atribut je vyžadován.<br /><br /> Název sestavení, které chcete načíst. `AssemblyName` Atribut je možné zadat sestavení se silným názvem, i když není potřeba silné názvy. Pomocí tohoto atributu je ekvivalentní k načtení sestavení s použitím <xref:System.Reflection.Assembly.Load%2A> metoda v rozhraní .NET.<br /><br /> Tento atribut nelze použít, pokud `AssemblyFile` atribut se používá.|  
|`AssemblyFile`|Buď `AssemblyName` nebo `AssemblyFile` atribut je vyžadován.<br /><br /> Cesta k souboru sestavení. Tento atribut je možné zadat relativní cesty nebo úplné cesty. Relativní cesty jsou relativní vzhledem k adresáři projektu soubor nebo soubor cílů kde `UsingTask` je deklarován element. Pomocí tohoto atributu je ekvivalentní k načtení sestavení s použitím <xref:System.Reflection.Assembly.LoadFrom%2A> metoda v rozhraní .NET.<br /><br /> Tento atribut nelze použít, pokud `AssemblyName` atribut se používá.|  
|`TaskFactory`|Nepovinný atribut.<br /><br /> Určuje třídu v sestavení, který je zodpovědný za generování instance zadaného `Task` název.  Uživatel může také určit `TaskBody` jako podřízený prvek, který přijímá objekt pro vytváření úkolů a používá ke generování úlohy. Obsah `TaskBody` jsou specifická pro objekt pro vytváření úloh.|  
|`TaskName`|Požadovaný atribut.<br /><br /> Název úkolu odkazovat ze sestavení. Pokud nejasnostem, je možné, tento atribut by měl být určen úplný obory názvů. Pokud existují nejednoznačnosti, vybere MSBuild libovolného shodu, což může vést k neočekávaným výsledkům.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínky pro hodnocení. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Sada parametrů, které se zobrazují na úkol, který je generována pomocí zadané `TaskFactory`.|  
|[Úloha](../msbuild/task-element-msbuild.md)|Data, která je předána `TaskFactory` k vytvoření instance úlohy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový element [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
  
## <a name="remarks"></a>Poznámky  
 Proměnné prostředí, vlastnosti příkazového řádku a vlastností na úrovni projektu může být odkazováno kdekoli v `UsingTask` element, pokud se zobrazí v souboru projektu buď explicitně nebo importovaného souboru projektu. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Na úrovni projektu vlastnosti nemají význam, pokud `UsingTask` element pochází z jednoho ze souborů .tasks globálně zaregistrovaných pomocí modulu MSBuild. Vlastnosti na úrovni projektu nejsou globální nástroji MSBuild.  
  
 V MSBuild 4.0 je možné pomocí úloh načíst ze souborů .overridetask.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `UsingTask` element s `AssemblyName` atribut.  
  
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
 Následující příklad ukazuje způsob použití `UsingTask` element s `AssemblyFile` atribut.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)



