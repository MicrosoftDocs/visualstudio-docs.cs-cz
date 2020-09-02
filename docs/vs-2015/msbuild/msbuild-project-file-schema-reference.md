---
title: Referenční dokumentace schématu souboru projektu nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158852"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenční dokumentace schématu souboru projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poskytuje tabulku všech [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] prvků schématu XML s jejich dostupnými atributy a podřízenými prvky.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používá soubory projektu k tomu, aby sestavovací modul vystavil sestavení a jak ho sestavit. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu jsou soubory XML, které vyhovují [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] schématu XML. Tato část dokumentuje soubor definice schématu XML (. XSD) pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
## <a name="msbuild-xml-schema-elements"></a>Prvky schématu XML pro MSBuild  
 V následující tabulce jsou uvedeny všechny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] prvky schématu XML spolu s jejich podřízenými elementy a atributy.  
  
|Prvek|Podřízené elementy|Atributy|  
|-------------|--------------------|----------------|  
|[Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)|Případech<br /><br /> Když|--|  
|[Import – element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Stav<br /><br /> Project|  
|[Import – element](../msbuild/importgroup-element.md)|Import|Stav|  
|[Item – prvek (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata –*|Stav<br /><br /> Exclude<br /><br /> Zařadit členy<br /><br /> Odebrat|  
|[ItemDefinitionGroup – element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Stav|  
|[ItemGroup – element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Stav|  
|[ItemMetadata – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Stav|  
|[OnError – element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Stav<br /><br /> ExecuteTargets|  
|[Otherwise – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Pomocí volby<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Output – element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Stav<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Element parametru](../msbuild/parameter-element.md)|--|Výstup<br /><br /> Zadanému ParameterType<br /><br /> Vyžadováno|  
|[Element Parameter](../msbuild/parametergroup-element.md)|*Parametr*|--|  
|[Project – element (MSBuild)](../msbuild/project-element-msbuild.md)|Pomocí volby<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions –<br /><br /> PropertyGroup<br /><br /> Cíl<br /><br /> UsingTask|DefaultTargets –<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions – element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property – element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Stav|  
|[PropertyGroup – element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Stav|  
|[Target – element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Úkol*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Stav<br /><br /> DependsOnTargets<br /><br /> Vstupy<br /><br /> KeepDuplicateOutputs<br /><br /> Název<br /><br /> Výstupy<br /><br /> Návraty|  
|[Task – element (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Stav<br /><br /> ContinueOnError<br /><br /> *Parametr*|  
|[TaskBody – element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Vyhodnotit|  
|[UsingTask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup –<br /><br /> TaskBody –|AssemblyFile<br /><br /> Doplňk<br /><br /> Stav<br /><br /> TaskFactory<br /><br /> /TN|  
|[When – element (MSBuild)](../msbuild/when-element-msbuild.md)|Pomocí volby<br /><br /> ItemGroup<br /><br /> PropertyGroup|Stav|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Stavu](../msbuild/msbuild-conditions.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 [Nástroji](msbuild.md)
