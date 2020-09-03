---
title: Property – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6590464b78d6b5452ce266d701aefc0f739185b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155940"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje sadu uživatelsky definovaných prvků [vlastností](../msbuild/property-element-msbuild.md) . Každý `Property` prvek použitý v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu musí být podřízeným prvkem `PropertyGroup` elementu.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Stav|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Vlastnost](../msbuild/property-element-msbuild.md)|Volitelný element.<br /><br /> Uživatelsky definovaný název vlastnosti, který obsahuje hodnotu vlastnosti. Element může obsahovat nula nebo více prvků *vlastností* `PropertyGroup` .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak nastavit vlastnosti na základě podmínky. V tomto příkladu, pokud `CompileConfig` je hodnota vlastnosti `DEBUG` ,, `Optimization` `Obfuscate` a `OutputPath` vlastností uvnitř `PropertyGroup` elementu, jsou nastaveny.  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [Vlastnosti nástroje MSBuild](msbuild-properties1.md)
