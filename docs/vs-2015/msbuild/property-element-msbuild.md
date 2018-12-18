---
title: Property – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: a8b9ebd5207b4fc4a6274090b91e8fa3ab0b20cb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262993"
---
# <a name="property-element-msbuild"></a>Property – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obsahuje název definované vlastnosti uživatele a hodnotu. Každé vlastnosti používané [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu musí být zadán jako podřízený objekt `PropertyGroup` elementu.  
  
 \<Project>  
 \<PropertyGroup >  
  
## <a name="syntax"></a>Syntaxe  
  
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
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element Grouping vlastností.|  
  
## <a name="text-value"></a>Textová hodnota  
 Textová hodnota je volitelná.  
  
 Tento text určuje hodnotu vlastnosti a může obsahovat kód XML.  
  
## <a name="remarks"></a>Poznámky  
 Názvy vlastností jsou omezené na pouze znaky ASCII. Hodnoty vlastností je odkazováno v projektu tak, že název vlastnosti mezi "`$(`"a"`)`". Například `$(builddir)\classes` by přeložit na "build\classes", pokud `builddir` vlastnost má hodnotu `build`. Další informace o vlastnostech najdete v tématu [vlastnosti nástroje MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Příklad  
 Následující kód nastaví `Optimization` vlastnost `false` a `DefaultVersion` vlastnost `1.0` Pokud `Version` vlastnost je prázdná.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Viz také
[Vlastnosti nástroje MSBuild](msbuild-properties1.md)  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)



