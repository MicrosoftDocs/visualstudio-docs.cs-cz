---
title: Project – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b11449626050c4da75b09f2d348a4b1b0190ec4d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476936"
---
# <a name="project-element-msbuild"></a>Project – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
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
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 Nepovinný atribut.<br /><br /> Výchozí cíl nebo cíle, které mají být vstupním bodem sestavení, pokud nebyl zadán žádný cíl. Více cílů je středníkem (;) oddělených.<br /><br /> Pokud není zadán žádný výchozí cíl buď v atributu `DefaultTargets`, nebo v příkazovém řádku [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], modul provede první cíl v souboru projektu po vyhodnocení [importovaných](../msbuild/import-element-msbuild.md) prvků.                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             Nepovinný atribut.<br /><br /> Počáteční cíl nebo cíle, které mají být spuštěny před cíli zadanými v atributu `DefaultTargets` nebo na příkazovém řádku. Více cílů je středníkem (;) oddělených.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Nepovinný atribut.<br /><br /> Verze sady nástrojů MSBuild používá k určení hodnot pro $ (MSBuildBinPath) a $ (MSBuildToolsPath).                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | Nepovinný atribut.<br /><br /> Názvy vlastností, které se nepovažují za globální Tento atribut zabraňuje specifickým vlastnostem příkazového řádku v přepsání hodnot vlastností, které jsou nastaveny v souboru projektu nebo cíle a všech následných importech. Více vlastností je středníkem (;) oddělených.<br /><br /> Obvykle globální vlastnosti přepíší hodnoty vlastností, které jsou nastaveny v souboru projektu nebo cíle. Pokud je vlastnost uvedena v `TreatAsLocalProperty` hodnotě, hodnota globální vlastnosti nepřepisuje hodnoty vlastností, které jsou nastaveny v tomto souboru a v následných importech. Další informace najdete v tématu [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Poznámka:**  Globální vlastnosti se nastavují na příkazovém řádku pomocí přepínače **/Property** (nebo **/p**). Můžete také nastavit nebo upravit globální vlastnosti pro podřízené projekty v sestavení více projektů pomocí atributu `Properties` úlohy MSBuild. Další informace najdete v tématu [Úloha MSBuild](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Povinný atribut (v MSBuild 15. x a starší).<br /><br /> Atribut `xmlns` musí mít hodnotu `http://schemas.microsoft.com/developer/msbuild/2003`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Výběrem](../msbuild/choose-element-msbuild.md)|Volitelný element.<br /><br /> Vyhodnotí podřízené prvky a vybere jednu sadu `ItemGroup` prvků a/nebo `PropertyGroup` prvky k vyhodnocení.|  
|[Import](../msbuild/import-element-msbuild.md)|Volitelný element.<br /><br /> Umožňuje souboru projektu importovat jiný soubor projektu. V projektu může být nula nebo více `Import` prvků.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé položky. Položky jsou určeny pomocí elementu [Item](../msbuild/item-element-msbuild.md) . V projektu může být nula nebo více `ItemGroup` prvků.|  
|[ProjectExtensions –](../msbuild/projectextensions-element-msbuild.md)|Volitelný element.<br /><br /> Poskytuje způsob, jak uchovávat ne[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] informace v souboru projektu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. V projektu může být nula nebo jeden `ProjectExtensions` elementů.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Volitelný element.<br /><br /> Prvek seskupení pro jednotlivé vlastnosti. Vlastnosti jsou určeny pomocí elementu [Property](../msbuild/property-element-msbuild.md) . V projektu může být nula nebo více `PropertyGroup` prvků.|  
|[Cíl](../msbuild/target-element-msbuild.md)|Volitelný element.<br /><br /> Obsahuje sadu úloh, které [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] provádět sekvenčně. Úkoly jsou určeny pomocí elementu [Task](../msbuild/task-element-msbuild.md) . V projektu může být nula nebo více `Target` prvků.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Volitelný element.<br /><br /> Poskytuje způsob, jak zaregistrovat úkoly v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. V projektu může být nula nebo více `UsingTask` prvků.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádné.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení, který cíl se má sestavit poprvé](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Referenční  příkazového řádku](../msbuild/msbuild-command-line-reference.md)  
 [Referenční  schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](msbuild.md)
