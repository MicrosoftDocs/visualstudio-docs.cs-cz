---
title: Vytváření úkolů | Microsoft Docs
description: Přečtěte si, jak můžete vytvořit vlastní úkoly k poskytnutí kódu, který se spouští během procesu sestavení MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0db9504404142e5bfdd17a66471820ddad790130
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214548"
---
# <a name="task-writing"></a>Zápis úloh

Úlohy poskytují kód, který se spouští během procesu sestavení. Úkoly jsou obsaženy v cílech. Součástí nástroje MSBuild je knihovna typických úkolů a můžete také vytvářet vlastní úkoly. Další informace o knihovně úloh, které jsou součástí nástroje MSBuild, naleznete v tématu [Task reference](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Úlohy

 Mezi příklady úloh patří [kopírování](../msbuild/copy-task.md), které kopíruje jeden nebo více souborů, [MakeDir –](../msbuild/makedir-task.md), které vytvoří adresář a [CSC](../msbuild/csc-task.md), který kompiluje soubory zdrojového kódu jazyka C#. Každá úloha je implementována jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, které je definováno v sestavení *Microsoft.Build.Framework.dll* .

 Existují dva přístupy, které můžete použít při implementaci úlohy:

- Implementujte <xref:Microsoft.Build.Framework.ITask> rozhraní přímo.

- Odvodit třídu z pomocné třídy, <xref:Microsoft.Build.Utilities.Task> , která je definována v sestavení *Microsoft.Build.Utilities.dll* . Úloha implementuje ITask a poskytuje výchozí implementace některých ITask členů. Protokolování je navíc jednodušší.

V obou případech je nutné přidat do třídy a metodu s názvem `Execute` , což je metoda, která je volána při spuštění úlohy. Tato metoda nepřijímá žádné parametry a vrací `Boolean` hodnotu: `true` Pokud úloha proběhla úspěšně, nebo `false` Pokud se nezdařila. Následující příklad ukazuje úlohu, která neprovede žádnou akci a vrátí `true` .

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Následující soubor projektu spouští tuto úlohu:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Když jsou spouštěny úlohy, mohou také přijímat vstupy ze souboru projektu, pokud vytvoříte vlastnosti rozhraní .NET pro třídu Task. Nástroj MSBuild nastavuje tyto vlastnosti těsně před voláním `Execute` metody úkolu. Chcete-li vytvořit řetězcovou vlastnost, použijte kód úlohy, například:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Následující soubor projektu spustí tuto úlohu a nastaví `MyProperty` na danou hodnotu:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Registrovat úlohy

 Pokud projekt spustí úlohu, MSBuild musí znát, jak najít sestavení, které obsahuje třídu Task. Úlohy jsou registrovány pomocí [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Soubor MSBuild *Microsoft. Common. Tasks* je soubor projektu, který obsahuje seznam `UsingTask` prvků, které registrují všechny úkoly, které jsou součástí nástroje MSBuild. Tento soubor je automaticky zahrnut při sestavování všech projektů. Pokud úkol, který je zaregistrován v *Microsoft. Common. Tasks* , je zaregistrován také v aktuálním souboru projektu, aktuální soubor projektu má přednost. To znamená, že můžete přepsat výchozí úkol vlastní úlohou, která má stejný název.

> [!TIP]
> Seznam úkolů, které se dodávají s nástrojem MSBuild, můžete zobrazit zobrazením obsahu *Microsoft. Common. Tasks*.

## <a name="raise-events-from-a-task"></a>Vyvolání událostí z úkolu

 Pokud je úloha odvozena z <xref:Microsoft.Build.Utilities.Task> pomocné třídy, můžete použít jakoukoli z následujících pomocných metod <xref:Microsoft.Build.Utilities.Task> třídy k vyvolání událostí, které budou zachyceny a zobrazeny všemi registrovanými protokolovacími nástroji:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Pokud úloha přímo implementuje <xref:Microsoft.Build.Framework.ITask> , můžete i nadále vyvolávat takové události, ale je nutné použít rozhraní IBuildEngine. Následující příklad ukazuje úlohu, která implementuje ITask a vyvolá vlastní událost:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Vyžadovat nastavení parametrů úkolu

 Některé vlastnosti úlohy můžete označit jako "požadováno", aby všechny soubory projektu, které spouštějí úlohu, musely nastavovat hodnoty pro tyto vlastnosti nebo sestavení selhalo. Použijte `[Required]` atribut na vlastnost .NET v úkolu následujícím způsobem:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 `[Required]`Atribut je definován <xref:Microsoft.Build.Framework.RequiredAttribute> v <xref:Microsoft.Build.Framework> oboru názvů.

## <a name="how-msbuild-invokes-a-task"></a>Jak MSBuild vyvolá úlohu

Při vyvolání úlohy MSBuild nejprve vytvoří instanci třídy Task a pak zavolá metodu setter vlastností tohoto objektu pro parametry úlohy, které jsou nastaveny v elementu Task v souboru projektu. Pokud element Task nespecifikuje parametr, nebo pokud je výraz zadaný v elementu vyhodnocen jako prázdný řetězec, vlastnost setter není volána.

Například v projektu

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

je volána pouze metoda setter pro `Input3` .

Úkol by neměl záviset na jakémkoli pořadí volání setter vlastnosti parametru.

### <a name="task-parameter-types"></a>Typy parametrů úlohy

MSBuild nativně zpracovává vlastnosti typu `string` , `bool` `ITaskItem` a `ITaskItem[]` . Pokud úloha přijímá parametr jiného typu, nástroj MSBuild vyvolá <xref:System.Convert.ChangeType%2A> Převod z `string` (se všemi rozbalenými odkazy na vlastnosti a položky) na cílový typ. Pokud se převod nezdařil pro jakýkoliv vstupní parametr, nástroj MSBuild vygeneruje chybu a nevolá `Execute()` metodu úkolu.

## <a name="example-1"></a>Příklad 1

### <a name="description"></a>Description

Tato následující třída jazyka C# ukazuje úlohu odvozenou z <xref:Microsoft.Build.Utilities.Task> pomocné třídy. Tato úloha vrátí hodnotu `true` , která označuje, že byla úspěšná.

### <a name="code"></a>Kód

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Příklad 2

### <a name="description"></a>Description

Tato následující třída jazyka C# ukazuje úlohu implementující <xref:Microsoft.Build.Framework.ITask> rozhraní. Tato úloha vrátí hodnotu `true` , která označuje, že byla úspěšná.

### <a name="code"></a>Kód

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Příklad 3

### <a name="description"></a>Description

Tato třída jazyka C# ukazuje úkol, který je odvozen z <xref:Microsoft.Build.Utilities.Task> pomocné třídy. Má požadovanou řetězcovou vlastnost a vyvolá událost, která se zobrazí ve všech zaregistrovaných protokolovacích nástrojích.

### <a name="code"></a>Kód

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Příklad 4

### <a name="description"></a>Description

Následující příklad ukazuje soubor projektu, který volá předchozí příklad úlohy SimpleTask3.

### <a name="code"></a>Kód

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
