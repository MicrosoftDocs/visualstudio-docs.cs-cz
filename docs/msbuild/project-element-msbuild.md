---
title: Project – element (MSBuild) | Microsoft Docs
description: Přečtěte si o elementu projektu MSBuild, který je požadovaným kořenovým elementem souboru projektu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 223ccd9e823bef4ee458a7aa1ce2d785788c6238
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048860"
---
# <a name="project-element-msbuild"></a>Project – element (MSBuild)

Požadovaný kořenový element souboru projektu MSBuild.

## <a name="syntax"></a>Syntax

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|------------------------| - |
| `DefaultTargets` | Nepovinný atribut.<br /><br /> Výchozí cíl nebo cíle, které mají být vstupním bodem sestavení, pokud nebyl zadán žádný cíl. Více cílů je středníkem (;) oddělených.<br /><br /> Pokud není zadán žádný výchozí cíl buď v `DefaultTargets` atributu, nebo v příkazovém řádku MSBuild, modul provede první cíl v souboru projektu po vyhodnocení prvků [importu](../msbuild/import-element-msbuild.md) . |
| `InitialTargets` | Nepovinný atribut.<br /><br /> Počáteční cíl nebo cíle, které mají být spuštěny před cíli zadanými v `DefaultTargets` atributu nebo na příkazovém řádku. Více cílů je středníkem ( `;` ) odděleno. Pokud je definováno více importovaných souborů `InitialTargets` , budou všechny zmíněné cíle spuštěny v pořadí, v jakém byly naimportovány. |
| `Sdk` | Nepovinný atribut. <br /><br /> Název sady SDK a volitelná verze, která se má použít k vytvoření implicitních příkazů importu, které jsou přidány do souboru. proj. Pokud není zadána žádná verze, MSBuild se pokusí přeložit výchozí verzi.  Příkladem je `<Project Sdk="Microsoft.NET.Sdk" />` nebo `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Nepovinný atribut.<br /><br /> Verze sady nástrojů MSBuild používá k určení hodnot pro $ (MSBuildBinPath) a $ (MSBuildToolsPath). |
| `TreatAsLocalProperty` | Nepovinný atribut.<br /><br /> Názvy vlastností, které se nepovažují za globální Tento atribut zabraňuje specifickým vlastnostem příkazového řádku v přepsání hodnot vlastností, které jsou nastaveny v souboru projektu nebo cíle a všech následných importech. Více vlastností je středníkem (;) oddělených.<br /><br /> Obvykle globální vlastnosti přepíší hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cíle. Pokud je vlastnost uvedena v `TreatAsLocalProperty` hodnotě, hodnota globální vlastnosti nepřepisuje hodnoty vlastností, které jsou nastaveny v tomto souboru a jakékoliv následné importy. Další informace najdete v tématu [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Poznámka:**  Globální vlastnosti se nastavují na příkazovém řádku pomocí přepínače **-Property** (nebo **-p** ). Můžete také nastavit nebo upravit globální vlastnosti pro podřízené projekty v sestavení více projektů pomocí `Properties` atributu úlohy MSBuild. Další informace najdete v tématu [Úloha MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Nepovinný atribut.<br /><br /> Je-li tento parametr zadán, `xmlns` musí mít hodnotu `http://schemas.microsoft.com/developer/msbuild/2003` . |

### <a name="child-elements"></a>Podřízené prvky

| Element | Popis |
| - | - |
| [Pomocí volby](../msbuild/choose-element-msbuild.md) | Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvků k vyhodnocení. |
| [Import](../msbuild/import-element-msbuild.md) | Volitelný element.<br /><br /> Umožňuje souboru projektu importovat jiný soubor projektu. V projektu může být nula nebo více `Import` prvků. |
| [ImportGroup –](../msbuild/importgroup-element.md) | Volitelný element.<br /><br /> Obsahuje kolekci `Import` prvků, které jsou seskupeny pod volitelnou podmínkou. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé položky. Položky jsou určeny pomocí elementu [Item](../msbuild/item-element-msbuild.md) . V projektu může být nula nebo více `ItemGroup` prvků. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Volitelný element.<br /><br /> Umožňuje definovat sadu definic položek, což jsou hodnoty metadat, které jsou aplikovány na všechny položky v projektu, ve výchozím nastavení. ItemDefinitionGroup nahrazuje nutnost použít `CreateItem` úlohu a `CreateProperty` úlohu. |
| [ProjectExtensions –](../msbuild/projectextensions-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak uchovávat informace mimo nástroj MSBuild v souboru projektu MSBuild. V projektu může být nula nebo jeden `ProjectExtensions` prvek. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé vlastnosti. Vlastnosti jsou určeny pomocí elementu [Property](../msbuild/property-element-msbuild.md) . V projektu může být nula nebo více `PropertyGroup` prvků. |
| [Sadě](../msbuild/sdk-element-msbuild.md) | Volitelný element.<br /><br /> Odkazuje na sadu SDK projektu MSBuild.  Tento element lze použít jako alternativu k atributu SDK. |
| [Cílové](../msbuild/target-element-msbuild.md) | Volitelný element.<br /><br /> Obsahuje sadu úloh, které může nástroj MSBuild spustit sekvenčně. Úkoly jsou určeny pomocí elementu [Task](../msbuild/task-element-msbuild.md) . V projektu může být nula nebo více `Target` prvků. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak registrovat úlohy v nástroji MSBuild. V projektu může být nula nebo více `UsingTask` prvků. |

### <a name="parent-elements"></a>Nadřazené prvky

 Žádné

## <a name="see-also"></a>Viz také

- [Postupy: určení prvního cíle sestavení](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Referenční dokumentace k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
