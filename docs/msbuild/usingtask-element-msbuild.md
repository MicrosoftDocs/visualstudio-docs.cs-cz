---
title: UsingTask – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8341a83443855f2fd90d7f5a742251fa54fc4890
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962906"
---
# <a name="usingtask-element-msbuild"></a>UsingTask – element (MSBuild)
Mapuje úlohu, na kterou je odkazováno v elementu [Task](../msbuild/task-element-msbuild.md) , na sestavení, které obsahuje implementaci úlohy.

 \<Project > \<UsingTask >

## <a name="syntax"></a>Syntaxe

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Na rozdíl od vlastností a položek se použije *první* prvek `UsingTask`, který se vztahuje na `TaskName`. Chcete-li přepsat úkoly, je nutné definovat nové `UsingTask` *před* stávajícím.

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`AssemblyName`|Je požadován buď atribut `AssemblyName`, nebo atribut `AssemblyFile`.<br /><br /> Název sestavení, které chcete načíst. Atribut `AssemblyName` přijímá sestavení se silným názvem, i když silné pojmenovávání není vyžadováno. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí metody <xref:System.Reflection.Assembly.Load%2A> v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li použit atribut `AssemblyFile`.|
|`AssemblyFile`|Je požadován buď atribut `AssemblyName`, nebo atribut `AssemblyFile`.<br /><br /> Cesta k souboru sestavení. Tento atribut přijímá úplné cesty nebo relativní cesty. Relativní cesty jsou relativní vzhledem k adresáři souboru projektu nebo souboru cílů, kde je deklarován element `UsingTask`. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí metody <xref:System.Reflection.Assembly.LoadFrom%2A> v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li použit atribut `AssemblyName`.|
|`TaskFactory`|Nepovinný atribut.<br /><br /> Určuje třídu v sestavení, která je zodpovědná za generování instancí zadaného názvu `Task`.  Uživatel může také zadat `TaskBody` jako podřízený prvek, který objekt pro vytváření úloh obdrží a použije k vygenerování úkolu. Obsah `TaskBody` je specifický pro objekt pro vytváření úloh.|
|`TaskName`|Požadovaný atribut.<br /><br /> Název úkolu, který se má odkazovat ze sestavení. Pokud je to možné, měl by tento atribut vždy určovat celé obory názvů. Pokud existují dvojznačnosti, nástroj MSBuild zvolí libovolnou shodu, což by mohlo způsobit neočekávané výsledky.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Sada parametrů, která se zobrazí u úlohy vygenerované zadaným `TaskFactory`.|
|[Úloha](../msbuild/task-element-msbuild.md)|Data předaná `TaskFactory` pro vygenerování instance úkolu.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Poznámky
 Proměnné prostředí, vlastnosti příkazového řádku, vlastnosti na úrovni projektu a položky na úrovni projektu lze odkazovat v prvcích `UsingTask` obsažených v souboru projektu buď přímo, nebo prostřednictvím importovaného souboru projektu. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Vlastnosti a položky na úrovni projektu nemají žádný význam, pokud prvek `UsingTask` pochází z jednoho ze souborů *. Tasks* , které jsou globálně registrovány pomocí modulu MSBuild. Hodnoty na úrovni projektu nejsou globálním pro MSBuild.

 V MSBuild 4,0 lze pomocí úloh načíst ze souborů *. overridetask* .

## <a name="example"></a>Příklad
 Následující příklad ukazuje způsob použití prvku `UsingTask` s atributem `AssemblyName`.

```xml
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
 Následující příklad ukazuje způsob použití prvku `UsingTask` s atributem `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Viz také:
- [Úkoly](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
