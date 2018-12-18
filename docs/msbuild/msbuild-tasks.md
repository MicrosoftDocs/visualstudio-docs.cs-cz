---
title: Úlohy nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a380917f3a4eaba71a00ff32f1bc627f47f5d4d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153199"
---
# <a name="msbuild-tasks"></a>úlohy nástroje MSBuild
Platformy sestavení musí být schopné spustit libovolný počet akcí během procesu sestavení. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používá *úlohy* k provedení těchto akcí. Úkol je jednotka spustitelný kód, který používá [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k operacím atomického sestavení.  
  
## <a name="task-logic"></a>Úloha logiky  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Formát souboru projektu XML nelze spustit plně sestavení operací na sama, takže logiku úkolu musí být implementované mimo rámec souborů projektu.  
  
 Logika spuštění úkolu je implementován jako třída rozhraní .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, která je definována v <xref:Microsoft.Build.Framework> oboru názvů.  
  
 Třída úloha také definuje vstupní a výstupní parametry k dispozici úkolu v souboru projektu. Všechny veřejné nastavitelné nestatické neabstraktní vlastností vystavovaných třídami třída úlohy je přístupný v souboru projektu tak, že na odpovídající atribut se stejným názvem [úloh](../msbuild/task-element-msbuild.md) elementu.  
  
 Můžete napsat vlastní úkol vytvořením spravovaného třídu, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace najdete v tématu [úkolů zápisu](../msbuild/task-writing.md).  
  
## <a name="execute-a-task-from-a-project-file"></a>Spustit úlohu ze souboru projektu  
 Před spuštěním úkolu v souboru projektu, je třeba nejprve namapovat typ v sestavení, který implementuje úkolů s názvem úkolu [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Díky tomu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] věděli, kde hledat logika spuštění úkolu, pokud se najde v souboru projektu.  
  
 Spustit úlohu v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] souboru projektu, vytvořte prvek se název úkolu jako podřízený objekt `Target` elementu. Pokud úloha přijímá parametry, ty jsou předány jako atributy elementu.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Položka vlastnosti a seznamy se dá použít jako parametry. Například následující kód volá `MakeDir` úloh a nastaví hodnotu vlastnosti `Directories` vlastnost `MakeDir` rovna hodnotě tohoto objektu `BuildDir` vlastnosti deklarované v předchozím příkladu.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Úlohy může také vracet informace do souboru projektu, která mohou být uložena v položky nebo vlastnosti pro pozdější použití. Například následující kód volá `Copy` úlohy a ukládá informace od `CopiedFiles` výstupní vlastnosti `SuccessfullyCopiedFiles` seznam položek.  
  
```xml  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Součástí úlohy  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se dodává s mnoha úkoly, jako [kopírování](../msbuild/copy-task.md), který zkopíruje soubory, [MakeDir](../msbuild/makedir-task.md), vytvoření adresářů a [Csc](../msbuild/csc-task.md), který zkompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] souborů zdrojového kódu. Úplný seznam dostupných úkolů a informace o použití najdete v části [úkolů odkaz](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Přepsané úlohy  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vyhledá pro úlohy v několika umístěních. První místo nachází soubory s příponou *. OverrideTasks* uložené v adresáři rozhraní .NET Framework. Úkoly v těchto souborech přepsat všechny úkoly se stejnými názvy, včetně úkolů v souboru projektu. Druhé místo je v souborech s příponou *. Úlohy* v adresáři rozhraní .NET Framework. Pokud úkol nebyl nalezen v některém z těchto umístění, použije se úkolu v souboru projektu.  
  
## <a name="see-also"></a>Viz také:  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Nástroj MSBuild](../msbuild/msbuild.md)   
 [Zápis úloh](../msbuild/task-writing.md)   
 [Vložené úlohy](../msbuild/msbuild-inline-tasks.md)