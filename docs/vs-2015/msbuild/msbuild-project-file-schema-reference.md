---
title: Referenční dokumentace schématu souboru projektu nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd1add4f68bb2e0648cf3cf08b72b1bc6f592595
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305978"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenční dokumentace schématu souboru projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obsahuje všechny tabulky [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] prvky schématu XML s jejich dostupné atributy a podřízené prvky.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu používá dáte pokyn, aby modul sestavení co k sestavení a jak ji sestavit. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu jsou soubory XML, které se řídí [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] schématu XML. Tato část popisuje soubor definice (XSD) schématu XML pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Prvky schématu MSBuild XML  
 V následující tabulce jsou uvedeny všechny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] prvků schématu XML spolu s jejich podřízené prvky a atributy.  
  
|Prvek|Podřízené elementy|Atributy|  
|-------------|--------------------|----------------|  
|[Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)|jinak<br /><br /> Kdy|--|  
|[Import – element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Podmínka<br /><br /> Projekt|  
|[ImportGroup – element](../msbuild/importgroup-element.md)|Importovat|Podmínka|  
|[Item – element (MSBuild)](../msbuild/item-element-msbuild.md)|*Itemmetadata –*|Podmínka<br /><br /> Vyloučení<br /><br /> Zařadit členy<br /><br /> odebrat|  
|[ItemDefinitionGroup – element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Podmínka|  
|[ItemGroup – element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Podmínka|  
|[ItemMetadata – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Podmínka|  
|[OnError – element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Podmínka<br /><br /> ExecuteTargets|  
|[Otherwise – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Zvolte<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output – element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Podmínka<br /><br /> Název položky<br /><br /> Vlastnost PropertyName<br /><br /> Parametr úkolu|  
|[Parameter – element](../msbuild/parameter-element.md)|--|Výstup<br /><br /> Zda položka ParameterType<br /><br /> Požadováno|  
|[ParameterGroup – element](../msbuild/parametergroup-element.md)|*Parametr*|--|  
|[Project – element (MSBuild)](../msbuild/project-element-msbuild.md)|Zvolte<br /><br /> Importovat<br /><br /> ItemGroup<br /><br /> Projectextensions –<br /><br /> PropertyGroup<br /><br /> Cíl<br /><br /> Usingtask –|Defaulttargets –<br /><br /> InitialTargets<br /><br /> Atribut ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> atribut xmlns|  
|[ProjectExtensions – element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property – element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Podmínka|  
|[PropertyGroup – element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Podmínka|  
|[Target – element (MSBuild)](../msbuild/target-element-msbuild.md)|Onerror –<br /><br /> *Úloha*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Podmínka<br /><br /> DependsOnTargets<br /><br /> Vstupy<br /><br /> KeepDuplicateOutputs<br /><br /> Název<br /><br /> Výstupy<br /><br /> Vrací|  
|[Task – element (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Podmínka<br /><br /> ContinueOnError –<br /><br /> *Parametr*|  
|[TaskBody – element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Vyhodnocení|  
|[UsingTask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|Parametergroup –<br /><br /> Taskbody –|AssemblyFile<br /><br /> AssemblyName<br /><br /> Podmínka<br /><br /> TaskFactory<br /><br /> TaskName|  
|[When – element (MSBuild)](../msbuild/when-element-msbuild.md)|Zvolte<br /><br /> ItemGroup<br /><br /> PropertyGroup|Podmínka|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Podmínky](../msbuild/msbuild-conditions.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)


