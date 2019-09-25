---
title: Vytváření úkolů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cf7f82d628c0c093e0d807920b379263c20ff0b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238199"
---
# <a name="task-writing"></a>Zápis úlohy
Úlohy poskytují kód, který se spouští během procesu sestavení. Úkoly jsou obsaženy v cílech. Součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]je knihovna typických úkolů. můžete také vytvořit vlastní úkoly. Další informace o knihovně úloh, které jsou součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]nástroje, naleznete v tématu [Task reference](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Úkoly
 Mezi příklady úloh patří [kopírování](../msbuild/copy-task.md), které kopíruje jeden nebo více souborů, [MakeDir –](../msbuild/makedir-task.md), které vytvoří adresář a [CSC](../msbuild/csc-task.md), který kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] soubory zdrojového kódu. Každá úloha je implementována jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, které je definováno v sestavení *Microsoft. Build. Framework. dll* .

 Existují dva přístupy, které můžete použít při implementaci úlohy:

- Implementujte <xref:Microsoft.Build.Framework.ITask> rozhraní přímo.

- Odvodit třídu z pomocné třídy <xref:Microsoft.Build.Utilities.Task>,, která je definována v sestavení *Microsoft. Build. Utilities. dll* . Úloha implementuje ITask a poskytuje výchozí implementace některých ITask členů. Protokolování je navíc jednodušší.

V obou případech je nutné přidat do třídy a metodu s názvem `Execute`, což je metoda, která je volána při spuštění úlohy. Tato metoda nepřijímá žádné parametry a vrací `Boolean` hodnotu: `true` Pokud úloha proběhla úspěšně `false` , nebo pokud se nezdařila. Následující příklad ukazuje úlohu, která neprovede žádnou akci a vrátí `true`.

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

 Když jsou spouštěny úlohy, mohou také přijímat vstupy ze souboru projektu, pokud vytvoříte vlastnosti rozhraní .NET pro třídu Task. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Tyto vlastnosti nastaví těsně před voláním `Execute` metody úkolu. Chcete-li vytvořit řetězcovou vlastnost, použijte kód úlohy, například:

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
 Pokud projekt spustí úlohu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musí znát, jak najít sestavení, které obsahuje třídu Task. Úlohy jsou registrovány pomocí [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Soubor Microsoft *. Common. Tasks* je soubor projektu, který `UsingTask` obsahuje seznam prvků, které registrují [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]všechny úkoly, které jsou součástí nástroje. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Tento soubor je automaticky zahrnut při sestavování všech projektů. Pokud úkol, který je zaregistrován v *Microsoft. Common. Tasks* , je zaregistrován také v aktuálním souboru projektu, aktuální soubor projektu má přednost. To znamená, že můžete přepsat výchozí úkol vlastní úlohou, která má stejný název.

> [!TIP]
> Seznam úkolů, které jsou k [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dispozici, zobrazíte zobrazením obsahu *Microsoft. Common. Tasks*.

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
 Některé vlastnosti úlohy můžete označit jako "požadováno", aby všechny soubory projektu, které spouštějí úlohu, musely nastavovat hodnoty pro tyto vlastnosti nebo sestavení selhalo. `[Required]` Použijte atribut na vlastnost .NET v úkolu následujícím způsobem:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Atribut je <xref:Microsoft.Build.Framework.RequiredAttribute> definován v<xref:Microsoft.Build.Framework> oboru názvů. `[Required]`

## <a name="how-includevstecmsbuildextensibilityinternalsincludesvstecmsbuild_mdmd-invokes-a-task"></a>Způsob [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vyvolání úlohy

Při vyvolání úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nejprve vytvoří instanci třídy Task a pak zavolá metodu setter vlastností objektu pro parametry úlohy, které jsou nastaveny v elementu Task v souboru projektu. Pokud element Task nespecifikuje parametr, nebo pokud je výraz zadaný v elementu vyhodnocen jako prázdný řetězec, vlastnost setter není volána.

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

je volána pouze metoda `Input3` setter pro.

Úkol by neměl záviset na jakémkoli pořadí volání setter vlastnosti parametru.

### <a name="task-parameter-types"></a>Typy parametrů úlohy

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Nativně zpracovává vlastnosti `string`typu, `ITaskItem` , a `ITaskItem[]`. `bool` Pokud úkol akceptuje parametr jiného typu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] <xref:System.Convert.ChangeType%2A> vyvolá se pro převod z `string` (se všemi rozbalenými odkazy na vlastnosti a položku) na cílový typ. Pokud převod není pro jakýkoliv vstupní parametr úspěšný, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vygeneruje chybu a nevolá `Execute()` metodu úkolu.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato třída ukazuje úlohu odvozenou <xref:Microsoft.Build.Utilities.Task> z pomocné třídy. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Tato úloha vrátí `true`hodnotu, která označuje, že byla úspěšná.

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

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato třída předvádí úlohu implementující <xref:Microsoft.Build.Framework.ITask>rozhraní. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Tato úloha vrátí `true`hodnotu, která označuje, že byla úspěšná.

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

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] třída předvádí úlohu, která je odvozena <xref:Microsoft.Build.Utilities.Task> z pomocné třídy. Má požadovanou řetězcovou vlastnost a vyvolá událost, která se zobrazí ve všech zaregistrovaných protokolovacích nástrojích.

### <a name="code"></a>Kód

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

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

## <a name="see-also"></a>Viz také:

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
