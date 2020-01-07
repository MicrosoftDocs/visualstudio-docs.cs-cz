---
title: Project – element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 1bb7c49e4f3dc86594c8a3211bacb538d3f10c4f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597435"
---
# <a name="project-element-msbuild"></a>Project – element (MSBuild)
Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="syntax"></a>Syntaxe

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
| `DefaultTargets` | Nepovinný atribut.<br /><br /> Výchozí cíl nebo cíle, které mají být vstupním bodem sestavení, pokud nebyl zadán žádný cíl. Více cílů je středníkem (;) oddělených.<br /><br /> Pokud není zadán žádný výchozí cíl buď v atributu `DefaultTargets`, nebo v příkazovém řádku [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], modul provede první cíl v souboru projektu po vyhodnocení [importovaných](../msbuild/import-element-msbuild.md) prvků. |
| `InitialTargets` | Nepovinný atribut.<br /><br /> Počáteční cíl nebo cíle, které mají být spuštěny před cíli zadanými v atributu `DefaultTargets` nebo na příkazovém řádku. Více cílů je středníkem (`;`) odděleno. Pokud je `InitialTargets`definováno více importovaných souborů, budou všechny uvedené cíle spuštěny v pořadí, v jakém byly naimportovány. |
| `Sdk` | Nepovinný atribut. <br /><br /> Název sady SDK a volitelná verze, která se má použít k vytvoření implicitních příkazů importu, které jsou přidány do souboru. proj. Pokud není zadána žádná verze, MSBuild se pokusí přeložit výchozí verzi.  Například `<Project Sdk="Microsoft.NET.Sdk" />` nebo `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Nepovinný atribut.<br /><br /> Verze sady nástrojů MSBuild používá k určení hodnot pro $ (MSBuildBinPath) a $ (MSBuildToolsPath). |
| `TreatAsLocalProperty` | Nepovinný atribut.<br /><br /> Názvy vlastností, které se nepovažují za globální Tento atribut zabraňuje specifickým vlastnostem příkazového řádku v přepsání hodnot vlastností, které jsou nastaveny v souboru projektu nebo cíle a všech následných importech. Více vlastností je středníkem (;) oddělených.<br /><br /> Obvykle globální vlastnosti přepíší hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cíle. Pokud je vlastnost uvedena v `TreatAsLocalProperty` hodnotě, hodnota globální vlastnosti nepřepisuje hodnoty vlastností, které jsou nastaveny v tomto souboru a v následných importech. Další informace najdete v tématu [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Poznámka:**  Globální vlastnosti se nastavují na příkazovém řádku pomocí přepínače **-Property** (nebo **-p**). Můžete také nastavit nebo upravit globální vlastnosti pro podřízené projekty v sestavení více projektů pomocí atributu `Properties` úlohy MSBuild. Další informace najdete v tématu [Úloha MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Nepovinný atribut.<br /><br /> Je-li tento parametr zadán, musí mít atribut `xmlns` hodnotu `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Podřízené prvky

| Prvek | Popis |
| - | - |
| [Výběrem](../msbuild/choose-element-msbuild.md) | Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvky k vyhodnocení. |
| [Import](../msbuild/import-element-msbuild.md) | Volitelný element.<br /><br /> Umožňuje souboru projektu importovat jiný soubor projektu. V projektu může být nula nebo více `Import` prvků. |
| [ImportGroup](../msbuild/importgroup-element.md) | Volitelný element.<br /><br /> Obsahuje kolekci `Import` prvků, které jsou seskupeny pod volitelnou podmínkou. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé položky. Položky jsou určeny pomocí elementu [Item](../msbuild/item-element-msbuild.md) . V projektu může být nula nebo více `ItemGroup` prvků. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Volitelný element.<br /><br /> Umožňuje definovat sadu definic položek, což jsou hodnoty metadat, které jsou aplikovány na všechny položky v projektu, ve výchozím nastavení. ItemDefinitionGroup nahrazuje nutnost použít úlohu `CreateItem` a úlohu `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak uchovávat ne[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] informace v souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. V projektu může být nula nebo jeden `ProjectExtensions` elementů. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé vlastnosti. Vlastnosti jsou určeny pomocí elementu [Property](../msbuild/property-element-msbuild.md) . V projektu může být nula nebo více `PropertyGroup` prvků. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Volitelný element.<br /><br /> Odkazuje na sadu SDK [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  Tento element lze použít jako alternativu k atributu SDK. |
| [Cíl](../msbuild/target-element-msbuild.md) | Volitelný element.<br /><br /> Obsahuje sadu úloh, které [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] provádět sekvenčně. Úkoly jsou určeny pomocí elementu [Task](../msbuild/task-element-msbuild.md) . V projektu může být nula nebo více `Target` prvků. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak zaregistrovat úkoly v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. V projektu může být nula nebo více `UsingTask` prvků. |

### <a name="parent-elements"></a>Nadřazené prvky
 Žádné

## <a name="see-also"></a>Viz také:
- [Postupy: určení prvního cíle sestavení](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
