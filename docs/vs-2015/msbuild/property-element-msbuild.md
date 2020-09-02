---
title: Property – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158267"
---
# <a name="property-element-msbuild"></a>Property – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje uživatelsky definovaný název a hodnotu vlastnosti. Každá vlastnost použitá v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu musí být zadána jako podřízená položka `PropertyGroup` elementu.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Seskupení elementu pro vlastnosti|  
  
## <a name="text-value"></a>Textová hodnota  
 Textová hodnota je volitelná.  
  
 Tento text určuje hodnotu vlastnosti a může obsahovat XML.  
  
## <a name="remarks"></a>Poznámky  
 Názvy vlastností jsou omezeny pouze na znaky ASCII. Hodnoty vlastností jsou odkazovány v projektu umístěním názvu vlastnosti mezi " `$(` " a " `)` ". Například by se `$(builddir)\classes` přeložila na "build\classes", pokud `builddir` vlastnost měla hodnotu `build` . Další informace o vlastnostech naleznete v tématu [vlastnosti MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví `Optimization` vlastnost na `false` a `DefaultVersion` vlastnost na hodnotu, `1.0` Pokud `Version` je vlastnost prázdná.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Viz také
[Vlastnosti nástroje MSBuild](msbuild-properties1.md)  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
