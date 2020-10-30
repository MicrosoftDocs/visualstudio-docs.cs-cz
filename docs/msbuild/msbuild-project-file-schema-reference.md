---
title: Referenční dokumentace schématu souboru projektu nástroje MSBuild | Microsoft Docs
description: Podívejte se na tabulku obsahující všechny prvky schématu XML nástroje MSBuild s jejich dostupnými atributy a podřízenými prvky.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 549e78309ef5fc5e9baf4237f9eca8c7484bc198
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046161"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenční dokumentace schématu souboru projektu nástroje MSBuild

Poskytuje tabulku všech prvků schématu XML nástroje MSBuild s jejich dostupnými atributy a podřízenými prvky.

 Nástroj MSBuild používá soubory projektu k tomu, aby vytvořil modul sestavení, který sestaví a jak ho sestavit. Soubory projektu MSBuild jsou soubory XML, které odpovídají schématu XML pro MSBuild. Tato část dokumentuje soubor definice schématu XML ( *. xsd* ) pro nástroj MSBuild.

Odkaz na schéma v souboru projektu MSBuild není vyžadován v aplikaci Visual Studio 2017 a novějším. Je-li k dispozici, měla by být ` http://schemas.microsoft.com/developer/msbuild/2003` bez ohledu na verzi sady Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Prvky schématu XML pro MSBuild

 V následující tabulce jsou uvedeny všechny prvky schématu XML nástroje MSBuild spolu s jejich podřízenými elementy a atributy.

|Prvek|Podřízené prvky|Atributy|
|-------------|--------------------|----------------|
|[Choose – element (MSBuild)](../msbuild/choose-element-msbuild.md)|Případech<br /><br /> Když|--|
|[Import – element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Stav<br /><br /> Project|
|[ImportGroup – element](../msbuild/importgroup-element.md)|Import|Stav|
|[Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetadata –*|Stav<br /><br /> Exclude<br /><br /> Zařadit členy<br /><br /> Odebrat|
|[ItemDefinitionGroup – Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Stav|
|[Item – Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Stav|
|[ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Stav|
|[Error – element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Stav<br /><br /> ExecuteTargets|
|[Jinak – element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Pomocí volby<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output – element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Stav<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter – element](../msbuild/parameter-element.md)|--|Výstup<br /><br /> Zadanému ParameterType<br /><br /> Vyžadováno|
|[ParameterGroup – element](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Project – element (MSBuild)](../msbuild/project-element-msbuild.md)|Pomocí volby<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions –<br /><br /> PropertyGroup<br /><br /> Cíl<br /><br /> UsingTask|DefaultTargets –<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions – – element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property – element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Stav|
|[Property – element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Stav|
|[Element sady SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Verze|
|[Target – element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Úloha*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Stav<br /><br /> DependsOnTargets<br /><br /> Vstupy<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Výstupy<br /><br /> Návraty|
|[Element Task cíle (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Stav<br /><br /> ContinueOnError<br /><br /> *Parametr*|
|[Element Task pro UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Vyhodnotit|
|[UsingTask – element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup –<br /><br /> Úloha|AssemblyFile<br /><br /> Doplňk<br /><br /> Stav<br /><br /> TaskFactory<br /><br /> /TN|
|[When – element (MSBuild)](../msbuild/when-element-msbuild.md)|Pomocí volby<br /><br /> ItemGroup<br /><br /> PropertyGroup|Stav|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Podmínky](../msbuild/msbuild-conditions.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
