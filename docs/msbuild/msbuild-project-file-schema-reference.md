---
title: Odkaz na schéma souboru projektu MSBuild | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263086"
---
# <a name="msbuild-project-file-schema-reference"></a>Odkaz na schéma souboru projektu MSBuild

Obsahuje tabulku všech prvků schématu XML MSBuild s jejich dostupnými atributy a podřízenými prvky.

 MSBuild používá soubory projektu pokyn modul sestavení, co sestavit a jak jej sestavit. Soubory projektu MSBuild jsou soubory XML, které dodržují schéma XML MSBuild. V této části je dokument dokument definice schématu XML (*xsd*) pro msbuild.

Odkaz na schéma v souboru projektu MSBuild není vyžadováno v sadě Visual Studio 2017 a novější. Pokud je k ` http://schemas.microsoft.com/developer/msbuild/2003` dispozici, by měla být bez ohledu na verzi sady Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Prvky schématu XML sestavení MSBuild

 V následující tabulce jsou uvedeny všechny prvky schématu XML MSBuild spolu s jejich podřízenými prvky a atributy.

|Element|Podřízené prvky|Atributy|
|-------------|--------------------|----------------|
|[Vybrat prvek (MSBuild)](../msbuild/choose-element-msbuild.md)|Jinak<br /><br /> Kdy|--|
|[Prvek importu (MSBuild)](../msbuild/import-element-msbuild.md)|--|Podmínka<br /><br /> Project|
|[Prvek ImportGroup](../msbuild/importgroup-element.md)|Import|Podmínka|
|[Prvek položky (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Podmínka<br /><br /> Exclude<br /><br /> Zařadit členy<br /><br /> Odebrat|
|[Element ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Položka*|Podmínka|
|[Element ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Položka*|Podmínka|
|[Element ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Položka*|Podmínka|
|[Prvek OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Podmínka<br /><br /> Spustit cíle|
|[Jinak prvek (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Pomocí volby<br /><br /> Skupina položek<br /><br /> Propertygroup|--|
|[Výstupní prvek (MSBuild)](../msbuild/output-element-msbuild.md)|--|Podmínka<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> Parametr_úkolu|
|[Element parametru](../msbuild/parameter-element.md)|--|Výstup<br /><br /> ParametrType<br /><br /> Požaduje se|
|[Element ParameterGroup](../msbuild/parametergroup-element.md)|*Parametr*|--|
|[Prvek projektu (MSBuild)](../msbuild/project-element-msbuild.md)|Pomocí volby<br /><br /> Import<br /><br /> Skupina položek<br /><br /> Rozšíření projektu<br /><br /> Propertygroup<br /><br /> Cíl<br /><br /> UsingTask|Výchozí cíle<br /><br /> Počáteční cíle<br /><br /> ToolsVersion<br /><br /> TreatasLocalProperty<br /><br /> Xmlns|
|[Prvek ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Element vlastnosti (MSBuild)](../msbuild/property-element-msbuild.md)|--|Podmínka|
|[Element PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Vlastnost*|Podmínka|
|[Prvek Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name (Název)<br /><br /> Version|
|[Cílový prvek (MSBuild)](../msbuild/target-element-msbuild.md)|Přichybě<br /><br /> *Úkol*|AfterTargets<br /><br /> Předcíle<br /><br /> Podmínka<br /><br /> DependsOnCíle<br /><br /> Vstupy<br /><br /> Zachovat duplikovatvýstupy<br /><br /> Name (Název)<br /><br /> Výstupy<br /><br /> Vrací|
|[Prvek úkolu targetu (MSBuild)](../msbuild/task-element-msbuild.md)|Výstup|Podmínka<br /><br /> ContinueOnError<br /><br /> *Parametr*|
|[Prvek úlohy UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Vyhodnotit|
|[UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|Skupina parametrů<br /><br /> Úkol|Assemblyfile<br /><br /> Assemblyname<br /><br /> Podmínka<br /><br /> Taskfactory<br /><br /> Název_úkolu|
|[Když element (MSBuild)](../msbuild/when-element-msbuild.md)|Pomocí volby<br /><br /> Skupina položek<br /><br /> Propertygroup|Podmínka|

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Podmínky](../msbuild/msbuild-conditions.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
