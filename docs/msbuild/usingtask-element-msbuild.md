---
title: UsingTask Element (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 22d61fe30e9eb68697f073ca0bcfbcc515e513dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431446"
---
# <a name="usingtask-element-msbuild"></a>UsingTask element (MSBuild)

Mapuje úkol, který je odkazován v [Task](../msbuild/task-element-msbuild.md) prvek sestavení, které obsahuje implementaci úkolu.

 \<Projekt \<> usingtask>

## <a name="syntax"></a>Syntaxe

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> Na rozdíl od vlastností a položek `TaskName` bude použit *první* `UsingTask` prvek, který se vztahuje na a; chcete-li přepsat úkoly, `UsingTask` musíte definovat nový *před* existujícím.

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`AssemblyName`|Je `AssemblyName` vyžadován atribut `AssemblyFile` nebo atribut.<br /><br /> Název sestavení, které chcete načíst. Atribut `AssemblyName` přijímá sestavení se silným názvem, i když není vyžadováno silné pojmenování. Použití tohoto atributu je ekvivalentní načítání <xref:System.Reflection.Assembly.Load%2A> sestavení pomocí metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, `AssemblyFile` pokud je atribut použit.|
|`AssemblyFile`|Je `AssemblyName` vyžadován `AssemblyFile` atribut nebo.<br /><br /> Cesta k souboru sestavení. Tento atribut přijímá úplné cesty nebo relativní cesty. Relativní cesty jsou relativní k adresáři souboru projektu `UsingTask` nebo cíle souboru, kde je deklarován prvek. Použití tohoto atributu je ekvivalentní načítání <xref:System.Reflection.Assembly.LoadFrom%2A> sestavení pomocí metody v rozhraní .NET.<br /><br /> Tento atribut nelze použít, `AssemblyName` pokud je atribut použit.|
|`TaskFactory`|Nepovinný atribut.<br /><br /> Určuje třídu v sestavení, která je zodpovědná za `Task` generování instancí zadaného názvu.  Uživatel může také `Task` zadat jako podřízený prvek, který továrna úloh přijímá a používá ke generování úlohy. Obsah `Task` jsou specifické pro továrnu úloh.|
|`TaskName`|Požadovaný atribut.<br /><br /> Název úkolu odkaz z sestavení. Pokud jsou možné nejasnosti, tento atribut by měl vždy zadat úplné obory názvů. Pokud existují nejasnosti, MSBuild zvolí libovolnou shodu, která by mohla způsobit neočekávané výsledky.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka vyhodnotit. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Skupina parametrů](../msbuild/parametergroup-element.md)|Sada parametrů, které se zobrazí na úkolu, který `TaskFactory`je generován zadaným .|
|[Úkol](../msbuild/task-element-msbuild.md)|Data, která je `TaskFactory` předána ke generování instance úkolu.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |

## <a name="remarks"></a>Poznámky

 Proměnné prostředí, vlastnosti příkazového řádku, vlastnosti na úrovni projektu a `UsingTask` položky na úrovni projektu lze odkazovat v prvcích zahrnutých v souboru projektu přímo nebo prostřednictvím importovaného souboru projektu. Další informace naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Vlastnosti a položky na úrovni `UsingTask` projektu nemají žádný význam, pokud prvek pochází z jednoho ze souborů *.tasks,* které jsou globálně registrovány pomocí modulu MSBuild. Hodnoty na úrovni projektu nejsou globální pro MSBuild.

 V msbuild 4.0 pomocí úloh lze načíst ze souborů *.overridetask.*

Sestavení obsahující vlastní úkol je načten `Task` při prvním použití.

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak `UsingTask` používat `AssemblyName` prvek s atributem.

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

 Následující příklad ukazuje, jak `UsingTask` používat `AssemblyFile` prvek s atributem.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
