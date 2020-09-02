---
title: Vytváření úkolů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaf927b1049709a04d8a883615d1997e9316599e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802795"
---
# <a name="task-writing"></a>Zápis úloh
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Úlohy poskytují kód, který se spouští během procesu sestavení. Úkoly jsou obsaženy v cílech. Součástí je knihovna typických úkolů [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . můžete také vytvořit vlastní úkoly. Další informace o knihovně úloh, které jsou součástí nástroje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , naleznete v tématu [Task reference](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Úlohy  
 Mezi příklady úloh patří [kopírování](../msbuild/copy-task.md), které kopíruje jeden nebo více souborů, [MakeDir –](../msbuild/makedir-task.md), které vytvoří adresář a [CSC](../msbuild/csc-task.md), který kompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] soubory zdrojového kódu. Každá úloha je implementována jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, které je definováno v sestavení Microsoft.Build.Framework.dll.  
  
 Existují dva přístupy, které můžete použít při implementaci úlohy:  
  
- Implementujte <xref:Microsoft.Build.Framework.ITask> rozhraní přímo.  
  
- Odvodit třídu z pomocné třídy, <xref:Microsoft.Build.Utilities.Task> , která je definována v sestavení Microsoft.Build.Utilities.dll. Úloha implementuje ITask a poskytuje výchozí implementace některých ITask členů. Protokolování je navíc jednodušší.  
  
  V obou případech je nutné přidat do třídy a metodu s názvem `Execute` , což je metoda, která je volána při spuštění úlohy. Tato metoda nepřijímá žádné parametry a vrací `Boolean` hodnotu: `true` Pokud úloha proběhla úspěšně, nebo `false` Pokud se nezdařila. Následující příklad ukazuje úlohu, která neprovede žádnou akci a vrátí `true` .  
  
```  
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
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Když jsou spouštěny úlohy, mohou také přijímat vstupy ze souboru projektu, pokud vytvoříte vlastnosti rozhraní .NET pro třídu Task. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Tyto vlastnosti nastaví těsně před voláním metody úkolu `Execute` . Chcete-li vytvořit řetězcovou vlastnost, použijte kód úlohy, například:  
  
```  
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
  
 Následující soubor projektu spustí tuto úlohu a nastaví `MyProperty` na danou hodnotu:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Registrace úloh  
 Pokud projekt spustí úlohu, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] musí znát, jak najít sestavení, které obsahuje třídu Task. Úlohy jsou registrovány pomocí [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Soubor Microsoft. Common. Tasks je soubor projektu, který obsahuje seznam `UsingTask` prvků, které registrují všechny úkoly, které jsou součástí nástroje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Tento soubor je automaticky zahrnut při sestavování všech projektů. Pokud úkol, který je zaregistrován v Microsoft. Common. Tasks, je zaregistrován také v aktuálním souboru projektu, aktuální soubor projektu má přednost. To znamená, že můžete přepsat výchozí úkol vlastní úlohou, která má stejný název.  
  
> [!TIP]
> Seznam úkolů, které jsou k dispozici, zobrazíte [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zobrazením obsahu Microsoft. Common. Tasks.  
  
## <a name="raising-events-from-a-task"></a>Vyvolávání událostí z úkolu  
 Pokud je úloha odvozena z <xref:Microsoft.Build.Utilities.Task> pomocné třídy, můžete použít jakoukoli z následujících pomocných metod <xref:Microsoft.Build.Utilities.Task> třídy k vyvolání událostí, které budou zachyceny a zobrazeny všemi registrovanými protokolovacími nástroji:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Pokud úloha přímo implementuje <xref:Microsoft.Build.Framework.ITask> , můžete i nadále vyvolávat takové události, ale je nutné použít rozhraní IBuildEngine. Následující příklad ukazuje úlohu, která implementuje ITask a vyvolá vlastní událost:  
  
```  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Vyžadování nastavení parametrů úlohy  
 Některé vlastnosti úlohy můžete označit jako "požadováno", aby všechny soubory projektu, které spouštějí úlohu, musely nastavovat hodnoty pro tyto vlastnosti nebo sestavení selhalo. Použijte `[Required]` atribut na vlastnost .NET v úkolu následujícím způsobem:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]`Atribut je definován <xref:Microsoft.Build.Framework.RequiredAttribute> v <xref:Microsoft.Build.Framework> oboru názvů.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Tato [!INCLUDE[csprcs](../includes/csprcs-md.md)] Třída ukazuje úlohu odvozenou z <xref:Microsoft.Build.Utilities.Task> pomocné třídy. Tato úloha vrátí hodnotu `true` , která označuje, že byla úspěšná.  
  
### <a name="code"></a>Kód  
  
```  
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
 Tato [!INCLUDE[csprcs](../includes/csprcs-md.md)] Třída předvádí úlohu implementující <xref:Microsoft.Build.Framework.ITask> rozhraní. Tato úloha vrátí hodnotu `true` , která označuje, že byla úspěšná.  
  
### <a name="code"></a>Kód  
  
```  
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
 Tato [!INCLUDE[csprcs](../includes/csprcs-md.md)] Třída předvádí úlohu, která je odvozena z <xref:Microsoft.Build.Utilities.Task> pomocné třídy. Má požadovanou řetězcovou vlastnost a vyvolá událost, která se zobrazí ve všech zaregistrovaných protokolovacích nástrojích.  
  
### <a name="code"></a>Kód  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje soubor projektu, který volá předchozí příklad úlohy SimpleTask3.  
  
### <a name="code"></a>Kód  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
