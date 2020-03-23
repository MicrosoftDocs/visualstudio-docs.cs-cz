---
title: Prvek projektu (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632976"
---
# <a name="project-element-msbuild"></a>Prvek projektu (MSBuild)

Požadovaný kořenový prvek souboru projektu MSBuild.

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

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|------------------------| - |
| `DefaultTargets` | Nepovinný atribut.<br /><br /> Výchozí cíl nebo cíle jako vstupní bod sestavení, pokud nebyl zadán žádný cíl. Více cílů je středník (;) Oddělený.<br /><br /> Pokud není zadán žádný výchozí `DefaultTargets` cíl v atributu nebo příkazovém řádku MSBuild, modul provede první cíl v souboru projektu po vyhodnocení prvků [importu.](../msbuild/import-element-msbuild.md) |
| `InitialTargets` | Nepovinný atribut.<br /><br /> Počáteční cíl nebo cíle, které mají být `DefaultTargets` spuštěny před cíli zadanými v atributu nebo na příkazovém řádku. Více cílů je vymezeno středníkem (`;`). Pokud definuje `InitialTargets`více importovaných souborů , budou spuštěny všechny uvedené cíle v pořadí, v jakém dojde k importu. |
| `Sdk` | Nepovinný atribut. <br /><br /> Název sady SDK a volitelná verze, které se mají použít k vytvoření implicitních příkazů Import, které jsou přidány do souboru .proj. Pokud není zadána žádná verze, msbuild se pokusí přeložit výchozí verzi.  Příkladem je `<Project Sdk="Microsoft.NET.Sdk" />` nebo `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Nepovinný atribut.<br /><br /> Verze sady nástrojů MSBuild používá k určení hodnot pro $(MSBuildBinPath) a $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Nepovinný atribut.<br /><br /> Názvy vlastností, které nebudou považovány za globální. Tento atribut zabraňuje přepsání hodnot vlastností určitých příkazového řádku, které jsou nastaveny v souboru projektu nebo cílů, a ve všech následných importech. Více vlastností je středník (;) Oddělený.<br /><br /> Globální vlastnosti obvykle přepíší hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cílů. Pokud je vlastnost uvedena `TreatAsLocalProperty` v hodnotě, globální hodnota vlastnosti nepřepíše hodnoty vlastností, které jsou nastaveny v tomto souboru a všechny následné importy. Další informace naleznete v [tématu Postup: Vytvoření stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Poznámka:**  Globální vlastnosti najdete na příkazovém řádku pomocí přepínače **vlastnosti -property** (nebo **-p).** Můžete také nastavit nebo upravit globální vlastnosti pro podřízené `Properties` projekty v sestavení více projektů pomocí atributu úkolu MSBuild. Další informace naleznete v tématu [MSBuild task](../msbuild/msbuild-task.md). |
| `xmlns` | Nepovinný atribut.<br /><br /> Pokud je `xmlns` zadán, atribut musí `http://schemas.microsoft.com/developer/msbuild/2003`mít hodnotu . |

### <a name="child-elements"></a>Podřízené prvky

| Element | Popis |
| - | - |
| [Pomocí volby](../msbuild/choose-element-msbuild.md) | Volitelný element.<br /><br /> Vyhodnotí podřízené prvky `ItemGroup` pro výběr `PropertyGroup` jedné sady prvků nebo prvků, které mají být vyhodnoceny. |
| [Import](../msbuild/import-element-msbuild.md) | Volitelný element.<br /><br /> Povolí souboru projektu importovat jiný soubor projektu. V projektu může `Import` být nula nebo více prvků. |
| [Skupina importu](../msbuild/importgroup-element.md) | Volitelný element.<br /><br /> Obsahuje kolekci `Import` prvků, které jsou seskupeny pod volitelnou podmínkou. |
| [Skupina položek](../msbuild/itemgroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé položky. Položky jsou [určeny](../msbuild/item-element-msbuild.md) pomocí Item element. V projektu může `ItemGroup` být nula nebo více prvků. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Volitelný element.<br /><br /> Umožňuje definovat sadu definic položek, což jsou hodnoty metadat, které jsou ve výchozím nastavení použity pro všechny položky v projektu. ItemDefinitionGroup nahrazuje potřebu použití `CreateItem` úkolu a `CreateProperty` úkolu. |
| [Rozšíření projektu](../msbuild/projectextensions-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak zachovat informace bez MSBuild v souboru projektu MSBuild. V projektu může `ProjectExtensions` být nula nebo jeden prvky. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé vlastnosti. Vlastnosti jsou určeny pomocí [Property](../msbuild/property-element-msbuild.md) element. V projektu může `PropertyGroup` být nula nebo více prvků. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Volitelný element.<br /><br /> Odkazuje na sadu SDK projektu MSBuild.  Tento prvek lze použít jako alternativu k atributu Sdk. |
| [Cíl](../msbuild/target-element-msbuild.md) | Volitelný element.<br /><br /> Obsahuje sadu úloh pro MSBuild postupně spustit. Úkoly jsou určeny pomocí [task](../msbuild/task-element-msbuild.md) elementu. V projektu může `Target` být nula nebo více prvků. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Volitelný element.<br /><br /> Poskytuje způsob, jak zaregistrovat úkoly v MSBuild. V projektu může `UsingTask` být nula nebo více prvků. |

### <a name="parent-elements"></a>Nadřazené prvky

 Žádné.

## <a name="see-also"></a>Viz také

- [Postup: Určete, který cíl má být sestavován jako první](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Msbuild](../msbuild/msbuild.md)
