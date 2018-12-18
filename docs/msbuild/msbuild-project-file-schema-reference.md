---
title: Referenční dokumentace schématu souboru projektu nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ed3fd3fc60e6c263d7363047ed36b2f0d891a76
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078937"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenční dokumentace schématu souboru projektu MSBuild
Obsahuje všechny tabulky [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] prvky schématu XML s jejich dostupné atributy a podřízené prvky.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubory projektu používá dáte pokyn, aby modul sestavení co k sestavení a jak ji sestavit. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubory projektu jsou soubory XML, které se řídí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] schématu XML. Tato část popisuje definici schématu XML (*XSD*) souboru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Prvky schématu MSBuild XML  
 V následující tabulce jsou uvedeny všechny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] prvků schématu XML spolu s jejich podřízené prvky a atributy.  
  
|Prvek|Podřízené prvky|Atributy|  
|-------------|--------------------|----------------|  
|[Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)|jinak<br /><br /> Kdy|--|  
|[Import – element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Podmínka<br /><br /> Projekt|  
|[Importgroup – element](../msbuild/importgroup-element.md)|Importovat|Podmínka|  
|[Item – element (MSBuild)](../msbuild/item-element-msbuild.md)|*Itemmetadata –*|Podmínka<br /><br /> Vyloučení<br /><br /> Zařadit členy<br /><br /> odebrat|  
|[ItemDefinitionGroup – element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Podmínka|  
|[Itemgroup – element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Podmínka|  
|[Itemmetadata – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Podmínka|  
|[Onerror – element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Podmínka<br /><br /> ExecuteTargets|  
|[Otherwise – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Zvolte<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output – element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Podmínka<br /><br /> Název položky<br /><br /> Vlastnost PropertyName<br /><br /> Parametr úkolu|  
|[Parameter – element](../msbuild/parameter-element.md)|--|Výstup<br /><br /> Zda položka ParameterType<br /><br /> Požadováno|  
|[Parametergroup – element](../msbuild/parametergroup-element.md)|*Parametr*|--|  
|[Project – element (MSBuild)](../msbuild/project-element-msbuild.md)|Zvolte<br /><br /> Importovat<br /><br /> ItemGroup<br /><br /> Projectextensions –<br /><br /> PropertyGroup<br /><br /> Cíl<br /><br /> Usingtask –|Defaulttargets –<br /><br /> InitialTargets<br /><br /> Atribut ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> atribut xmlns|  
|[Projectextensions – element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property – element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Podmínka|  
|[PropertyGroup – element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Podmínka|  
|[SDK – element (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Název<br /><br /> Version|  
|[Target – element (MSBuild)](../msbuild/target-element-msbuild.md)|Onerror –<br /><br /> *Úloha*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Podmínka<br /><br /> DependsOnTargets<br /><br /> Vstupy<br /><br /> KeepDuplicateOutputs<br /><br /> Název<br /><br /> Výstupy<br /><br /> Vrací|  
|[Task – element (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Podmínka<br /><br /> ContinueOnError –<br /><br /> *Parametr*|  
|[Taskbody – element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Vyhodnocení|  
|[Usingtask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|Parametergroup –<br /><br /> Taskbody –|AssemblyFile<br /><br /> AssemblyName<br /><br /> Podmínka<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Když – element (MSBuild)](../msbuild/when-element-msbuild.md)|Zvolte<br /><br /> ItemGroup<br /><br /> PropertyGroup|Podmínka|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Podmínky](../msbuild/msbuild-conditions.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
