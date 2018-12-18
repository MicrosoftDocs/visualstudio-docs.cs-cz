---
title: Úloha zápis | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cf8c8a05d07d1a75a8794c52a2f89a55f01419e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152060"
---
# <a name="task-writing"></a>Zápis úloh
Úlohy poskytují kód, který se spustí během procesu sestavení. Úkoly jsou obsaženy v cíli. Je součástí knihovny typické úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], a můžete také vytvořit vlastní úlohy. Další informace o knihovně úlohy, které jsou součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], naleznete v tématu [úkolů odkaz](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Úlohy  
 Příklady úloh [kopírování](../msbuild/copy-task.md), který kopíruje jeden nebo více souborů, [MakeDir](../msbuild/makedir-task.md), který vytvoří adresář, a [Csc](../msbuild/csc-task.md), který zkompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] souborů zdrojového kódu. Každý úkol je implementován jako třída rozhraní .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, která je definována v *Microsoft.Build.Framework.dll* sestavení.  
  
 Existují dvě metody, které můžete použít při implementaci úkolu:  
  
-   Implementace <xref:Microsoft.Build.Framework.ITask> rozhraní přímo.  
  
-   Odvodit třídu z pomocná třída <xref:Microsoft.Build.Utilities.Task>, který je definován v *Microsoft.Build.Utilities.dll* sestavení. Úloha implementuje ITask a poskytuje výchozí implementaci některých ITask členů. Protokolování je navíc jednodušší.  

V obou případech musíte přidat do vaší třídy metodu s názvem `Execute`, což je metoda, která je volána, když je úloha spuštěna. Tato metoda nemá žádné parametry a vrátí `Boolean` hodnota: `true` Pokud byla úloha úspěšná nebo `false` Pokud se něco nepovedlo. Následující příklad zobrazuje úlohu, která neprovede žádnou akci a vrátí `true`.  
  
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
  
 Tato úloha spuštěna následující soubor projektu:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Pokud úkoly spouštějí, můžete také obdrží vstupů ze souboru projektu Pokud vytvoříte .NET vlastnosti ve třídě úlohy. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Nastaví tyto vlastnosti bezprostředně před volání úkolu `Execute` metody. K vytvoření vlastnosti typu string, použijte kód úlohy, jako:  
  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Následující projekt soubor spuštění této úlohy a sady `MyProperty` na zadanou hodnotu:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="register-tasks"></a>Registrace úlohy  
 Pokud je projekt spustit úlohu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musí vědět, jak najít sestavení obsahující třídu úloh. Úkoly jsou registrované pomocí [usingtask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Souboru *Microsoft.Common.Tasks* je soubor projektu, který obsahuje seznam `UsingTask` prvky, které registrují všechny úkoly, které jsou součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tento soubor je automaticky zahrnuty při sestavování každý projekt. Pokud úkol, který je registrován v *Microsoft.Common.Tasks* je zaregistrovaná taky v aktuálním souboru projektu, aktuální soubor projektu má přednost před; to znamená, můžete přepsat výchozí úlohu s vlastní úkol, který má stejný název.  
  
> [!TIP]
>  Zobrazí se seznam úloh, které jsou součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zobrazením obsah *Microsoft.Common.Tasks*.  
  
## <a name="raise-events-from-a-task"></a>Vyvolávání událostí z úlohy  
 Pokud vaše úlohy je odvozen od <xref:Microsoft.Build.Utilities.Task> pomocná třída, můžete použít některý z následujících metod helper na <xref:Microsoft.Build.Utilities.Task> třídy pro vyvolání události, které bude zachycena a zobrazí všechny registrované protokolovacích nástrojů:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Pokud vaše úloha implementuje <xref:Microsoft.Build.Framework.ITask> přímo, stále může vyvolat tyto události ale musí používat IBuildEngine rozhraní. Následující příklad zobrazuje úlohu, která implementuje ITask a vyvolává vlastní události:  
  
```csharp
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## <a name="require-task-parameters-to-be-set"></a>Vyžadovat parametry úlohy, která se má nastavit  
 Některé vlastnosti úlohy jako "povinné" můžete označit tak, aby libovolný soubor projektu, na kterém běží úloha musí nastavit hodnoty těchto vlastností nebo sestavení selže. Použít `[Required]` atribut vlastnosti .NET v úkolu následujícím způsobem:  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` Je definován atribut <xref:Microsoft.Build.Framework.RequiredAttribute> v <xref:Microsoft.Build.Framework> oboru názvů.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následující [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ukazuje úkol odvozený od třídy <xref:Microsoft.Build.Utilities.Task> pomocná třída. Tato úloha vrátí `true`, což indikuje, že byla úspěšná.  
  
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
 V následující [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] třídy ukazuje úkolů implementace <xref:Microsoft.Build.Framework.ITask> rozhraní. Tato úloha vrátí `true`, což indikuje, že byla úspěšná.  
  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
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
 To [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ukazuje úlohu, která je odvozena z třídy <xref:Microsoft.Build.Utilities.Task> pomocná třída. Má vlastnost požadovaný řetězec a vyvolá událost, která se zobrazí všechny registrované protokolovacích nástrojů.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje volání předchozí příklad úkolu, SimpleTask3 souboru projektu.  
  
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
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
