---
title: Psaní úkolů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631833"
---
# <a name="task-writing"></a>Psaní úkolů

Úkoly poskytují kód, který se spustí během procesu sestavení. Úkoly jsou obsaženy v cílech. Knihovna typických úkolů je součástí MSBuild a můžete také vytvořit vlastní úkoly. Další informace o knihovně úkolů, které jsou součástí msbuild, naleznete v [tématu Task reference](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Úlohy

 Příklady úkolů zahrnují [copy](../msbuild/copy-task.md), který kopíruje jeden nebo více souborů, [MakeDir](../msbuild/makedir-task.md), který vytváří adresář, a [Csc](../msbuild/csc-task.md), který kompiluje soubory zdrojového kódu C#. Každá úloha je implementována jako <xref:Microsoft.Build.Framework.ITask> třída .NET, která implementuje rozhraní, které je definováno v sestavení *Microsoft.Build.Framework.dll.*

 Existují dva přístupy, které můžete použít při implementaci úkolu:

- Implementujte <xref:Microsoft.Build.Framework.ITask> rozhraní přímo.

- Odvodit třídu z <xref:Microsoft.Build.Utilities.Task>pomocné třídy , která je definována v sestavení *Microsoft.Build.Utilities.dll.* Úloha implementuje ITask a poskytuje výchozí implementace některých členů ITask. Protokolování je navíc jednodušší.

V obou případech je nutné přidat do `Execute`třídy metodu s názvem , což je metoda, která je volána při spuštění úlohy. Tato metoda nepřebírá žádné `Boolean` parametry `true` a vrátí hodnotu: pokud byl úkol úspěšný nebo `false` pokud se nezdařil. Následující příklad ukazuje úkol, který neprovádí žádnou akci a vrátí `true`.

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

 Následující soubor projektu spustí tento úkol:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Při spuštění úloh mohou také přijímat vstupy ze souboru projektu, pokud vytvoříte vlastnosti .NET ve třídě úkolu. MSBuild nastaví tyto vlastnosti bezprostředně `Execute` před voláním metody úlohy. Chcete-li vytvořit vlastnost řetězce, použijte kód úlohy, například:

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

 Následující soubor projektu spustí tento `MyProperty` úkol a nastaví na danou hodnotu:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Registrace úkolů

 Pokud projekt se chystá spustit úkol, MSBuild musí vědět, jak najít sestavení, které obsahuje třídu úkolu. Úkoly jsou registrovány pomocí [usingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Soubor MSBuild *Microsoft.Common.Tasks* je soubor projektu, `UsingTask` který obsahuje seznam prvků, které registrují všechny úkoly, které jsou dodávány s MSBuild. Tento soubor je automaticky zahrnut při vytváření každého projektu. Pokud je úkol, který je registrován v *souboru microsoft.common.tasks* je také registrován v aktuálním souboru projektu, aktuální soubor projektu má přednost; To znamená, že můžete přepsat výchozí úkol s vlastní úkol, který má stejný název.

> [!TIP]
> Seznam úkolů, které jsou součástí služby MSBuild, zobrazíte pomocí obsahu *souboru Microsoft.Common.Tasks*.

## <a name="raise-events-from-a-task"></a>Vyvolávání událostí z úkolu

 Pokud vaše úloha <xref:Microsoft.Build.Utilities.Task> pochází z pomocné třídy, můžete použít některou z následujících metod pomocníka ve <xref:Microsoft.Build.Utilities.Task> třídě ke zvýšení události, které budou zachyceny a zobrazeny všechny registrované úhozy kláves:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Pokud váš úkol <xref:Microsoft.Build.Framework.ITask> implementuje přímo, můžete stále vyvolat takové události, ale je nutné použít rozhraní IBuildEngine. Následující příklad ukazuje úkol, který implementuje ITask a vyvolá vlastní událost:

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

## <a name="require-task-parameters-to-be-set"></a>Vyžadovat nastavení parametrů úlohy

 Můžete označit určité vlastnosti úkolu jako "povinné", takže každý soubor projektu, který spustí úkol, musí nastavit hodnoty pro tyto vlastnosti nebo sestavení selže. Použijte `[Required]` atribut na vlastnost .NET ve vaší úloze následujícím způsobem:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Atribut `[Required]` je definován <xref:Microsoft.Build.Framework.RequiredAttribute> v <xref:Microsoft.Build.Framework> oboru názvů.

## <a name="how-msbuild-invokes-a-task"></a>Jak MSBuild vyvolá úlohu

Při vyvolání úkolu msbuild nejprve konkretizuje třídu úkolu a pak zavolá nastavení vlastností tohoto objektu pro parametry úkolu, které jsou nastaveny v prvku úkolu v souboru projektu. Pokud prvek úkolu neurčuje parametr nebo pokud výraz zadaný v elementu vyhodnotí prázdný řetězec, není volána možnost nastavení vlastností.

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

volá pouze setter pro. `Input3`

Úloha by neměla záviset na žádné relativní pořadí vyvolání setter vlastností parametrů.

### <a name="task-parameter-types"></a>Typy parametrů úlohy

MSBuild nativně zpracovává vlastnosti `string` `bool`typu `ITaskItem` `ITaskItem[]`, a . Pokud úloha přijme parametr jiného typu, MSBuild <xref:System.Convert.ChangeType%2A> vyvolá `string` převést z (se všemi odkazy na vlastnosta a položky) na cílový typ. Pokud se převod nezdaří pro libovolný vstupní parametr, MSBuild vydává `Execute()` chybu a nevolá metodu úlohy.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato následující třída C# demonstruje úlohu <xref:Microsoft.Build.Utilities.Task> odvozenou z pomocné třídy. Tento úkol `true`vrátí , označující, že byl úspěšný.

### <a name="code"></a>kód

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

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato následující třída C# demonstruje <xref:Microsoft.Build.Framework.ITask> úlohu implementující rozhraní. Tento úkol `true`vrátí , označující, že byl úspěšný.

### <a name="code"></a>kód

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

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato třída C# demonstruje úlohu, která je odvozena <xref:Microsoft.Build.Utilities.Task> z pomocné třídy. Má vlastnost required string a vyvolá událost, která je zobrazena všemi registrovanými úhozy kláves.

### <a name="code"></a>kód

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje soubor projektu s vyvoláním předchozího ukázkového úkolu SimpleTask3.

### <a name="code"></a>kód

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

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
