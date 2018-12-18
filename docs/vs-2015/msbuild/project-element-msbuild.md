---
title: Project – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 923cfa4a32362e28705e9f7fddfa3461979f84e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820022"
---
# <a name="project-element-msbuild"></a>Project – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Požadovaný kořenový element [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
  
|       Atribut        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Popis                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 Nepovinný atribut.<br /><br /> Výchozí cíl nebo cíle se vstupním bodem sestavení, pokud nebyl zadán žádný cíl. Více cílů se středníkem (;) s oddělovači.<br /><br /> Pokud není zadána žádná výchozí cíl buď `DefaultTargets` atribut nebo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] příkazového řádku, modul spustí první cíl v souboru projektu po [Import](../msbuild/import-element-msbuild.md) vyhodnocení elementy.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             Nepovinný atribut.<br /><br /> Počáteční cíle nebo cílů se má spustit před cíle zadané v `DefaultTargets` atribut nebo na příkazovém řádku. Více cílů se středníkem (;) s oddělovači.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Nepovinný atribut.<br /><br /> Verze sady nástrojů MSBuild používá k určení hodnoty $(MSBuildBinPath) a $(MSBuildToolsPath).                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | Nepovinný atribut.<br /><br /> Názvy vlastností, které se za globální. Tento atribut zabrání přepsání hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cílů a všechny následné importy specifické vlastnosti příkazového řádku. Víc vlastností se středníkem (;) s oddělovači.<br /><br /> Za normálních okolností se globální vlastnosti přepisují hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cílů. Pokud vlastnost je uvedená v `TreatAsLocalProperty` hodnota nepřepíše hodnota globální vlastnosti hodnoty vlastností, které jsou nastaveny v souboru a všechny následné importy. Další informace najdete v tématu [postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Poznámka:** nastavení globálních vlastností příkazového řádku s použitím **/property** (nebo **/p**) přepnutí. Můžete také nastavit nebo upravit globální vlastnosti pro podřízené projekty v sestaveních s více projekty pomocí `Properties` atribut úlohy nástroje MSBuild. Další informace najdete v tématu [úlohy nástroje MSBuild](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Požadovaný atribut.<br /><br /> `xmlns` Atribut musí mít hodnotu "<http://schemas.microsoft.com/developer/msbuild/2003>".                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Zvolte](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí jako podřízené prvky k výběru jedné sadě `ItemGroup` elementy a/nebo `PropertyGroup` prvky k vyhodnocení.|  
|[Import](../msbuild/import-element-msbuild.md)|Volitelný element.<br /><br /> Umožňuje projektu soubor k importu jiný soubor projektu. Může být nula nebo více `Import` prvky v projektu.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Element grouping pro jednotlivé položky. Položkami zadávají pomocí [položky](../msbuild/item-element-msbuild.md) elementu. Může být nula nebo více `ItemGroup` prvky v projektu.|  
|[Projectextensions –](../msbuild/projectextensions-element-msbuild.md)|Volitelný element.<br /><br /> Poskytuje způsob, jak zachovat jinou hodnotu než[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] informace [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu. Může být žádný nebo jeden `ProjectExtensions` prvky v projektu.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Element grouping pro jednotlivé vlastnosti. Vlastnosti jsou určeny pomocí [vlastnost](../msbuild/property-element-msbuild.md) elementu. Může být nula nebo více `PropertyGroup` prvky v projektu.|  
|[Cíl](../msbuild/target-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu úkolů pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] postupně provést. Úlohy je určené vlastností [úloh](../msbuild/task-element-msbuild.md) elementu. Může být nula nebo více `Target` prvky v projektu.|  
|[Usingtask –](../msbuild/usingtask-element-msbuild.md)|Volitelný element.<br /><br /> Poskytuje způsob, jak zaregistrovat úlohy v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Může být nula nebo více `UsingTask` prvky v projektu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení prvního cíle k sestavení](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)


