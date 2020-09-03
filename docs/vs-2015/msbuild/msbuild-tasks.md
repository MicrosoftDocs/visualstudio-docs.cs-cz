---
title: Úlohy nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 756c19da1aeb8878c2d045f4ee471d8449d2a954
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154805"
---
# <a name="msbuild-tasks"></a>Úlohy nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platforma sestavení potřebuje možnost spustit libovolný počet akcí během procesu sestavení. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k provedení těchto akcí používá *úkoly* . Úkol je jednotka spustitelného kódu, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] který používá k provádění atomických operací sestavení.  
  
## <a name="task-logic"></a>Logika úlohy  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Formát souboru XML projektu nemůže plně provádět operace sestavení samostatně, takže logika úlohy musí být implementována mimo soubor projektu.  
  
 Logika spuštění úkolu je implementována jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, které je definováno v <xref:Microsoft.Build.Framework> oboru názvů.  
  
 Třída Task také definuje vstupní a výstupní parametry, které jsou k dispozici pro úkol v souboru projektu. Všechny veřejné nestatické nestatické nestatické vlastnosti, které jsou vystaveny třídou Task, mohou být přístupné v souboru projektu umístěním odpovídajícího atributu se stejným názvem do elementu [Task](../msbuild/task-element-msbuild.md) .  
  
 Vlastní úlohu můžete napsat vytvářením spravované třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace najdete v tématu [psaní úloh](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Spuštění úkolu ze souboru projektu  
 Před spuštěním úlohy v souboru projektu je nutné nejprve namapovat typ v sestavení, které implementuje úlohu, na název úlohy pomocí elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . To umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] určit, kde má být při hledání v souboru projektu hledána logika spuštění úkolu.  
  
 Chcete-li spustit úlohu v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu, vytvořte prvek s názvem úkolu jako podřízený `Target` elementu. Pokud úkol akceptuje parametry, jsou předány jako atributy elementu.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] seznamy položek a vlastnosti lze použít jako parametry. Například následující kód volá `MakeDir` úlohu a nastaví hodnotu `Directories` vlastnosti `MakeDir` objektu rovnající se hodnotě `BuildDir` vlastnosti deklarované v předchozím příkladu.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Úkoly mohou také vracet informace do souboru projektu, které mohou být uloženy v položkách nebo vlastnostech pro pozdější použití. Například následující kód volá `Copy` úlohu a ukládá informace z `CopiedFiles` vlastnosti Output v `SuccessfullyCopiedFiles` seznamu položek.  
  
```  
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
  
## <a name="included-tasks"></a>Zahrnuté úlohy  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dodává se s mnoha úlohami, jako je například [kopírování](../msbuild/copy-task.md), která kopíruje soubory, [MakeDir –](../msbuild/makedir-task.md), které vytváří adresáře a [CSC](../msbuild/csc-task.md), který kompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] soubory zdrojového kódu. Úplný seznam dostupných úloh a informací o využití najdete v tématu s [odkazem na úlohu](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Přepsané úlohy  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vyhledá úkoly v několika umístěních. První umístění se nachází v souborech s příponou. OverrideTasks uložené v adresářích .NET Framework. Úkoly v těchto souborech přepíšou všechny další úlohy se stejnými názvy, včetně úkolů v souboru projektu. Druhé umístění se nachází v souborech s příponou. Úlohy v adresářích .NET Framework. Pokud úloha není v některém z těchto umístění nalezena, je použita úloha v souboru projektu.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Nástroji](msbuild.md)   
 [Zápis úlohy](../msbuild/task-writing.md)   
 [Vložené úkoly](../msbuild/msbuild-inline-tasks.md)
