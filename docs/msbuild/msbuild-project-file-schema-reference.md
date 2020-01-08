---
title: Referenční dokumentace schématu souboru projektu nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: def9edb232a37bc58a56ffd1ec9a16bcb1b75092
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590316"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenční dokumentace schématu souboru projektu nástroje MSBuild
Poskytuje tabulku všech [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] prvků schématu XML s jejich dostupnými atributy a podřízenými prvky.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používá soubory projektu k tomu, aby modul buildu instruoval, co sestavit a jak ho sestavit. soubory projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jsou soubory XML, které vyhovují schématu XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Tato část dokumentuje soubor definice schématu XML ( *. xsd*) pro [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>Prvky schématu XML pro MSBuild
 V následující tabulce jsou uvedeny všechny prvky [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] schématu XML spolu s jejich podřízenými prvky a atributy.

|Prvek|Podřízené prvky|Atributy|
|-------------|--------------------|----------------|
|[Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)|Případech<br /><br /> Když|--|
|[Import – element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Podmínka<br /><br /> Projekt|
|[Import – element](../msbuild/importgroup-element.md)|Importovat|Podmínka|
|[Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Podmínka<br /><br /> Vyloučit<br /><br /> Zařadit členy<br /><br /> Odebrat|
|[ItemDefinitionGroup – Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Podmínka|
|[Item – Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Podmínka|
|[ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Podmínka|
|[Error – element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Podmínka<br /><br /> ExecuteTargets|
|[Jinak – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Možnost<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output – element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Podmínka<br /><br /> ItemName<br /><br /> Vlastnost PropertyName<br /><br /> TaskParameter|
|[Element parametru](../msbuild/parameter-element.md)|--|Výstup<br /><br /> Zadanému ParameterType<br /><br /> Požadováno|
|[Element Parameter](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Project – element (MSBuild)](../msbuild/project-element-msbuild.md)|Možnost<br /><br /> Importovat<br /><br /> ItemGroup<br /><br /> ProjectExtensions –<br /><br /> PropertyGroup<br /><br /> Cíl<br /><br /> UsingTask|DefaultTargets –<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions – – element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property – element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Podmínka|
|[Property – element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Podmínka|
|[Element sady SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Version|
|[Target – element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Úloha*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Podmínka<br /><br /> DependsOnTargets<br /><br /> Vstupy<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Výstupy<br /><br /> Vrátí|
|[Task – element (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Podmínka<br /><br /> ContinueOnError –<br /><br /> *Parametr*|
|[TaskBody – – element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Zhodnocení produktu|
|[UsingTask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup –<br /><br /> TaskBody –|AssemblyFile<br /><br /> Doplňk<br /><br /> Podmínka<br /><br /> TaskFactory<br /><br /> TaskName|
|[When – element (MSBuild)](../msbuild/when-element-msbuild.md)|Možnost<br /><br /> ItemGroup<br /><br /> PropertyGroup|Podmínka|

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Podmínky](../msbuild/msbuild-conditions.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
