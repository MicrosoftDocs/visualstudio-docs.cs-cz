---
title: ItemCollection – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20c22e0ea2ef05c108ebe564b186ede2a02f9dfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162422"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje sadu uživatelsky definovaných prvků [položky](../msbuild/item-element-msbuild.md) . Každá položka, která se používá v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu, musí být zadána jako podřízený `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Položka](../msbuild/item-element-msbuild.md)|Definuje vstupy procesu sestavení. Může existovat nula nebo více `Item` prvků v `ItemGroup` .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
|[Cílové](../msbuild/target-element-msbuild.md)|Počínaje .NET Framework 3,5 se `ItemGroup` element může objevit uvnitř `Target` elementu. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje uživatelsky definované kolekce položek `Res` a `CodeFiles` deklarované uvnitř `ItemGroup` elementu. Každá položka v `Res` kolekci položek obsahuje uživatelsky definovaný podřízený element [ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md) .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Položek](../msbuild/msbuild-items.md)   
 [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
