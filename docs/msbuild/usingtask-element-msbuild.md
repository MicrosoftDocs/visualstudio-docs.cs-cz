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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14556467e0907818333695b3388b2d11f3467ed7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85289154"
---
# <a name="usingtask-element-msbuild"></a>UsingTask – element (MSBuild)

Mapuje úlohu, na kterou je odkazováno v elementu [Task](../msbuild/task-element-msbuild.md) , na sestavení, které obsahuje implementaci úlohy.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Syntax

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Na rozdíl od vlastností a položek *first* `UsingTask` bude použit první prvek, který se vztahuje na a, `TaskName` aby bylo možné přepsat úkoly, které je nutné definovat `UsingTask` *před* existujícím.

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Architecture`|Nepovinný atribut.<br /><br /> Určuje, že úloha musí běžet v procesu zadaného bitová verze. Pokud aktuální proces nesplňuje požadavky, úloha se spustí v procesu hostitele úlohy, který provede.<br /><br /> Podporované hodnoty jsou `x86` (32 – bit), `x64` (64-bit), `CurrentArchitecture` a `*` (jakákoli architektura).|  
|`AssemblyName`|`AssemblyName`Je vyžadován buď atribut, nebo `AssemblyFile` atribut.<br /><br /> Název sestavení, které chcete načíst. `AssemblyName`Atribut přijímá sestavení se silným názvem, i když silné pojmenovávání není vyžadováno. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí <xref:System.Reflection.Assembly.Load%2A> metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li `AssemblyFile` použit atribut.|
|`AssemblyFile`|`AssemblyName` `AssemblyFile` Je vyžadován buď atribut, nebo.<br /><br /> Cesta k souboru sestavení. Tento atribut přijímá úplné cesty nebo relativní cesty. Relativní cesty jsou relativní vzhledem k adresáři souboru projektu nebo souboru cílů, kde `UsingTask` je element deklarovaný. Použití tohoto atributu je ekvivalentní k načtení sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, je-li `AssemblyName` použit atribut.|
|`Runtime`|Nepovinný atribut.<br /><br /> Určuje, že úloha musí běžet v modulu .NET Framework runtime zadané verze. Pokud aktuální proces nesplňuje požadavky, úloha se spustí v procesu hostitele úlohy, který provede. Nepodporuje se v nástroji MSBuild pro .NET Core.<br /><br /> Podporované hodnoty jsou `CLR2` (.NET Framework 3,5), `CLR4` (.NET Framework 4.7.2 nebo vyšší), `CurrentRuntime` a `*` (libovolný modul runtime).|  
|`TaskFactory`|Nepovinný atribut.<br /><br /> Určuje třídu v sestavení, která je zodpovědná za generování instancí zadaného `Task` názvu.  Uživatel může také určit `Task` jako podřízený prvek, který objekt pro vytváření úloh obdrží a použije k vygenerování úlohy. Obsah je `Task` specifický pro objekt pro vytváření úloh.|
|`TaskName`|Požadovaný atribut.<br /><br /> Název úkolu, který se má odkazovat ze sestavení. Pokud je to možné, měl by tento atribut vždy určovat celé obory názvů. Pokud existují dvojznačnosti, nástroj MSBuild zvolí libovolnou shodu, což by mohlo způsobit neočekávané výsledky.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[ParameterGroup –](../msbuild/parametergroup-element.md)|Sada parametrů, která se zobrazí na úkolu vygenerovaného zadaným `TaskFactory` .|
|[Úkol](../msbuild/task-element-msbuild.md)|Data předaná do `TaskFactory` pro vygenerování instance úkolu.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="remarks"></a>Poznámky

 Proměnné prostředí, vlastnosti příkazového řádku, vlastnosti na úrovni projektu a položky na úrovni projektu lze odkazovat v `UsingTask` prvcích obsažených v souboru projektu buď přímo, nebo prostřednictvím importovaného souboru projektu. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Vlastnosti a položky na úrovni projektu nemají žádný význam, pokud `UsingTask` prvek přichází z jednoho ze souborů *. Tasks* , které jsou globálně registrovány v modulu MSBuild. Hodnoty na úrovni projektu nejsou globálním pro MSBuild.

 V MSBuild 4,0 lze pomocí úloh načíst ze souborů *. overridetask* .

Sestavení obsahující vlastní úlohu je načteno při `Task` prvním použití.

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak použít `UsingTask` element s `AssemblyName` atributem.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak použít `UsingTask` element s `AssemblyFile` atributem.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Postupy: Konfigurace cílů a úloh](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
